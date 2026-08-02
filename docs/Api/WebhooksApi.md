# Lockally\SDK\WebhooksApi

HMAC-signed event subscriptions

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**v1WebhooksGet()**](WebhooksApi.md#v1WebhooksGet) | **GET** /v1/webhooks | List webhooks |
| [**v1WebhooksIdDelete()**](WebhooksApi.md#v1WebhooksIdDelete) | **DELETE** /v1/webhooks/{id} | Delete a webhook |
| [**v1WebhooksIdPatch()**](WebhooksApi.md#v1WebhooksIdPatch) | **PATCH** /v1/webhooks/{id} | Update a webhook |
| [**v1WebhooksPost()**](WebhooksApi.md#v1WebhooksPost) | **POST** /v1/webhooks | Create a webhook |


## `v1WebhooksGet()`

```php
v1WebhooksGet(): \Lockally\SDK\Model\V1WebhooksGet200Response
```

List webhooks

Returns the calling tenant's webhook subscriptions. Never returns the signing secret — only metadata.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->v1WebhooksGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->v1WebhooksGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\V1WebhooksGet200Response**](../Model/V1WebhooksGet200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1WebhooksIdDelete()`

```php
v1WebhooksIdDelete($id)
```

Delete a webhook

Hard-delete; cascades to `webhook_deliveries` history.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->v1WebhooksIdDelete($id);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->v1WebhooksIdDelete: ', $e->getMessage(), PHP_EOL;
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

## `v1WebhooksIdPatch()`

```php
v1WebhooksIdPatch($id, $v1_webhooks_id_patch_request): \Lockally\SDK\Model\Webhook
```

Update a webhook

Supply at least one of `url`, `events`, `paused`. Setting `paused` to `false` ALSO resets `consecutive_failures` to 0 — re-arms the 50-failure auto-pause counter.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$v1_webhooks_id_patch_request = new \Lockally\SDK\Model\V1WebhooksIdPatchRequest(); // \Lockally\SDK\Model\V1WebhooksIdPatchRequest

try {
    $result = $apiInstance->v1WebhooksIdPatch($id, $v1_webhooks_id_patch_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->v1WebhooksIdPatch: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **v1_webhooks_id_patch_request** | [**\Lockally\SDK\Model\V1WebhooksIdPatchRequest**](../Model/V1WebhooksIdPatchRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Webhook**](../Model/Webhook.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1WebhooksPost()`

```php
v1WebhooksPost($v1_webhooks_post_request): \Lockally\SDK\Model\Webhook
```

Create a webhook

Subscribes a URL to one or more event types. Returns the `signing_secret` ONCE in the response — store it immediately. The dispatcher signs every outbound POST per design L3:      X-Lockally-Signature: t=<unix>,v1=<hex(hmac_sha256(secret, t + \".\" + body))>  Verify on your end using HMAC-SHA256 with a 5-minute timestamp window (replay protection). A reference verifier ships in [internal/webhook](https://github.com/ucheigwedinma/lockally/blob/main/internal/webhook/sign.go).  Event names: see the [event catalogue](https://github.com/ucheigwedinma/lockally/blob/main/docs/v1-design.md#64-webhook-event-catalogue-v1).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\WebhooksApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$v1_webhooks_post_request = new \Lockally\SDK\Model\V1WebhooksPostRequest(); // \Lockally\SDK\Model\V1WebhooksPostRequest

try {
    $result = $apiInstance->v1WebhooksPost($v1_webhooks_post_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->v1WebhooksPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **v1_webhooks_post_request** | [**\Lockally\SDK\Model\V1WebhooksPostRequest**](../Model/V1WebhooksPostRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Webhook**](../Model/Webhook.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
