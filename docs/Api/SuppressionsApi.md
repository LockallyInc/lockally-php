# Lockally\SDK\SuppressionsApi

Suppression list — recipients Lockally won&#39;t mail (unsubscribes, complaints, hard bounces)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**v1SuppressionsEmailDelete()**](SuppressionsApi.md#v1SuppressionsEmailDelete) | **DELETE** /v1/suppressions/{email} | Remove a suppression |
| [**v1SuppressionsEmailGet()**](SuppressionsApi.md#v1SuppressionsEmailGet) | **GET** /v1/suppressions/{email} | Check whether an address is suppressed |
| [**v1SuppressionsGet()**](SuppressionsApi.md#v1SuppressionsGet) | **GET** /v1/suppressions | List suppressed recipients |
| [**v1SuppressionsPost()**](SuppressionsApi.md#v1SuppressionsPost) | **POST** /v1/suppressions | Add a suppression |


## `v1SuppressionsEmailDelete()`

```php
v1SuppressionsEmailDelete($email)
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
    $apiInstance->v1SuppressionsEmailDelete($email);
} catch (Exception $e) {
    echo 'Exception when calling SuppressionsApi->v1SuppressionsEmailDelete: ', $e->getMessage(), PHP_EOL;
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

## `v1SuppressionsEmailGet()`

```php
v1SuppressionsEmailGet($email): \Lockally\SDK\Model\Suppression
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
    $result = $apiInstance->v1SuppressionsEmailGet($email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SuppressionsApi->v1SuppressionsEmailGet: ', $e->getMessage(), PHP_EOL;
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

## `v1SuppressionsGet()`

```php
v1SuppressionsGet($reason, $cursor, $limit): \Lockally\SDK\Model\V1SuppressionsGet200Response
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
    $result = $apiInstance->v1SuppressionsGet($reason, $cursor, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SuppressionsApi->v1SuppressionsGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **reason** | **string**|  | [optional] |
| **cursor** | **string**|  | [optional] |
| **limit** | **int**|  | [optional] [default to 50] |

### Return type

[**\Lockally\SDK\Model\V1SuppressionsGet200Response**](../Model/V1SuppressionsGet200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1SuppressionsPost()`

```php
v1SuppressionsPost($v1_suppressions_post_request): \Lockally\SDK\Model\Suppression
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
$v1_suppressions_post_request = new \Lockally\SDK\Model\V1SuppressionsPostRequest(); // \Lockally\SDK\Model\V1SuppressionsPostRequest

try {
    $result = $apiInstance->v1SuppressionsPost($v1_suppressions_post_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SuppressionsApi->v1SuppressionsPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **v1_suppressions_post_request** | [**\Lockally\SDK\Model\V1SuppressionsPostRequest**](../Model/V1SuppressionsPostRequest.md)|  | |

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
