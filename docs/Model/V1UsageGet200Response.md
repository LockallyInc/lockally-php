# V1UsageGet200Response

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**mailboxes_active** | **int** | Mailboxes that are neither disabled nor soft-deleted. |
**mailboxes_total** | **int** | All mailboxes for this tenant, including disabled/soft-deleted. | [optional]
**domains_verified** | **int** | Domains that have passed DNS verification. | [optional]
**domains_total** | **int** |  | [optional]
**messages_sent_last_60s** | **int** | Sends in the 60-second window ending now. Used by the rate-cap check. | [optional]
**messages_sent_today_utc** | **int** | Sends since 00:00 UTC. Compared against &#x60;daily_msg_quota&#x60;. | [optional]
**messages_sent_last_30d** | **int** | Rolling 30-day send count (not calendar month). | [optional]
**bytes_stored** | **int** | Lifetime sum of &#x60;messages.size_bytes&#x60; for this tenant. | [optional]
**rate_cap_per_min** | **int** | Per-tenant outbound rate cap (sends per minute). | [optional]
**daily_msg_quota** | **int** | Per-tenant daily send quota (UTC day boundary). | [optional]
**webhooks_total** | **int** |  | [optional]
**webhooks_paused** | **int** | Webhook subscriptions auto-paused after 50 consecutive failures (LT2). | [optional]
**generated_at** | **\DateTime** | When this snapshot was generated, RFC 3339 UTC. |

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
