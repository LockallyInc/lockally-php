# CreateApiKeyRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**label** | **string** | Free-text identifier shown in the dashboard. |
**scopes** | **string[]** | Allowed scopes on this key. |
**test** | **bool** | Issue a test key (&#x60;lk_test_&#x60; prefix). A test key accepts sends, records them and fires a simulated delivery webhook without sending mail, and counts against no limit or allowance. | [optional] [default to false]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
