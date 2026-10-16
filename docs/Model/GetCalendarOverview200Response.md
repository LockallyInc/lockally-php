# GetCalendarOverview200Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**total_calendars** | **int** |  | [optional]
**active_calendars** | **int** | Calendars with an event created, edited or held in the last 30 days. | [optional]
**shared_calendars** | **int** | Calendars visible to the whole organization. | [optional]
**events_this_month** | **int** | Events on every calendar, in the account&#39;s own timezone. | [optional]
**upcoming_org_events** | **int** | Future events on organization-visible calendars. | [optional]
**bookable_resources** | **int** | Resources that are not disabled. | [optional]
**access_granted** | **int** | People who own a calendar or are named on one. | [optional]
**access_org_wide** | **int** | Everyone who can see an organization calendar; 0 when none exists. | [optional]
**activity** | [**\Lockally\SDK\Model\GetCalendarOverview200ResponseActivityInner[]**](GetCalendarOverview200ResponseActivityInner.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
