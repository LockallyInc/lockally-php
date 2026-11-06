# SendEmailBatchRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**messages** | [**\Lockally\SDK\Model\SendMessage[]**](SendMessage.md) |  |
**variables** | **array<string,string>** | Template variables every message in the batch inherits. Each message&#39;s own &#x60;variables&#x60; override these key by key, so shared values are written once and per-recipient ones stay per-recipient.  Without this, a 500-message batch repeats every shared variable 500 times: most of the payload, and 500 places for one of them to differ by a typo. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
