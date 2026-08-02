# Lockally\SDK\ApiKeysApi



All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**v1ApiKeysGet()**](ApiKeysApi.md#v1ApiKeysGet) | **GET** /v1/api-keys | List API keys |
| [**v1ApiKeysIdDelete()**](ApiKeysApi.md#v1ApiKeysIdDelete) | **DELETE** /v1/api-keys/{id} | Revoke an API key |
| [**v1ApiKeysPost()**](ApiKeysApi.md#v1ApiKeysPost) | **POST** /v1/api-keys | Create an API key |


## `v1ApiKeysGet()`

```php
v1ApiKeysGet(): \Lockally\SDK\Model\V1ApiKeysGet200Response
```

List API keys

Returns all API keys (active and revoked) belonging to the calling tenant. The `secret` is **never** returned — only prefix + metadata.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ApiKeysApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->v1ApiKeysGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ApiKeysApi->v1ApiKeysGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\V1ApiKeysGet200Response**](../Model/V1ApiKeysGet200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1ApiKeysIdDelete()`

```php
v1ApiKeysIdDelete($id)
```

Revoke an API key

Soft-deletes (sets `revoked_at`) on the named key. The row stays for audit purposes; the key no longer authenticates.  You **cannot revoke the key currently being used** to make this call — that would lock you out. Use a different `tenant:admin` key.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ApiKeysApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->v1ApiKeysIdDelete($id);
} catch (Exception $e) {
    echo 'Exception when calling ApiKeysApi->v1ApiKeysIdDelete: ', $e->getMessage(), PHP_EOL;
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

## `v1ApiKeysPost()`

```php
v1ApiKeysPost($v1_api_keys_post_request): \Lockally\SDK\Model\V1ApiKeysPost201Response
```

Create an API key

Provisions a fresh API key for the calling tenant.  **The full `secret` is included in this response ONLY** — store it immediately. The cleartext secret is not recoverable from the argon2id hash kept server-side; rotate by creating a new key and revoking the old one.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ApiKeysApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$v1_api_keys_post_request = new \Lockally\SDK\Model\V1ApiKeysPostRequest(); // \Lockally\SDK\Model\V1ApiKeysPostRequest

try {
    $result = $apiInstance->v1ApiKeysPost($v1_api_keys_post_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ApiKeysApi->v1ApiKeysPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **v1_api_keys_post_request** | [**\Lockally\SDK\Model\V1ApiKeysPostRequest**](../Model/V1ApiKeysPostRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\V1ApiKeysPost201Response**](../Model/V1ApiKeysPost201Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
