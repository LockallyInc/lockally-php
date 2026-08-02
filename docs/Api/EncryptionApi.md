# Lockally\SDK\EncryptionApi

End-to-end encryption key management

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**batchLookupPublicKeys()**](EncryptionApi.md#batchLookupPublicKeys) | **GET** /v1/encryption/keys/lookup | Batch-lookup public keys by email |
| [**createEncryptionKey()**](EncryptionApi.md#createEncryptionKey) | **POST** /v1/encryption/keys | Upload an encryption key pair |
| [**createEncryptionRecovery()**](EncryptionApi.md#createEncryptionRecovery) | **POST** /v1/encryption/recovery | Store an encryption recovery blob |
| [**getEncryptionKey()**](EncryptionApi.md#getEncryptionKey) | **GET** /v1/encryption/keys/{email} | Get encryption key for a mailbox |
| [**rotateEncryptionKey()**](EncryptionApi.md#rotateEncryptionKey) | **POST** /v1/encryption/keys/rotate | Rotate an encryption key |


## `batchLookupPublicKeys()`

```php
batchLookupPublicKeys($emails): \Lockally\SDK\Model\BatchLookupPublicKeys200Response
```

Batch-lookup public keys by email

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\EncryptionApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$emails = 'emails_example'; // string | Comma-separated list of email addresses

try {
    $result = $apiInstance->batchLookupPublicKeys($emails);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EncryptionApi->batchLookupPublicKeys: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **emails** | **string**| Comma-separated list of email addresses | |

### Return type

[**\Lockally\SDK\Model\BatchLookupPublicKeys200Response**](../Model/BatchLookupPublicKeys200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createEncryptionKey()`

```php
createEncryptionKey($create_encryption_key_request): \Lockally\SDK\Model\CreateEncryptionKey201Response
```

Upload an encryption key pair

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\EncryptionApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_encryption_key_request = new \Lockally\SDK\Model\CreateEncryptionKeyRequest(); // \Lockally\SDK\Model\CreateEncryptionKeyRequest

try {
    $result = $apiInstance->createEncryptionKey($create_encryption_key_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EncryptionApi->createEncryptionKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_encryption_key_request** | [**\Lockally\SDK\Model\CreateEncryptionKeyRequest**](../Model/CreateEncryptionKeyRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\CreateEncryptionKey201Response**](../Model/CreateEncryptionKey201Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createEncryptionRecovery()`

```php
createEncryptionRecovery($create_encryption_recovery_request)
```

Store an encryption recovery blob

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\EncryptionApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_encryption_recovery_request = new \Lockally\SDK\Model\CreateEncryptionRecoveryRequest(); // \Lockally\SDK\Model\CreateEncryptionRecoveryRequest

try {
    $apiInstance->createEncryptionRecovery($create_encryption_recovery_request);
} catch (Exception $e) {
    echo 'Exception when calling EncryptionApi->createEncryptionRecovery: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_encryption_recovery_request** | [**\Lockally\SDK\Model\CreateEncryptionRecoveryRequest**](../Model/CreateEncryptionRecoveryRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getEncryptionKey()`

```php
getEncryptionKey($email): \Lockally\SDK\Model\GetEncryptionKey200Response
```

Get encryption key for a mailbox

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\EncryptionApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email = 'email_example'; // string

try {
    $result = $apiInstance->getEncryptionKey($email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling EncryptionApi->getEncryptionKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\GetEncryptionKey200Response**](../Model/GetEncryptionKey200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `rotateEncryptionKey()`

```php
rotateEncryptionKey($rotate_encryption_key_request)
```

Rotate an encryption key

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\EncryptionApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$rotate_encryption_key_request = new \Lockally\SDK\Model\RotateEncryptionKeyRequest(); // \Lockally\SDK\Model\RotateEncryptionKeyRequest

try {
    $apiInstance->rotateEncryptionKey($rotate_encryption_key_request);
} catch (Exception $e) {
    echo 'Exception when calling EncryptionApi->rotateEncryptionKey: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **rotate_encryption_key_request** | [**\Lockally\SDK\Model\RotateEncryptionKeyRequest**](../Model/RotateEncryptionKeyRequest.md)|  | |

### Return type

void (empty response body)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
