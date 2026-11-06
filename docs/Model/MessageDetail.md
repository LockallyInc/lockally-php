# MessageDetail

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**tenant_id** | **string** |  |
**message_id** | **string** | RFC 5322 Message-ID header, including angle brackets. |
**sender** | **string** |  |
**recipients** | **string[]** |  |
**subject** | **string** |  | [optional]
**status** | **string** |  |
**queued_at** | **\DateTime** |  |
**updated_at** | **\DateTime** |  |
**bounce_reason** | **string** |  | [optional]
**size_bytes** | **int** |  | [optional]
**metadata** | **array<string,string>** | The sender&#39;s own key/value from the send request. Always present; &#x60;{}&#x60; when none was set. | [optional]
**tags** | **string[]** | Grouping labels, lowercased and deduplicated. Always present; &#x60;[]&#x60; when none were set. | [optional]
**from** | **string** |  | [optional]
**to** | **string[]** |  | [optional]
**cc** | **string[]** |  | [optional]
**bcc** | **string[]** |  | [optional]
**text** | **string** |  | [optional]
**html** | **string** |  | [optional]
**headers** | **array<string,string>** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
