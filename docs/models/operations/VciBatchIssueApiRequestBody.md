# VciBatchIssueApiRequestBody


## Fields

| Field                                                                                | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `accessToken`                                                                        | *Optional\<String>*                                                                  | :heavy_minus_sign:                                                                   | The access token that came along with the credential request.                        |
| `orders`                                                                             | List\<[CredentialIssuanceOrder](../../models/components/CredentialIssuanceOrder.md)> | :heavy_minus_sign:                                                                   | The instructions for issuance of credentials and/or transaction IDs.                 |