# Lockally\SDK\AdminApi

Tenant-admin login (email+password → session token for app.lockally.com)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**adminLogin()**](AdminApi.md#adminLogin) | **POST** /v1/admin/login | Tenant-admin email+password login |
| [**adminLogout()**](AdminApi.md#adminLogout) | **POST** /v1/admin/logout | Invalidate the current admin session |
| [**getCurrentAdmin()**](AdminApi.md#getCurrentAdmin) | **GET** /v1/admin/me | Get the current admin + tenant |


## `adminLogin()`

```php
adminLogin($admin_login_request): \Lockally\SDK\Model\AdminLogin200Response
```

Tenant-admin email+password login

Exchanges an admin's email + password for a session token. The web console at `app.lockally.com` posts this on form submission and stores the returned token in an httpOnly cookie.  **No enumeration leak.** Wrong-email and wrong-password both return the same 401 with title \"Invalid credentials\". The argon2id verify runs even on lookup miss (well, structurally, the lookup fails fast but the response shape is constant) so timing leaks are bounded.  Tokens are prefixed `adm_sess_` and valid for 7 days. Use as the `Authorization: Bearer` value on all subsequent calls.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new Lockally\SDK\Api\AdminApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$admin_login_request = new \Lockally\SDK\Model\AdminLoginRequest(); // \Lockally\SDK\Model\AdminLoginRequest

try {
    $result = $apiInstance->adminLogin($admin_login_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AdminApi->adminLogin: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **admin_login_request** | [**\Lockally\SDK\Model\AdminLoginRequest**](../Model/AdminLoginRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\AdminLogin200Response**](../Model/AdminLogin200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `adminLogout()`

```php
adminLogout()
```

Invalidate the current admin session

Deletes the session row from the database. Idempotent, calling logout on an already-invalid token returns 204 anyway.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AdminApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $apiInstance->adminLogout();
} catch (Exception $e) {
    echo 'Exception when calling AdminApi->adminLogout: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

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

## `getCurrentAdmin()`

```php
getCurrentAdmin(): \Lockally\SDK\Model\GetCurrentAdmin200Response
```

Get the current admin + tenant

Returns the admin profile + tenant for the session token presented in `Authorization: Bearer`. Used by the web console's layout load function to populate the sidebar.  Returns 403 if called with an API key (lk_live_*) bearer, admin context only exists for session tokens.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AdminApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getCurrentAdmin();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AdminApi->getCurrentAdmin: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\GetCurrentAdmin200Response**](../Model/GetCurrentAdmin200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
