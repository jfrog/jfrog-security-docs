# Revoke and Create Registration Token

**Description:** Revokes a specified registration token and generates a new, active token in a single operation.

**Security:** Requires a valid Identity Token with Admin privileges.

**Usage:** `DELETE /runtime/api/v1/registration_token/{token}`

**Produces:** `application`/`json`

#### Request Path Parameters

| Name    | Type   | Required/Optional | Description                           |
| ------- | ------ | ----------------- | ------------------------------------- |
| `token` | string | Mandatory         | The registration token to be revoked. |

#### Response Body

| Name           | Type   | Description                             |
| -------------- | ------ | --------------------------------------- |
| `access_token` | string | The newly generated registration token. |

**Response Codes**

| 201 | OK                                              |
| --- | ----------------------------------------------- |
| 401 | Unauthorized                                    |
| 403 | Permission denied                               |
| 404 | Not found - The specified token does not exist. |
| 500 | Internal server error                           |

#### Examples

**Request Sample**

```
curl --location --request DELETE 'https://<JFROG_URL>/runtime/api/v1/registration_token/<TOKEN_TO_REVOKE>' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer <IDENTITY_TOKEN>'
```

**Successful Response Sample**

```
{
  "access_token": "new_token"
}
```

**Error Response Sample**

```
{
  "error": "registration token not found"
}
```
