# Renewing Registration Tokens

Registration tokens used by JFrog Runtime Security instances have an expiration period. To ensure the uninterrupted operation of the controller and sensors, the registration token must be renewed before it expires.

1. Retrieve the current registration token using either the [Get Registration Token](../apis/get-registration-token.md) API, or the UI:&#x20;
   1. Navigate to **Administration** > **Runtime Management** > **Install Runtime**
   2. Select the **Provider**.
   3. Enter the **Cluster name**.
   4. Select **Next**.
   5. In the **Deploy the sensor** window, locate the code block.
   6. Copy the value of:

```ini
registrationToken=<token>
```

2.  Revoke the existing registration token, using the Revoke and [Create Registration Token](../apis/revoke-and-create-registration-token.md) API.

    Revoking will generate a new registration token.
3. Update all Runtime clusters with the new registration token.
