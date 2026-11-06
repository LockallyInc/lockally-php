# BatchResult

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**index** | **int** |  | [optional]
**id** | **string** |  | [optional]
**message_id** | **string** |  | [optional]
**status** | **string** | \&quot;suppressed\&quot; means every recipient of that slot was on your suppression list, and it carries no id or message_id. \&quot;delivered\&quot; only appears on a test key: the send was simulated, not transmitted. | [optional]
**error** | **string** | Present when this message failed; the others are then absent. | [optional]
**warning** | **string** | Advisory, and NOT a failure. Today the only one is a template variable the template referenced and the request never supplied, which rendered as the empty string. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
