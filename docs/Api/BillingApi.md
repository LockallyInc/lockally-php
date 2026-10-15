# Lockally\SDK\BillingApi

Plan, subscription checkout, and send-unit purchases

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createBillingCheckout()**](BillingApi.md#createBillingCheckout) | **POST** /v1/billing/checkout | Create a plan checkout session |
| [**createUnitsCheckout()**](BillingApi.md#createUnitsCheckout) | **POST** /v1/billing/units/checkout | Create a send-units checkout session |
| [**getBilling()**](BillingApi.md#getBilling) | **GET** /v1/billing | Get billing status |


## `createBillingCheckout()`

```php
createBillingCheckout($create_billing_checkout_request): \Lockally\SDK\Model\CreateBillingCheckout200Response
```

Create a plan checkout session

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_billing_checkout_request = new \Lockally\SDK\Model\CreateBillingCheckoutRequest(); // \Lockally\SDK\Model\CreateBillingCheckoutRequest

try {
    $result = $apiInstance->createBillingCheckout($create_billing_checkout_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->createBillingCheckout: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_billing_checkout_request** | [**\Lockally\SDK\Model\CreateBillingCheckoutRequest**](../Model/CreateBillingCheckoutRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\CreateBillingCheckout200Response**](../Model/CreateBillingCheckout200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createUnitsCheckout()`

```php
createUnitsCheckout($create_units_checkout_request): \Lockally\SDK\Model\CreateUnitsCheckout200Response
```

Create a send-units checkout session

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_units_checkout_request = new \Lockally\SDK\Model\CreateUnitsCheckoutRequest(); // \Lockally\SDK\Model\CreateUnitsCheckoutRequest

try {
    $result = $apiInstance->createUnitsCheckout($create_units_checkout_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->createUnitsCheckout: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_units_checkout_request** | [**\Lockally\SDK\Model\CreateUnitsCheckoutRequest**](../Model/CreateUnitsCheckoutRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\CreateUnitsCheckout200Response**](../Model/CreateUnitsCheckout200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getBilling()`

```php
getBilling(): \Lockally\SDK\Model\BillingStatus
```

Get billing status

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\BillingApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getBilling();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling BillingApi->getBilling: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\BillingStatus**](../Model/BillingStatus.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
