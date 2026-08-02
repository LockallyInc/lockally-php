# Lockally\SDK\AliasesApi

Email aliases (forwarders) on verified tenant domains

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**v1AliasesAddressDelete()**](AliasesApi.md#v1AliasesAddressDelete) | **DELETE** /v1/aliases/{address} | Delete an alias |
| [**v1AliasesGet()**](AliasesApi.md#v1AliasesGet) | **GET** /v1/aliases | List aliases |
| [**v1AliasesPost()**](AliasesApi.md#v1AliasesPost) | **POST** /v1/aliases | Create an alias |


## `v1AliasesAddressDelete()`

```php
v1AliasesAddressDelete($address)
```

Delete an alias

Hard-delete (no soft-delete window — aliases are cheap to recreate).

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
    $apiInstance->v1AliasesAddressDelete($address);
} catch (Exception $e) {
    echo 'Exception when calling AliasesApi->v1AliasesAddressDelete: ', $e->getMessage(), PHP_EOL;
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

## `v1AliasesGet()`

```php
v1AliasesGet(): \Lockally\SDK\Model\V1AliasesGet200Response
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
    $result = $apiInstance->v1AliasesGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AliasesApi->v1AliasesGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\V1AliasesGet200Response**](../Model/V1AliasesGet200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1AliasesPost()`

```php
v1AliasesPost($v1_aliases_post_request): \Lockally\SDK\Model\Alias
```

Create an alias

Creates an email alias. `alias_address` must be on a verified tenant-owned domain. `alias_target` can be any email — intra-tenant or external (forwarding to a Gmail account is a legitimate use).

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
$v1_aliases_post_request = new \Lockally\SDK\Model\V1AliasesPostRequest(); // \Lockally\SDK\Model\V1AliasesPostRequest

try {
    $result = $apiInstance->v1AliasesPost($v1_aliases_post_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AliasesApi->v1AliasesPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **v1_aliases_post_request** | [**\Lockally\SDK\Model\V1AliasesPostRequest**](../Model/V1AliasesPostRequest.md)|  | |

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
