# Lockally\SDK\HealthApi

Liveness checks

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**healthCheck()**](HealthApi.md#healthCheck) | **GET** /healthz | Liveness check |


## `healthCheck()`

```php
healthCheck(): \Lockally\SDK\Model\HealthCheck200Response
```

Liveness check

Returns 200 if the process is up and the database pings cleanly. No authentication required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new Lockally\SDK\Api\HealthApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $result = $apiInstance->healthCheck();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling HealthApi->healthCheck: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\HealthCheck200Response**](../Model/HealthCheck200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
