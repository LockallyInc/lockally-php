# TenantHealthCheck

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**key** | **string** | Stable identifier, today one of &#x60;domain_verification&#x60;, &#x60;smtp&#x60;, &#x60;storage&#x60;, &#x60;security&#x60;. Treat unknown keys as new checks, not errors. |
**label** | **string** | Human-readable name for display. |
**status** | **string** | &#x60;healthy&#x60;, &#x60;warning&#x60; or &#x60;critical&#x60;. |
**detail** | **string** |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
