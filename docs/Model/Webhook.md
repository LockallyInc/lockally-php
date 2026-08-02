# Webhook

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**tenant_id** | **string** |  |
**url** | **string** |  |
**events** | **string[]** |  |
**paused** | **bool** |  |
**paused_at** | **\DateTime** |  | [optional]
**last_success_at** | **\DateTime** |  | [optional]
**last_failure_at** | **\DateTime** |  | [optional]
**consecutive_failures** | **int** |  |
**created_at** | **\DateTime** |  |
**signing_secret** | **string** | Hex-encoded HMAC-SHA256 key. Present ONLY on POST response. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
