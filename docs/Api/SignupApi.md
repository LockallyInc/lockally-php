# Lockally\SDK\SignupApi

Self-serve tenant registration (public, no auth)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**signup()**](SignupApi.md#signup) | **POST** /v1/signup | Sign up a new tenant |


## `signup()`

```php
signup($signup_request): \Lockally\SDK\Model\V1AdminLoginPost200Response
```

Sign up a new tenant

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new Lockally\SDK\Api\SignupApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$signup_request = new \Lockally\SDK\Model\SignupRequest(); // \Lockally\SDK\Model\SignupRequest

try {
    $result = $apiInstance->signup($signup_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SignupApi->signup: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **signup_request** | [**\Lockally\SDK\Model\SignupRequest**](../Model/SignupRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\V1AdminLoginPost200Response**](../Model/V1AdminLoginPost200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
