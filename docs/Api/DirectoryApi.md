# Lockally\SDK\DirectoryApi

Global address list (GAL), directory permissions, stats

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**getDirectoryActivity()**](DirectoryApi.md#getDirectoryActivity) | **GET** /v1/directory-activity | Get recent directory activity |
| [**getDirectoryPermissions()**](DirectoryApi.md#getDirectoryPermissions) | **GET** /v1/directory-permissions | Get directory permission settings |
| [**getDirectoryStats()**](DirectoryApi.md#getDirectoryStats) | **GET** /v1/directory-stats | Get directory statistics |
| [**getGALSettings()**](DirectoryApi.md#getGALSettings) | **GET** /v1/gal-settings | Get Global Address List settings |
| [**rebuildGALIndex()**](DirectoryApi.md#rebuildGALIndex) | **POST** /v1/gal-settings/rebuild-index | Rebuild the GAL search index |
| [**syncGAL()**](DirectoryApi.md#syncGAL) | **POST** /v1/gal-settings/sync | Sync GAL with external directory sources |
| [**updateDirectoryPermissions()**](DirectoryApi.md#updateDirectoryPermissions) | **PATCH** /v1/directory-permissions | Update directory permission settings |
| [**updateGALSettings()**](DirectoryApi.md#updateGALSettings) | **PATCH** /v1/gal-settings | Update GAL settings |


## `getDirectoryActivity()`

```php
getDirectoryActivity(): \Lockally\SDK\Model\GetDirectoryActivity200Response
```

Get recent directory activity

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DirectoryApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getDirectoryActivity();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DirectoryApi->getDirectoryActivity: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\GetDirectoryActivity200Response**](../Model/GetDirectoryActivity200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getDirectoryPermissions()`

```php
getDirectoryPermissions(): \Lockally\SDK\Model\DirectoryPermissions
```

Get directory permission settings

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DirectoryApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getDirectoryPermissions();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DirectoryApi->getDirectoryPermissions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\DirectoryPermissions**](../Model/DirectoryPermissions.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getDirectoryStats()`

```php
getDirectoryStats(): \Lockally\SDK\Model\GetDirectoryStats200Response
```

Get directory statistics

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DirectoryApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getDirectoryStats();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DirectoryApi->getDirectoryStats: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\GetDirectoryStats200Response**](../Model/GetDirectoryStats200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getGALSettings()`

```php
getGALSettings(): \Lockally\SDK\Model\GALSettings
```

Get Global Address List settings

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DirectoryApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getGALSettings();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DirectoryApi->getGALSettings: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\GALSettings**](../Model/GALSettings.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `rebuildGALIndex()`

```php
rebuildGALIndex(): \Lockally\SDK\Model\GALSettings
```

Rebuild the GAL search index

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DirectoryApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->rebuildGALIndex();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DirectoryApi->rebuildGALIndex: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\GALSettings**](../Model/GALSettings.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `syncGAL()`

```php
syncGAL(): \Lockally\SDK\Model\GALSettings
```

Sync GAL with external directory sources

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DirectoryApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->syncGAL();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DirectoryApi->syncGAL: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\GALSettings**](../Model/GALSettings.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateDirectoryPermissions()`

```php
updateDirectoryPermissions($update_directory_permissions_request): \Lockally\SDK\Model\DirectoryPermissions
```

Update directory permission settings

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DirectoryApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$update_directory_permissions_request = new \Lockally\SDK\Model\UpdateDirectoryPermissionsRequest(); // \Lockally\SDK\Model\UpdateDirectoryPermissionsRequest

try {
    $result = $apiInstance->updateDirectoryPermissions($update_directory_permissions_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DirectoryApi->updateDirectoryPermissions: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **update_directory_permissions_request** | [**\Lockally\SDK\Model\UpdateDirectoryPermissionsRequest**](../Model/UpdateDirectoryPermissionsRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\DirectoryPermissions**](../Model/DirectoryPermissions.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateGALSettings()`

```php
updateGALSettings($update_gal_settings_request): \Lockally\SDK\Model\GALSettings
```

Update GAL settings

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DirectoryApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$update_gal_settings_request = new \Lockally\SDK\Model\UpdateGALSettingsRequest(); // \Lockally\SDK\Model\UpdateGALSettingsRequest

try {
    $result = $apiInstance->updateGALSettings($update_gal_settings_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DirectoryApi->updateGALSettings: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **update_gal_settings_request** | [**\Lockally\SDK\Model\UpdateGALSettingsRequest**](../Model/UpdateGALSettingsRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\GALSettings**](../Model/GALSettings.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
