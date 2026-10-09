# Domain

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**tenant_id** | **string** |  |
**domain** | **string** |  |
**verification_token** | **string** |  |
**verified** | **bool** |  |
**verified_at** | **\DateTime** |  | [optional]
**dkim_selector** | **string** |  |
**dkim_public_record** | **string** |  |
**created_at** | **\DateTime** |  |
**records** | [**\Lockally\SDK\Model\DNSRecord[]**](DNSRecord.md) | DNS records the tenant must publish under their own DNS. | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
