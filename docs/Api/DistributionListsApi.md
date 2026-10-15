# Lockally\SDK\DistributionListsApi



All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createDistributionList()**](DistributionListsApi.md#createDistributionList) | **POST** /v1/distribution-lists | Create a distribution list |
| [**deleteDistributionList()**](DistributionListsApi.md#deleteDistributionList) | **DELETE** /v1/distribution-lists/{address} | Delete a distribution list |
| [**getDistributionList()**](DistributionListsApi.md#getDistributionList) | **GET** /v1/distribution-lists/{address} | Get a distribution list |
| [**listDistributionLists()**](DistributionListsApi.md#listDistributionLists) | **GET** /v1/distribution-lists | List distribution lists |
| [**replaceDistributionListMembers()**](DistributionListsApi.md#replaceDistributionListMembers) | **PUT** /v1/distribution-lists/{address}/members | Replace distribution list members |


## `createDistributionList()`

```php
createDistributionList($create_distribution_list_request): \Lockally\SDK\Model\DistributionListDetail
```

Create a distribution list

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DistributionListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_distribution_list_request = new \Lockally\SDK\Model\CreateDistributionListRequest(); // \Lockally\SDK\Model\CreateDistributionListRequest

try {
    $result = $apiInstance->createDistributionList($create_distribution_list_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DistributionListsApi->createDistributionList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_distribution_list_request** | [**\Lockally\SDK\Model\CreateDistributionListRequest**](../Model/CreateDistributionListRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\DistributionListDetail**](../Model/DistributionListDetail.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteDistributionList()`

```php
deleteDistributionList($address)
```

Delete a distribution list

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DistributionListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address = 'address_example'; // string | Distribution list email address

try {
    $apiInstance->deleteDistributionList($address);
} catch (Exception $e) {
    echo 'Exception when calling DistributionListsApi->deleteDistributionList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address** | **string**| Distribution list email address | |

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

## `getDistributionList()`

```php
getDistributionList($address): \Lockally\SDK\Model\DistributionListDetail
```

Get a distribution list

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DistributionListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address = 'address_example'; // string | Distribution list email address

try {
    $result = $apiInstance->getDistributionList($address);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DistributionListsApi->getDistributionList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address** | **string**| Distribution list email address | |

### Return type

[**\Lockally\SDK\Model\DistributionListDetail**](../Model/DistributionListDetail.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listDistributionLists()`

```php
listDistributionLists(): \Lockally\SDK\Model\ListDistributionLists200Response
```

List distribution lists

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DistributionListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listDistributionLists();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DistributionListsApi->listDistributionLists: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\ListDistributionLists200Response**](../Model/ListDistributionLists200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `replaceDistributionListMembers()`

```php
replaceDistributionListMembers($address, $replace_distribution_list_members_request): \Lockally\SDK\Model\ReplaceDistributionListMembers200Response
```

Replace distribution list members

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DistributionListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address = 'address_example'; // string | Distribution list email address
$replace_distribution_list_members_request = new \Lockally\SDK\Model\ReplaceDistributionListMembersRequest(); // \Lockally\SDK\Model\ReplaceDistributionListMembersRequest

try {
    $result = $apiInstance->replaceDistributionListMembers($address, $replace_distribution_list_members_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DistributionListsApi->replaceDistributionListMembers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address** | **string**| Distribution list email address | |
| **replace_distribution_list_members_request** | [**\Lockally\SDK\Model\ReplaceDistributionListMembersRequest**](../Model/ReplaceDistributionListMembersRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\ReplaceDistributionListMembers200Response**](../Model/ReplaceDistributionListMembers200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
