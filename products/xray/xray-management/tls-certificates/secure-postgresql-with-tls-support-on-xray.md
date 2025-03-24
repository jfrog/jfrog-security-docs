# Secure PostgreSQL with TLS Support on Xray

Copy these TLS parameters to​​`/var/opt/jfrog/postgres/data/postgresql.conf`​​

```
ssl = on
ssl_ciphers = 'HIGH:MEDIUM:+3DES:!aNULL'
ssl_prefer_server_ciphers = on
ssl_cert_file = '/full/path/to/postgres/certificates/server.crt'
ssl_key_file = '/full/path/to/postgres/certificates/server.key'
ssl_ca_file = '/full/path/to/postgres/certificates/server_ca.crt'
```

Verify that the certificates have the correct permissions.

```
chown postgres /full/path/to/postgres/certificates/* && \
chgrp postgres /full/path/to/postgres/certificates/* && \
chmod 600 /full/path/to/postgres/certificates/*
```

Change the connection string in the `/ ​var/opt/jfrog/xray/var/etc/system.yaml​​` file.

```
postgres://xray:xray@postgres:5432/xraydb?sslrootcert=/full/path/to/xray/certificates/ca_certificate.crt&sslkey=/full/path/to/xray/certificates/client.key&sslcert=/full/path/to/xray/certificates/client.crt&sslmode=verify-ca
```

Make sure you have an Xray user and group.

```
groupadd -g 1035 xray && \
adduser xray --uid 1035 --gid 1035
```

Assign permissions to the certificates.

```
chown xray /full/path/to/xray/certificates/* && \
chgrp xray /full/path/to/xray/certificates/* && \
chmod 600 /full/path/to/xray/certificates/*
```

Restart all the Xray services.

```
bash /opt/jfrog/xray/scripts/xray.sh restart all
```
