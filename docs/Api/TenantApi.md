# Lockally\SDK\TenantApi

Operations on the calling tenant

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**getTenant()**](TenantApi.md#getTenant) | **GET** /v1/tenant | Get the calling tenant |
| [**getTrackingPolicy()**](TenantApi.md#getTrackingPolicy) | **GET** /v1/tracking | Get the engagement tracking policy |
| [**getUsage()**](TenantApi.md#getUsage) | **GET** /v1/usage | Usage snapshot |
| [**updateTrackingPolicy()**](TenantApi.md#updateTrackingPolicy) | **PUT** /v1/tracking | Update the engagement tracking policy |


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

## `getTrackingPolicy()`

```php
getTrackingPolicy(): \Lockally\SDK\Model\TrackingPolicy
```

Get the engagement tracking policy

Whether open and click tracking are enabled for this account. **Both are off until switched on**, and an account that has never set a policy reads as off rather than as an error.  `configured` reports whether this deployment holds a signing secret. Without one no tracking token can be minted or verified, so tracking cannot work however the flags are set, and a caller seeing `track_opens: true` with nothing arriving deserves to know why.

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
    $result = $apiInstance->getTrackingPolicy();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TenantApi->getTrackingPolicy: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\TrackingPolicy**](../Model/TrackingPolicy.md)

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

Returns the tenant's current usage + cap consumption. Designed for poll-based alerting on the integrator side (e.g. \"warn when daily quota is 80% used\"). Computed live on request, so there is no cache, so callers should poll at most once per minute.

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

## `updateTrackingPolicy()`

```php
updateTrackingPolicy($update_tracking_policy_request): \Lockally\SDK\Model\TrackingPolicy
```

Update the engagement tracking policy

Enables or disables tracking for the account. Send either flag or both; an omitted flag is left unchanged rather than reset.  **Enabling this changes what Lockally collects about your recipients**, who have no relationship with us. You are the controller for them. What is collected is a user-agent string, a timestamp, and for a click the destination URL: **no IP address**, ever. The change is written to your audit log.

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
$update_tracking_policy_request = new \Lockally\SDK\Model\UpdateTrackingPolicyRequest(); // \Lockally\SDK\Model\UpdateTrackingPolicyRequest

try {
    $result = $apiInstance->updateTrackingPolicy($update_tracking_policy_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TenantApi->updateTrackingPolicy: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **update_tracking_policy_request** | [**\Lockally\SDK\Model\UpdateTrackingPolicyRequest**](../Model/UpdateTrackingPolicyRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\TrackingPolicy**](../Model/TrackingPolicy.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
