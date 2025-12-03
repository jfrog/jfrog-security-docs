# Get Registration Token

**Description:** Retrieves the current, active registration token. This token is used to register new cluster nodes.

**Security:** Requires a valid Identity Token with Admin privileges.

**Usage:** `POST /runtime/api/v1/registration_token`

**Produces:** `application/json`

#### Response Body

| `access_token` | string | The current, active registration token. |
| -------------- | ------ | --------------------------------------- |

**Response Codes**

| Status Code | Description           |
| ----------- | --------------------- |
| 201         | OK                    |
| 401         | Unauthorized          |
| 403         | Permission denied     |
| 500         | Internal server error |

#### Examples

**Request Sample**

```
curl --location --request POST 'https://<JFROG_URL>/runtime/api/v1/registration_token' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer <IDENTITY_TOKEN>'
```

Successful Response Sample

```
{
  "access_token": "current_token"
}
```
