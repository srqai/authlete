# AuthTokenGetListApiRequest


## Fields

| Field                                                              | Type                                                               | Required                                                           | Description                                                        |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `clientIdentifier`                                                 | *Optional\<String>*                                                | :heavy_minus_sign:                                                 | Client Identifier (client ID or client ID alias).<br/>             |
| `subject`                                                          | *Optional\<String>*                                                | :heavy_minus_sign:                                                 | Unique user ID.<br/>                                               |
| `start`                                                            | *Optional\<Integer>*                                               | :heavy_minus_sign:                                                 | Start index of search results (inclusive). The default value is 0. |
| `end`                                                              | *Optional\<Integer>*                                               | :heavy_minus_sign:                                                 | End index of search results (exclusive). The default value is 5.<br/> |
| `serviceId`                                                        | *String*                                                           | :heavy_check_mark:                                                 | A service ID.                                                      |