# Lockally\SDK\SuppressionsApi

Suppression list — recipients Lockally won&#39;t mail (unsubscribes, complaints, hard bounces)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createSuppression()**](SuppressionsApi.md#createSuppression) | **POST** /v1/suppressions | Add a suppression |
| [**deleteSuppression()**](SuppressionsApi.md#deleteSuppression) | **DELETE** /v1/suppressions/{email} | Remove a suppression |
| [**getSuppression()**](SuppressionsApi.md#getSuppression) | **GET** /v1/suppressions/{email} | Check whether an address is suppressed |
| [**listSuppressions()**](SuppressionsApi.md#listSuppressions) | **GET** /v1/suppressions | List suppressed recipients |


## `createSuppression()`

```php
createSuppression($create_suppression_request): \Lockally\SDK\Model\Suppression
```

Add a suppression

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\SuppressionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_suppression_request = new \Lockally\SDK\Model\CreateSuppressionRequest(); // \Lockally\SDK\Model\CreateSuppressionRequest

try {
    $result = $apiInstance->createSuppression($create_suppression_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SuppressionsApi->createSuppression: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_suppression_request** | [**\Lockally\SDK\Model\CreateSuppressionRequest**](../Model/CreateSuppressionRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Suppression**](../Model/Suppression.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteSuppression()`

```php
deleteSuppression($email)
```

Remove a suppression

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\SuppressionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email = 'email_example'; // string

try {
    $apiInstance->deleteSuppression($email);
} catch (Exception $e) {
    echo 'Exception when calling SuppressionsApi->deleteSuppression: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |

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

## `getSuppression()`

```php
getSuppression($email): \Lockally\SDK\Model\Suppression
```

Check whether an address is suppressed

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\SuppressionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email = 'email_example'; // string

try {
    $result = $apiInstance->getSuppression($email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SuppressionsApi->getSuppression: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Suppression**](../Model/Suppression.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listSuppressions()`

```php
listSuppressions($reason, $cursor, $limit): \Lockally\SDK\Model\ListSuppressions200Response
```

List suppressed recipients

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\SuppressionsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$reason = 'reason_example'; // string
$cursor = 'cursor_example'; // string
$limit = 50; // int

try {
    $result = $apiInstance->listSuppressions($reason, $cursor, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SuppressionsApi->listSuppressions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **reason** | **string**|  | [optional] |
| **cursor** | **string**|  | [optional] |
| **limit** | **int**|  | [optional] [default to 50] |

### Return type

[**\Lockally\SDK\Model\ListSuppressions200Response**](../Model/ListSuppressions200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
