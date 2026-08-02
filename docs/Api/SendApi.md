# Lockally\SDK\SendApi

Programmatic outbound mail (single, batch, scheduled, templated) + delivery stats

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**v1MessagesGet()**](SendApi.md#v1MessagesGet) | **GET** /v1/messages | List outbound messages |
| [**v1MessagesIdDelete()**](SendApi.md#v1MessagesIdDelete) | **DELETE** /v1/messages/{id} | Cancel a scheduled send |
| [**v1MessagesIdGet()**](SendApi.md#v1MessagesIdGet) | **GET** /v1/messages/{id} | Get message status |
| [**v1MessagesStatsGet()**](SendApi.md#v1MessagesStatsGet) | **GET** /v1/messages/stats | Aggregate delivery stats |
| [**v1SendBatchPost()**](SendApi.md#v1SendBatchPost) | **POST** /v1/send/batch | Send a batch of emails |
| [**v1SendPost()**](SendApi.md#v1SendPost) | **POST** /v1/send | Send an email |


## `v1MessagesGet()`

```php
v1MessagesGet($status, $sender, $q, $since, $cursor, $limit): \Lockally\SDK\Model\V1MessagesGet200Response
```

List outbound messages

Returns recent outbound messages for the calling tenant, sorted newest first. Backs the send-status pill in the SvelteKit /sends view and the outbound search box.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\SendApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$status = 'status_example'; // string
$sender = 'sender_example'; // string | Exact match against the `from` mailbox.
$q = 'q_example'; // string | Free-text search across subject + sender.
$since = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Only messages queued at or after this RFC 3339 instant.
$cursor = 'cursor_example'; // string | queued_at of the prior page boundary. Pass back the `next_cursor` returned by the previous call.
$limit = 50; // int

try {
    $result = $apiInstance->v1MessagesGet($status, $sender, $q, $since, $cursor, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->v1MessagesGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **status** | **string**|  | [optional] |
| **sender** | **string**| Exact match against the &#x60;from&#x60; mailbox. | [optional] |
| **q** | **string**| Free-text search across subject + sender. | [optional] |
| **since** | **\DateTime**| Only messages queued at or after this RFC 3339 instant. | [optional] |
| **cursor** | **string**| queued_at of the prior page boundary. Pass back the &#x60;next_cursor&#x60; returned by the previous call. | [optional] |
| **limit** | **int**|  | [optional] [default to 50] |

### Return type

[**\Lockally\SDK\Model\V1MessagesGet200Response**](../Model/V1MessagesGet200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1MessagesIdDelete()`

```php
v1MessagesIdDelete($id)
```

Cancel a scheduled send

Cancels a still-scheduled message (future queued_at). Already sending/sent → 409.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\SendApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->v1MessagesIdDelete($id);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->v1MessagesIdDelete: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

void (empty response body)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1MessagesIdGet()`

```php
v1MessagesIdGet($id): \Lockally\SDK\Model\MessageDetail
```

Get message status

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\SendApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->v1MessagesIdGet($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->v1MessagesIdGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\MessageDetail**](../Model/MessageDetail.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1MessagesStatsGet()`

```php
v1MessagesStatsGet($from, $to, $domain): \Lockally\SDK\Model\MessageStats
```

Aggregate delivery stats

Counts by delivery outcome (delivered/bounced/deferred/complaint) plus rates over a window, from the delivery-event store. Privacy-first: this reflects what receiving servers reported, NOT whether a human opened the mail — Lockally does no open/click tracking.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\SendApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$from = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Window start (default 7 days ago).
$to = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime | Window end (default now).
$domain = 'domain_example'; // string | Filter by sender domain.

try {
    $result = $apiInstance->v1MessagesStatsGet($from, $to, $domain);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->v1MessagesStatsGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **from** | **\DateTime**| Window start (default 7 days ago). | [optional] |
| **to** | **\DateTime**| Window end (default now). | [optional] |
| **domain** | **string**| Filter by sender domain. | [optional] |

### Return type

[**\Lockally\SDK\Model\MessageStats**](../Model/MessageStats.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1SendBatchPost()`

```php
v1SendBatchPost($idempotency_key, $v1_send_batch_post_request): \Lockally\SDK\Model\V1SendBatchPost200Response
```

Send a batch of emails

Sends up to 500 messages in one call. Each is validated and enqueued independently — a bad message fails only its own slot (partial success, HTTP 200). One `Idempotency-Key` header covers the batch; per-message keys are derived as `<key>:<index>`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\SendApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$idempotency_key = 'idempotency_key_example'; // string
$v1_send_batch_post_request = new \Lockally\SDK\Model\V1SendBatchPostRequest(); // \Lockally\SDK\Model\V1SendBatchPostRequest

try {
    $result = $apiInstance->v1SendBatchPost($idempotency_key, $v1_send_batch_post_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->v1SendBatchPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **idempotency_key** | **string**|  | |
| **v1_send_batch_post_request** | [**\Lockally\SDK\Model\V1SendBatchPostRequest**](../Model/V1SendBatchPostRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\V1SendBatchPost200Response**](../Model/V1SendBatchPost200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1SendPost()`

```php
v1SendPost($idempotency_key, $v1_send_post_request): \Lockally\SDK\Model\V1SendPost202Response
```

Send an email

Submits an email for delivery via lockally. Returns 202 immediately once the message is accepted into lockally's queue; the actual SMTP submission to the recipient is async. Track delivery via `GET /v1/messages/{id}` or webhook subscriptions for `delivery.delivered` / `delivery.bounced` / `delivery.complaint`.  **Idempotency-Key required.** Per design L7 — any unique string per send, 24-hour dedupe window. Repeated calls with the same key return byte-exact the original response and do NOT create a duplicate message.  **Sender authorisation.** `from` must be a non-disabled mailbox owned by the calling tenant on a verified domain. Sending from aliases is not yet supported.  **Rate cap.** Per-tenant `rate_cap_per_min` (returned on `/v1/tenant`) is enforced — 429 with `Retry-After: 60` once tripped.  **Recipient warning.** Over 25 total recipients (To+Cc+Bcc) sets a `warning` field in the response — large fan-outs queue noticeably at scale. Hard cap is 100/send.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\SendApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$idempotency_key = 'idempotency_key_example'; // string
$v1_send_post_request = new \Lockally\SDK\Model\V1SendPostRequest(); // \Lockally\SDK\Model\V1SendPostRequest

try {
    $result = $apiInstance->v1SendPost($idempotency_key, $v1_send_post_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->v1SendPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **idempotency_key** | **string**|  | |
| **v1_send_post_request** | [**\Lockally\SDK\Model\V1SendPostRequest**](../Model/V1SendPostRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\V1SendPost202Response**](../Model/V1SendPost202Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
