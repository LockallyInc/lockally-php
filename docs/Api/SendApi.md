# Lockally\SDK\SendApi

Programmatic outbound mail (single, batch, scheduled, templated) + delivery stats

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**cancelMessage()**](SendApi.md#cancelMessage) | **DELETE** /v1/messages/{id} | Cancel a scheduled send |
| [**getMessage()**](SendApi.md#getMessage) | **GET** /v1/messages/{id} | Get message status |
| [**getMessageStats()**](SendApi.md#getMessageStats) | **GET** /v1/messages/stats | Aggregate delivery stats |
| [**listMessages()**](SendApi.md#listMessages) | **GET** /v1/messages | List outbound messages |
| [**sendEmail()**](SendApi.md#sendEmail) | **POST** /v1/send | Send an email |
| [**sendEmailBatch()**](SendApi.md#sendEmailBatch) | **POST** /v1/send/batch | Send a batch of emails |


## `cancelMessage()`

```php
cancelMessage($id)
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
    $apiInstance->cancelMessage($id);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->cancelMessage: ', $e->getMessage(), PHP_EOL;
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

## `getMessage()`

```php
getMessage($id): \Lockally\SDK\Model\MessageDetail
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
    $result = $apiInstance->getMessage($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->getMessage: ', $e->getMessage(), PHP_EOL;
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

## `getMessageStats()`

```php
getMessageStats($from, $to, $domain): \Lockally\SDK\Model\MessageStats
```

Aggregate delivery stats

Counts by delivery outcome (delivered/bounced/deferred/complaint) plus rates over a window, from the delivery-event store. Privacy-first: this reflects what receiving servers reported, NOT whether a human opened the mail, Lockally does no open/click tracking.

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
    $result = $apiInstance->getMessageStats($from, $to, $domain);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->getMessageStats: ', $e->getMessage(), PHP_EOL;
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

## `listMessages()`

```php
listMessages($status, $sender, $q, $since, $cursor, $limit): \Lockally\SDK\Model\ListMessages200Response
```

List outbound messages

Returns recent outbound messages for the calling tenant, sorted newest first.

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
    $result = $apiInstance->listMessages($status, $sender, $q, $since, $cursor, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->listMessages: ', $e->getMessage(), PHP_EOL;
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

[**\Lockally\SDK\Model\ListMessages200Response**](../Model/ListMessages200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendEmail()`

```php
sendEmail($idempotency_key, $send_email_request): \Lockally\SDK\Model\SendEmail200Response
```

Send an email

Submits an email for delivery via lockally. Returns 202 immediately once the message is accepted into lockally's queue; the actual SMTP submission to the recipient is async. Track delivery via `GET /v1/messages/{id}` or webhook subscriptions for `delivery.delivered` / `delivery.bounced` / `delivery.complaint`.  **Idempotency-Key required.** Any unique string per send, 24-hour dedupe window. Repeated calls with the same key return byte-exact the original response and do NOT create a duplicate message.  **Sender authorisation.** `from` must be an address the calling tenant owns on a verified domain. A mailbox always qualifies. On business and combined accounts an **alias** qualifies too, so a send-only address such as `no-reply@` need not be a billed seat. An alias on an unverified domain, or one belonging to another account, is refused with `403`. A catch-all creates no aliases and so grants no sending rights.  **Rate cap.** Per-tenant `rate_cap_per_min` (returned on `/v1/tenant`) is enforced, 429 with `Retry-After: 60` once tripped.  **Recipient warning.** Over 25 total recipients (To+Cc+Bcc) sets a `warning` field in the response, large fan-outs queue noticeably at scale. Hard cap is 100/send.  **Not every success is a 202.** Check the status code, not just the body. A `200` means nothing was queued: either every recipient was already suppressed, or the call used a test key and the send was simulated. Both are successes, and neither produces a real delivery. See the `200` response below.  **Warm-up headers.** While the platform is in its outbound warm-up ramp, accepted sends carry `X-Warmup-Day`, `X-Warmup-Daily-Cap` and `X-Warmup-Used-Today`. They describe a platform-wide cap shared by every tenant, not your own allowance, and they disappear once the ramp finishes. Hitting the cap returns 429.

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
$send_email_request = new \Lockally\SDK\Model\SendEmailRequest(); // \Lockally\SDK\Model\SendEmailRequest

try {
    $result = $apiInstance->sendEmail($idempotency_key, $send_email_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->sendEmail: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **idempotency_key** | **string**|  | |
| **send_email_request** | [**\Lockally\SDK\Model\SendEmailRequest**](../Model/SendEmailRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\SendEmail200Response**](../Model/SendEmail200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `sendEmailBatch()`

```php
sendEmailBatch($idempotency_key, $send_email_batch_request): \Lockally\SDK\Model\SendEmailBatch200Response
```

Send a batch of emails

Sends up to 500 messages in one call. Each is validated and enqueued independently, a bad message fails only its own slot (partial success, HTTP 200). One `Idempotency-Key` header covers the batch; per-message keys are derived as `<key>:<index>`.

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
$send_email_batch_request = new \Lockally\SDK\Model\SendEmailBatchRequest(); // \Lockally\SDK\Model\SendEmailBatchRequest

try {
    $result = $apiInstance->sendEmailBatch($idempotency_key, $send_email_batch_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SendApi->sendEmailBatch: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **idempotency_key** | **string**|  | |
| **send_email_batch_request** | [**\Lockally\SDK\Model\SendEmailBatchRequest**](../Model/SendEmailBatchRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\SendEmailBatch200Response**](../Model/SendEmailBatch200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
