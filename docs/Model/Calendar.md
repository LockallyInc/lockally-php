# Calendar

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**id** | **string** |  |
**tenant_id** | **string** |  |
**name** | **string** |  |
**color** | **string** |  | [optional]
**owner_email** | **string** |  | [optional]
**description** | **string** |  | [optional]
**calendar_type** | **string** | What the calendar is for. Separate from visibility, which is who may see it: a team calendar can be open to everyone and a department one restricted to named people. \&quot;personal\&quot; is a person&#39;s own and is not listed in the console&#39;s management table. | [optional]
**owner_unit** | **string** | The owning department or office. Empty on a personal calendar, which is owned by owner_email. | [optional]
**visibility** | **string** |  |
**access_department** | **string** | Which department may see it, when visibility is \&quot;department\&quot;. Matched against the department recorded on a user, so access follows a person between departments with no membership list to maintain. | [optional]
**status** | **string** | Archived keeps the calendar, its events and its feed, and stops it taking new events. | [optional]
**feed_url** | **string** |  | [optional]
**event_count** | **int** |  | [optional]
**created_at** | **\DateTime** |  |
**updated_at** | **\DateTime** |  |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
