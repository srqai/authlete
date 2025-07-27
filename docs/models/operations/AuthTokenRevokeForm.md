# AuthTokenRevokeForm


## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `token`                                                          | *String*                                                         | :heavy_check_mark:                                               | Access or refresh token to be revoked                            |
| `tokenTypeHint`                                                  | *Optional\<String>*                                              | :heavy_minus_sign:                                               | Hint about the type of the token (access_token or refresh_token) |