# Secure RabbitMQ with TLS Support on Xray

1. Generate certificates for RabbitMQ and Xray.\
   The name "CN=rabbitmq" (which appears twice in the following code) should be a resolvable DNS, and should be used in the system.yaml file when providing the shared.rabbitMq.url (see step 6 below)
   1.  Create Certificate Authority (CA) files.

       ```
       #Creates ca-key.pem and ca.csr CA files. These are self-signed.
       openssl req -new -nodes -text -out ca.csr -keyout ca-key.pem -subj "/CN=certificate-authority"

       ```
   2.  Sign the CA private key, ca-key.pem, and create the related CA certificate.

       ```
       openssl x509 -req -in ca.csr -text -extfile /etc/ssl/openssl.cnf -extensions v3_ca -signkey ca-key.pem -out ca-cert.pem
       ```
   3.  Create the RabbitMQ private key (server-key.pem) and certificate signing request file(server.csr).

       ```
       openssl req -new -nodes -text -out server.csr -keyout server-key.pem -subj "/CN=rabbitmq"
       ```
   4.  Create a signed RabbitMQ public key (server-cert.pem).

       ```
       openssl x509 -req -in server.csr -text -CA ca-cert.pem -CAkey ca-key.pem -CAcreateserial -out server-cert.pem
       ```
   5.  Create Xray client key (client-key.pem) and certificate signing request file (client.csr).

       ```
       openssl req -new -nodes -text -out client.csr -keyout client-key.pem -subj "/CN=rabbitmq"
       ```
   6.  Create Xray client certificate file.

       ```
       openssl x509 -req -in client.csr -text -CA ca-cert.pem -CAkey ca-key.pem -CAcreateserial -out client-cert.pem
       ```
2.  Create the `certs` directories under `$JFROG_HOME/xray/var/data/server` and`$JFROG_HOME/xray/var/data/rabbitmq`.

    ```
    mkdir $JFROG_HOME/xray/var/data/server/certs

    mkdir $JFROG_HOME/xray/var/data/rabbitmq/certs
    ```
3.  Copy the ca and server certificates to `$JFROG_HOME/xray/var/data/rabbitmq/certs` and `$JFROG_HOME/xray/var/data/server/certs` respectively.

    **Docker Compose**

    ```
    ls -ltr <mounted directory>/xray/var/data/server/certs/
    total 3
    -rw-r--r-- 1 xray xray 1127 Oct 11 15:55 ca-cert.pem
    -rw-r--r-- 1 xray xray  993 Oct 11 15:55 client-cert.pem
    -rw-r--r-- 1 xray xray 1704 Oct 11 15:55 client-key.pem
    ```

    **RPM / DEB**

    ```
    ls -ltr /opt/jfrog/xray/var/data/server/certs/
    total 3
    -rw-r--r-- 1 xray xray 1127 Oct 11 15:55 ca-cert.pem
    -rw-r--r-- 1 xray xray  993 Oct 11 15:55 client-cert.pem
    -rw-r--r-- 1 xray xray 1704 Oct 11 15:55 client-key.pem
    ```

    **Linux Archive**

    ```
    ls -ltr JFROG_HOME/xray/var/data/server/certs/
    total 3
    -rw-r--r-- 1 xray xray 1127 Oct 11 15:55 ca-cert.pem
    -rw-r--r-- 1 xray xray  993 Oct 11 15:55 client-cert.pem
    -rw-r--r-- 1 xray xray 1704 Oct 11 15:55 client-key.pem
    ```

    ```
    cp ca-cert.pem server-cert.pem server-key.pem $JFROG_HOME/xray/var/data/rabbitmq/certs

    cp ca-cert.pem client-cert.pem client-key.pem $JFROG_HOME/xray/var/data/server/certs
    ```
4.  Modify the certificate permissions for the RabbitMQ user.

    **Docker Compose**

    ```
    chown -R 999:999 <mounted directory>/xray/var/data/rabbitmq/certs
    ```

    **DEB / RPM**

    ```
    chown -R xray:xray /opt/jfrog/xray/var/data/rabbitmq/certs
    ```

    **Linux Archive**

    ```
    ## default user and group is xray:xray
    chown -R <xray user>:<xray group> JFROG_HOME/xray/var/data/rabbitmq/certs
    ```
5.  Modify the certificate permissions for the Xray user.

    **Docker Compose**

    ```
    chown -R 1035:1035 <mounted directory>/xray/var/data/server/certs
    ```

    **RPM / DEB**

    ```
    chown -R xray:xray /opt/jfrog/xray/var/data/server/certs/
    ```

    **Linux Archive**

    ```
    ## default user and group is xray:xray
    chown -R <xray user>:<xray group> JFROG_HOME/xray/var/data/server/certs/
    ```
6.  Modify `/opt/jfrog/xray/var/etc/system.yaml` under `shared.rabbitmq`, according to your configuration. Do not overwrite existing lines in the file

    ```
    shared:
        rabbitMq:
            url: amqps://localhost:5671
            certCaFilePath: "/opt/jfrog/xray/var/data/server/certs/ca-cert.pem"
            certFilePath: "/opt/jfrog/xray/var/data/server/certs/client-cert.pem"
            certKeyFilePath: "/opt/jfrog/xray/var/data/server/certs/client-key.pem"
            autoStop: true
            node:
                rabbitmqConf:
                    - name: ssl_options.cacertfile
                      value: /opt/jfrog/xray/var/data/rabbitmq/certs/ca-cert.pem
                    - name: ssl_options.certfile
                      value: /opt/jfrog/xray/var/data/rabbitmq/certs/server-cert.pem
                    - name: ssl_options.keyfile
                      value: /opt/jfrog/xray/var/data/rabbitmq/certs/server-key.pem
                    - name: ssl_options.verify
                      value: verify_peer
                    - name: ssl_options.fail_if_no_peer_cert
                      value: false
                    - name: management.listener.ssl
                      value: true
                    - name: listeners.ssl.default
                      value: 5671
                    - name: listeners.tcp
                      value: none
    ```

    Replace `<rabbitmq-password>` with your own RabbitMQ password. If you use a different user in RabbitMQ, replace the guest user with your own user in the `shared.rabbitMq.url` value.
7.  Create a JSON file with the following content to enable the TLS connection to RabbitMQ in Xray using the REST API.

    ```
    {

        "sslInsecure": false,

        "maxDiskDataUsage": 80,

        "monitorSamplingInterval": 300,

        "mailNoSsl": false,

        "messageMaxTTL": 7,

        "jobInterval": 86400,

        "allowSendingAnalytics": true,

        "httpsPort": 443,

        "enableTlsConnectionToRabbitMQ": true,

        "httpClientMaxConnections": 50,

        "httpClientMaxIdleConnections": 20,

        "jsFilesBatch": 20

    }
    ```
8.  Run the REST API call using the JSON file you created in the previous step to enable the TLS connection to RabbitMQ in Xray.

    ```
    curl -u<username>:<password> -d @<your_json_file>.json -H "Content-Type: application/json" -X PUT http://<artifactory_url>/xray/api/v1/configuration/systemParameters
    ```

    Replace `<username>` and `<password>` with an admin user and password credentials for Artifactory, the \<your\_json\_file>.json with the name of the JSON file you created in the previous step and the \<artifactory\_url> with the actual Artifactory URL address.

    Run the following steps to enable the TLS connection to RabbitMQ in Xray if you use Docker Compose.

    **Docker Compose**

    ```
    cd  <path to extracted compose directory>/jfrog-xray-<version>-compose/
    ```

    ```
    ## Export the TLS port in the docker-compose-rabbitmq.yaml (docker-compose.yaml for older versions of 3.x) and add under services -> rabbitmq -> ports.
    - 5671:5671
    ```

    ```
    # Restart RabbitMQ services
    docker-compose -p xray-rabbitmq -f docker-compose-rabbitmq.yaml down
    docker-compose -p xray-rabbitmq -f docker-compose-rabbitmq.yaml up -d
    ```
9.  Restart Xray services.

    **Docker Compose**

    ```
    docker-compose -p xray -f docker-compose.yaml down
    docker-compose -p xray -f docker-compose.yaml up -d
    ```

    **RPM / DEB**

    ```
    systemctl stop xray.service
    systemctl start xray.service

    ## For Centos 6 and RHEL 6
    # service xray stop
    # service xray start 
    ```

    **Linux Archive**

    ```
    /opt/jfrog/xray/bin/xray.sh stop
    /opt/jfrog/xray/bin/xray.sh start 
    ```
10. After Xray services are up and running, you can verify if RabbitMQ is accessible through `https://<xray-ipaddress-or-hostname>:15672`.

### **For Self-signed Certificates Only**

To ensure that the client trusts self-signed certificates (only), you will need to perform the following steps according to the OS you are using.

**For Docker**

You will need to mount a root ca bundle into each Xray container:

```
volumes:
      - /etc/localtime:/etc/localtime:ro
      - "${ROOT_DATA_DIR}/var:/var/opt/jfrog/xray"
      - /opt/jfrog/xray/app/third-party/rabbitmq/rabbitmq-root-ca.crt:/etc/ssl/certs/ca-certificates.crt
```

**For Linux Archive/Native OS: Debian 8/9/10, Ubuntu 16/18/20**

Copy your root certificate into `/usr/local/share/ca-certificates/` and then run the `update-ca-certificates` `command`.

```
# cp rabbitmq-root-ca.crt /usr/local/share/ca-certificates/
# update-ca-certificates
Updating certificates in /etc/ssl/certs...
1 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d...Adding debian:rabbitmq-root-ca.pem
done.
done.
```

**For Linux Archive/Native OS: CentOS 6/7/8, RHEL 6/7/8**

Copy your root certificate into /etc/pki/ca-trust/source/anchors/ and then run the update-ca-trust command.

```
# cp rabbitmq-root-ca.crt /etc/pki/ca-trust/source/anchors/
# update-ca-trust
```

Note that on CentOS 6/RHEL 6 you will have to run an additional command `- update-ca-trust force-enable`.

After you add your own root certificate into the system bundle - you can verify the certificate with the following command:

```
# openssl verify -verbose /opt/jfrog/xray/var/data/server/certs/rabbitmq-client.crt
/opt/jfrog/xray/var/data/server/certs/rabbitmq-client.crt: OK

# openssl verify -verbose /opt/jfrog/xray/var/data/rabbitmq/certs/rabbitmq-server.crt
/opt/jfrog/xray/var/data/rabbitmq/certs/rabbitmq-server.crt: OK
Otherwise we will get the error

# openssl verify -verbose /opt/jfrog/xray/var/data/server/certs/rabbitmq-client.crt
/opt/jfrog/xray/var/data/server/certs/rabbitmq-client.crt: CN = rabbitmq
error 20 at 0 depth lookup:unable to get local issuer certificate

# openssl verify -verbose /opt/jfrog/xray/var/data/rabbitmq/certs/rabbitmq-server.crt
/opt/jfrog/xray/var/data/rabbitmq/certs/rabbitmq-server.crt: CN = rabbitmq
error 20 at 0 depth lookup:unable to get local issuer certificate
```

Troubleshoot RabbitMQ with TLS in Xray\
​\
If you encounter any errors or issues you might find the following troubleshooting tips helpful:

* Ensure that you have the proper certificates and that their location is correct. The ​`$JFROG_HOME​` variable refers to the directory in which Xray is installed. The default is ​`/opt/jfrog`​​.
* In some operating systems, the ​`openssl.cnf`​ file may be located in a different location than​`/etc/ssl/openssl.cnf`​​. Use the find command to find it in your system: `find / -name openssl.cnf`
* Check that all the certificates are owned by the user and group `​xray`​​. If you are using a different user and group to run Xray, ensure this user is the owner of the files.
* The YAML files must have proper indentation with the same amount of spaces across the entire file. Ensure the Xray ​`system.yaml​​` file is properly indented and that the syntax is correct. Also, check that the details are correct such as passwords, paths, and URLs are correct in the YAML file.
* A successful REST API call requires an Artifactory admin user.
* Check the logs to find additional information to help in further troubleshooting any issues. The logs directory is​​`$JFROG_HOME/xray/var/log`​​. The recommended logs to look at are the​ `console.log`​​, ​`xray-server-service.log`​​, and the `RabbitMQ` logs in the `rabbitmq` directory.



\
​\
\
​\
