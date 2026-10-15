# Lockally\SDK\TenantApi

Operations on the calling tenant

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**getTenant()**](TenantApi.md#getTenant) | **GET** /v1/tenant | Get the calling tenant |
| [**getUsage()**](TenantApi.md#getUsage) | **GET** /v1/usage | Usage snapshot |


## `getTenant()`

```php
getTenant(): \Lockally\SDK\Model\Tenant
```

Get the calling tenant

Returns the tenant the presented API key belongs to.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\TenantApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getTenant();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TenantApi->getTenant: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\Tenant**](../Model/Tenant.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getUsage()`

```php
getUsage(): \Lockally\SDK\Model\GetUsage200Response
```

Usage snapshot

Returns the tenant's current usage + cap consumption. Designed for poll-based alerting on the integrator side (e.g. \"warn when daily quota is 80% used\"). Refreshed live from Postgres — there is no cache, so callers should poll at most once per minute.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\TenantApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getUsage();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TenantApi->getUsage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\GetUsage200Response**](../Model/GetUsage200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
