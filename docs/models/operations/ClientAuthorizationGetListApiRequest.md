# ClientAuthorizationGetListApiRequest


## Fields

| Field                                                              | Type                                                               | Required                                                           | Description                                                        |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `serviceId`                                                        | *String*                                                           | :heavy_check_mark:                                                 | A service ID.                                                      |
| `subject`                                                          | *String*                                                           | :heavy_check_mark:                                                 | Unique user ID of an end-user.<br/>                                |
| `developer`                                                        | *Optional\<String>*                                                | :heavy_minus_sign:                                                 | Unique ID of a client developer.<br/>                              |
| `start`                                                            | *Optional\<Integer>*                                               | :heavy_minus_sign:                                                 | Start index of search results (inclusive). The default value is 0. |
| `end`                                                              | *Optional\<Integer>*                                               | :heavy_minus_sign:                                                 | End index of search results (exclusive). The default value is 5.<br/> |