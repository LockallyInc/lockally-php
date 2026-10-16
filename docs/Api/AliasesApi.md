# Lockally\SDK\AliasesApi

Email aliases (forwarders) on verified tenant domains

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createAlias()**](AliasesApi.md#createAlias) | **POST** /v1/aliases | Create an alias |
| [**deleteAlias()**](AliasesApi.md#deleteAlias) | **DELETE** /v1/aliases/{address} | Delete an alias |
| [**listAliases()**](AliasesApi.md#listAliases) | **GET** /v1/aliases | List aliases |


## `createAlias()`

```php
createAlias($create_alias_request): \Lockally\SDK\Model\Alias
```

Create an alias

Creates an email alias. `alias_address` must be on a verified tenant-owned domain and must not be the address of an existing mailbox (live, suspended or deleted). `alias_target` must be an active mailbox in the same workspace; forwarding to an address Lockally does not host is not supported. The alias delivers as soon as the call returns.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AliasesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_alias_request = new \Lockally\SDK\Model\CreateAliasRequest(); // \Lockally\SDK\Model\CreateAliasRequest

try {
    $result = $apiInstance->createAlias($create_alias_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AliasesApi->createAlias: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_alias_request** | [**\Lockally\SDK\Model\CreateAliasRequest**](../Model/CreateAliasRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Alias**](../Model/Alias.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteAlias()`

```php
deleteAlias($address)
```

Delete an alias

Hard-delete (no soft-delete window, aliases are cheap to recreate).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AliasesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$address = 'address_example'; // string

try {
    $apiInstance->deleteAlias($address);
} catch (Exception $e) {
    echo 'Exception when calling AliasesApi->deleteAlias: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **address** | **string**|  | |

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

## `listAliases()`

```php
listAliases(): \Lockally\SDK\Model\ListAliases200Response
```

List aliases

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AliasesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listAliases();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AliasesApi->listAliases: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\ListAliases200Response**](../Model/ListAliases200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
