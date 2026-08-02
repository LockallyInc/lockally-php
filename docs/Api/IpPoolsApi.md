# Lockally\SDK\IpPoolsApi



All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createDedicatedIPRequest()**](IpPoolsApi.md#createDedicatedIPRequest) | **POST** /v1/dedicated-ip-requests | Request a dedicated IP |
| [**getIPAssignment()**](IpPoolsApi.md#getIPAssignment) | **GET** /v1/ip-assignment | Get current IP assignment |
| [**listDedicatedIPRequests()**](IpPoolsApi.md#listDedicatedIPRequests) | **GET** /v1/dedicated-ip-requests | List dedicated IP requests |


## `createDedicatedIPRequest()`

```php
createDedicatedIPRequest($create_dedicated_ip_request_request): \Lockally\SDK\Model\DedicatedIPRequest
```

Request a dedicated IP

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\IpPoolsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_dedicated_ip_request_request = new \Lockally\SDK\Model\CreateDedicatedIPRequestRequest(); // \Lockally\SDK\Model\CreateDedicatedIPRequestRequest

try {
    $result = $apiInstance->createDedicatedIPRequest($create_dedicated_ip_request_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IpPoolsApi->createDedicatedIPRequest: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_dedicated_ip_request_request** | [**\Lockally\SDK\Model\CreateDedicatedIPRequestRequest**](../Model/CreateDedicatedIPRequestRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\DedicatedIPRequest**](../Model/DedicatedIPRequest.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getIPAssignment()`

```php
getIPAssignment(): \Lockally\SDK\Model\GetIPAssignment200Response
```

Get current IP assignment

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\IpPoolsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getIPAssignment();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IpPoolsApi->getIPAssignment: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\GetIPAssignment200Response**](../Model/GetIPAssignment200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listDedicatedIPRequests()`

```php
listDedicatedIPRequests(): \Lockally\SDK\Model\ListDedicatedIPRequests200Response
```

List dedicated IP requests

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\IpPoolsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listDedicatedIPRequests();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling IpPoolsApi->listDedicatedIPRequests: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\ListDedicatedIPRequests200Response**](../Model/ListDedicatedIPRequests200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
