# VciBatchIssueApiRequestBody


## Fields

| Field                                                                            | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `accessToken`                                                                    | *Optional\<String>*                                                              | :heavy_minus_sign:                                                               | The access token that came along with the credential request.                    |
| `orders`                                                                         | List\<[VciBatchIssueApiOrder](../../models/operations/VciBatchIssueApiOrder.md)> | :heavy_minus_sign:                                                               | The instructions for issuance of credentials and/or transaction IDs.             |