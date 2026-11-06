# CreateApiKey201Response

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
**test** | **bool** | True for an lk_test_* key: the whole request path runs but a send never reaches the mail server and nothing counts against the account. | [optional]
**expires_at** | **\DateTime** | When the key stops authenticating. Null means it does not expire, which is how every key behaved before expiry existed. Enforced at authentication, so the key fails the first request after this moment rather than whenever a sweep runs. | [optional]
**rotated_to** | **string** | The successor issued by &#x60;POST /v1/api-keys/{id}/rotate&#x60;. Set on the PREDECESSOR, so you can see which key replaced this one while both still work through the overlap window. | [optional]
**secret** | **string** | The full &#x60;lk_live_&lt;prefix&gt;_&lt;secret&gt;&#x60; token. Shown ONCE. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
