# Lockally\SDK\WebhooksApi

HMAC-signed event subscriptions

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createWebhook()**](WebhooksApi.md#createWebhook) | **POST** /v1/webhooks | Create a webhook |
| [**deleteWebhook()**](WebhooksApi.md#deleteWebhook) | **DELETE** /v1/webhooks/{id} | Delete a webhook |
| [**listWebhooks()**](WebhooksApi.md#listWebhooks) | **GET** /v1/webhooks | List webhooks |
| [**updateWebhook()**](WebhooksApi.md#updateWebhook) | **PATCH** /v1/webhooks/{id} | Update a webhook |


## `createWebhook()`

```php
createWebhook($create_webhook_request): \Lockally\SDK\Model\Webhook
```

Create a webhook

Subscribes a URL to one or more event types. Returns the `signing_secret` ONCE in the response, store it immediately. Every outbound POST is signed:      X-Lockally-Signature: t=<unix>,v1=<hex(hmac_sha256(secret, t + \".\" + body))>  Verify on your end using HMAC-SHA256 with a 5-minute timestamp window (replay protection). A reference verifier ships in [Signature verification](https://developers.lockally.com/webhooks/verification/).  Event names: see the [event catalogue](https://developers.lockally.com/webhooks/events/).

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
$create_webhook_request = new \Lockally\SDK\Model\CreateWebhookRequest(); // \Lockally\SDK\Model\CreateWebhookRequest

try {
    $result = $apiInstance->createWebhook($create_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->createWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_webhook_request** | [**\Lockally\SDK\Model\CreateWebhookRequest**](../Model/CreateWebhookRequest.md)|  | |

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

## `deleteWebhook()`

```php
deleteWebhook($id)
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
    $apiInstance->deleteWebhook($id);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->deleteWebhook: ', $e->getMessage(), PHP_EOL;
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

## `listWebhooks()`

```php
listWebhooks(): \Lockally\SDK\Model\ListWebhooks200Response
```

List webhooks

Returns the calling tenant's webhook subscriptions. Never returns the signing secret, only metadata.

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
    $result = $apiInstance->listWebhooks();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->listWebhooks: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\ListWebhooks200Response**](../Model/ListWebhooks200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateWebhook()`

```php
updateWebhook($id, $update_webhook_request): \Lockally\SDK\Model\Webhook
```

Update a webhook

Supply at least one of `url`, `events`, `paused`. Setting `paused` to `false` ALSO resets `consecutive_failures` to 0, re-arms the 50-failure auto-pause counter.

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
$update_webhook_request = new \Lockally\SDK\Model\UpdateWebhookRequest(); // \Lockally\SDK\Model\UpdateWebhookRequest

try {
    $result = $apiInstance->updateWebhook($id, $update_webhook_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling WebhooksApi->updateWebhook: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_webhook_request** | [**\Lockally\SDK\Model\UpdateWebhookRequest**](../Model/UpdateWebhookRequest.md)|  | |

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
