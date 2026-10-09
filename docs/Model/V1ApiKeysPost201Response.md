# V1ApiKeysPost201Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**tenant_id** | **string** |  |
**prefix** | **string** | 8-char public prefix; safe to store and display. |
**scopes** | **string[]** |  |
**label** | **string** |  |
**last_used_at** | **\DateTime** |  | [optional]
**revoked_at** | **\DateTime** |  | [optional]
**created_at** | **\DateTime** |  |
**secret** | **string** | The full &#x60;lk_live_&lt;prefix&gt;_&lt;secret&gt;&#x60; token. Shown ONCE. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
