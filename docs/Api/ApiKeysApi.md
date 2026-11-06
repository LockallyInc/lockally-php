# Lockally\SDK\ApiKeysApi



All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createApiKey()**](ApiKeysApi.md#createApiKey) | **POST** /v1/api-keys | Create an API key |
| [**listApiKeys()**](ApiKeysApi.md#listApiKeys) | **GET** /v1/api-keys | List API keys |
| [**revokeApiKey()**](ApiKeysApi.md#revokeApiKey) | **DELETE** /v1/api-keys/{id} | Revoke an API key |
| [**rotateApiKey()**](ApiKeysApi.md#rotateApiKey) | **POST** /v1/api-keys/{id}/rotate | Rotate an API key |
| [**updateApiKey()**](ApiKeysApi.md#updateApiKey) | **PATCH** /v1/api-keys/{id} | Update an API key |


## `createApiKey()`

```php
createApiKey($create_api_key_request): \Lockally\SDK\Model\CreateApiKey201Response
```

Create an API key

Provisions a fresh API key for the calling tenant.  **The full `secret` is included in this response ONLY**, store it immediately. The cleartext secret is not recoverable from the argon2id hash kept server-side; rotate by creating a new key and revoking the old one.

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
$create_api_key_request = new \Lockally\SDK\Model\CreateApiKeyRequest(); // \Lockally\SDK\Model\CreateApiKeyRequest

try {
    $result = $apiInstance->createApiKey($create_api_key_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ApiKeysApi->createApiKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_api_key_request** | [**\Lockally\SDK\Model\CreateApiKeyRequest**](../Model/CreateApiKeyRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\CreateApiKey201Response**](../Model/CreateApiKey201Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listApiKeys()`

```php
listApiKeys($sort, $order): \Lockally\SDK\Model\ListApiKeys200Response
```

List API keys

Returns all API keys (active and revoked) belonging to the calling tenant. The `secret` is **never** returned, only prefix + metadata.

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
$sort = 'created_at'; // string | Field to order by. This list holds tens of rows per account, so every column is offered and none needs an index.
$order = 'order_example'; // string | Defaults to desc for the default field and asc for any other. Always tie-broken on id, so the order is total.

try {
    $result = $apiInstance->listApiKeys($sort, $order);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ApiKeysApi->listApiKeys: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **sort** | **string**| Field to order by. This list holds tens of rows per account, so every column is offered and none needs an index. | [optional] [default to &#39;created_at&#39;] |
| **order** | **string**| Defaults to desc for the default field and asc for any other. Always tie-broken on id, so the order is total. | [optional] |

### Return type

[**\Lockally\SDK\Model\ListApiKeys200Response**](../Model/ListApiKeys200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `revokeApiKey()`

```php
revokeApiKey($id)
```

Revoke an API key

Soft-deletes (sets `revoked_at`) on the named key. The row stays for audit purposes; the key no longer authenticates.  You **cannot revoke the key currently being used** to make this call, that would lock you out. Use a different `tenant:admin` key.

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
    $apiInstance->revokeApiKey($id);
} catch (Exception $e) {
    echo 'Exception when calling ApiKeysApi->revokeApiKey: ', $e->getMessage(), PHP_EOL;
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

## `rotateApiKey()`

```php
rotateApiKey($id, $rotate_api_key_request): \Lockally\SDK\Model\CreateApiKey201Response
```

Rotate an API key

Issues a successor key and puts a short expiry on this one, so **both work until the overlap ends**. That window is the point: without it, rotation is revocation with extra steps and every caller has to swap credentials in the same instant.  The successor inherits this key's scopes, its label (the label names the integration, and the integration has not changed) and its test flag. Its full `secret` is in this response and nowhere else.  The response's `expires_at` is the **predecessor's** deadline, so you can see from the rotation itself how long you have to cut over.  A key that has already been rotated cannot be rotated again: chaining overlaps would leave several live keys for one integration, which is the opposite of the intent. Rotate the successor instead.

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
$rotate_api_key_request = new \Lockally\SDK\Model\RotateApiKeyRequest(); // \Lockally\SDK\Model\RotateApiKeyRequest

try {
    $result = $apiInstance->rotateApiKey($id, $rotate_api_key_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ApiKeysApi->rotateApiKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **rotate_api_key_request** | [**\Lockally\SDK\Model\RotateApiKeyRequest**](../Model/RotateApiKeyRequest.md)|  | [optional] |

### Return type

[**\Lockally\SDK\Model\CreateApiKey201Response**](../Model/CreateApiKey201Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateApiKey()`

```php
updateApiKey($id, $update_api_key_request): \Lockally\SDK\Model\APIKey
```

Update an API key

Changes a key's label, scopes or expiry in place, without reissuing the secret.  **Every field is optional and absent means unchanged.** Renaming a key does not clear its expiry. For `expires_at` there are three distinct requests: omit the field to leave the expiry alone, send a timestamp to set one, and send an explicit `null` to remove one.  Scopes are replaced wholesale, not merged. This endpoint does not restrict which scopes you may grant, because `POST /v1/api-keys` never has either: a key with `tenant:admin` can already mint a key with any scope, so `tenant:admin` is root-equivalent for key management.  A revoked key cannot be updated.

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
$update_api_key_request = new \Lockally\SDK\Model\UpdateApiKeyRequest(); // \Lockally\SDK\Model\UpdateApiKeyRequest

try {
    $result = $apiInstance->updateApiKey($id, $update_api_key_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ApiKeysApi->updateApiKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_api_key_request** | [**\Lockally\SDK\Model\UpdateApiKeyRequest**](../Model/UpdateApiKeyRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\APIKey**](../Model/APIKey.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
