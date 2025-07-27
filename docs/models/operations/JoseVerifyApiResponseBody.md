# JoseVerifyApiResponseBody


## Fields

| Field                                                      | Type                                                       | Required                                                   | Description                                                |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| `resultCode`                                               | *Optional\<String>*                                        | :heavy_minus_sign:                                         | The code which represents the result of the API call.      |
| `resultMessage`                                            | *Optional\<String>*                                        | :heavy_minus_sign:                                         | A short message which explains the result of the API call. |
| `valid`                                                    | *Optional\<Boolean>*                                       | :heavy_minus_sign:                                         | The result of the verification on the JOSE object.<br/>    |
| `signatureValid`                                           | *Optional\<Boolean>*                                       | :heavy_minus_sign:                                         | The result of the signature verification.<br/>             |
| `missingClaims`                                            | List\<*String*>                                            | :heavy_minus_sign:                                         | The list of missing claims.<br/>                           |
| `invalidClaims`                                            | List\<*String*>                                            | :heavy_minus_sign:                                         | The list of invalid claims.<br/>                           |
| `errorDescriptions`                                        | List\<*String*>                                            | :heavy_minus_sign:                                         | The list of error messages.<br/>                           |