# Lockally\SDK\AiApi

Metered LLM features (thread classification; BYOK or prepaid AI units)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**classifyThread()**](AiApi.md#classifyThread) | **POST** /v1/threads/{threadID}/classify | LLM-classify a thread |
| [**createAiUnitsCheckout()**](AiApi.md#createAiUnitsCheckout) | **POST** /v1/billing/ai-units/checkout | Buy prepaid AI units |
| [**getAiConfig()**](AiApi.md#getAiConfig) | **GET** /v1/ai-config | Read the tenant&#39;s AI configuration |
| [**updateAiConfig()**](AiApi.md#updateAiConfig) | **PUT** /v1/ai-config | Configure the AI tier |


## `classifyThread()`

```php
classifyThread($thread_id, $refresh): \Lockally\SDK\Model\ThreadClassification
```

LLM-classify a thread

Returns {intent, urgency, summary, suggested_action} via the tenant's AI tier (BYOK or prepaid units, see /v1/ai-config). Cached per thread state: unchanged threads return the cache free; ?refresh=true forces a re-run. A failed model call charges nothing. 402 when the AI tier is off.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AiApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$thread_id = 'thread_id_example'; // string
$refresh = True; // bool

try {
    $result = $apiInstance->classifyThread($thread_id, $refresh);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AiApi->classifyThread: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **thread_id** | **string**|  | |
| **refresh** | **bool**|  | [optional] |

### Return type

[**\Lockally\SDK\Model\ThreadClassification**](../Model/ThreadClassification.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createAiUnitsCheckout()`

```php
createAiUnitsCheckout(): \Lockally\SDK\Model\CreateAiUnitsCheckout200Response
```

Buy prepaid AI units

Body: {\"bundle\": \"100|500|2000\"}. One classification = one unit; bundles expire after 6 months. Admin session required. 503 until Paystack billing is configured.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AiApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->createAiUnitsCheckout();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AiApi->createAiUnitsCheckout: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\CreateAiUnitsCheckout200Response**](../Model/CreateAiUnitsCheckout200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getAiConfig()`

```php
getAiConfig(): \Lockally\SDK\Model\AiConfig
```

Read the tenant's AI configuration

Mode (off/byok/units), model, masked key hint, AI-unit balance, whether the units tier is available on this deployment.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AiApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getAiConfig();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AiApi->getAiConfig: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\AiConfig**](../Model/AiConfig.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateAiConfig()`

```php
updateAiConfig(): \Lockally\SDK\Model\AiConfigUpdate
```

Configure the AI tier

Body: {\"mode\": \"off|byok|units\", \"model\": \"...\", \"anthropic_key\": \"sk-ant-...\"}. BYOK keys are stored AES-256-GCM encrypted; the cleartext is never returned. Omit anthropic_key to keep the stored one.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AiApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->updateAiConfig();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AiApi->updateAiConfig: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\AiConfigUpdate**](../Model/AiConfigUpdate.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
