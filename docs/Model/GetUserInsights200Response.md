# GetUserInsights200Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**recently_added** | [**\Lockally\SDK\Model\UserEvent[]**](UserEvent.md) |  | [optional]
**recently_suspended** | [**\Lockally\SDK\Model\UserEvent[]**](UserEvent.md) |  | [optional]
**inactive_30d** | [**\Lockally\SDK\Model\UserEvent[]**](UserEvent.md) |  | [optional]
**seats_used** | **int** |  | [optional]
**seats_alloc** | **int** |  | [optional]
**seats_capped** | **bool** | True only on tiers with a hard seat cap (Free, Founder). On unlimited/per-seat tiers seats_alloc merely tracks the live mailbox count, so seats_used &#x3D;&#x3D; seats_alloc is normal and must not be read as &#39;at capacity&#39;. | [optional]
**generated_at** | **\DateTime** |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
