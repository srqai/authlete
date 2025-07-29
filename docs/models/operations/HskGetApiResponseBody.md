# HskGetApiResponseBody


## Fields

| Field                                                                       | Type                                                                        | Required                                                                    | Description                                                                 |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `resultCode`                                                                | *Optional\<String>*                                                         | :heavy_minus_sign:                                                          | The code which represents the result of the API call.                       |
| `resultMessage`                                                             | *Optional\<String>*                                                         | :heavy_minus_sign:                                                          | A short message which explains the result of the API call.                  |
| `action`                                                                    | [Optional\<HskGetApiAction>](../../models/operations/HskGetApiAction.md)    | :heavy_minus_sign:                                                          | Result of the API call                                                      |
| `hsk`                                                                       | [Optional\<HskGetApiHsk>](../../models/operations/HskGetApiHsk.md)          | :heavy_minus_sign:                                                          | Holds information about a key managed in an HSM (Hardware Security Module)<br/> |