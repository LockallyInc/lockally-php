# RotateApiKeyRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**grace_seconds** | **int** | How long the old key keeps working. Defaults to 24 hours, which is long enough to cut over without a scramble. Capped at 30 days, because beyond that \&quot;rotated\&quot; stops meaning anything. | [optional] [default to 86400]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
