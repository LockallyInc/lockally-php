# Lockally\SDK\AdminApi

Tenant-admin login (email+password → session token for app.lockally.com)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**v1AdminLoginPost()**](AdminApi.md#v1AdminLoginPost) | **POST** /v1/admin/login | Tenant-admin email+password login |
| [**v1AdminLogoutPost()**](AdminApi.md#v1AdminLogoutPost) | **POST** /v1/admin/logout | Invalidate the current admin session |
| [**v1AdminMeGet()**](AdminApi.md#v1AdminMeGet) | **GET** /v1/admin/me | Get the current admin + tenant |


## `v1AdminLoginPost()`

```php
v1AdminLoginPost($v1_admin_login_post_request): \Lockally\SDK\Model\V1AdminLoginPost200Response
```

Tenant-admin email+password login

Exchanges an admin's email + password for a session token. The web console at `app.lockally.com` posts this on form submission and stores the returned token in an httpOnly cookie.  **No enumeration leak.** Wrong-email and wrong-password both return the same 401 with title \"Invalid credentials\". The argon2id verify runs even on lookup miss (well, structurally — the lookup fails fast but the response shape is constant) so timing leaks are bounded.  Tokens are prefixed `adm_sess_` and valid for 7 days. Use as the `Authorization: Bearer` value on all subsequent calls.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new Lockally\SDK\Api\AdminApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$v1_admin_login_post_request = new \Lockally\SDK\Model\V1AdminLoginPostRequest(); // \Lockally\SDK\Model\V1AdminLoginPostRequest

try {
    $result = $apiInstance->v1AdminLoginPost($v1_admin_login_post_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AdminApi->v1AdminLoginPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **v1_admin_login_post_request** | [**\Lockally\SDK\Model\V1AdminLoginPostRequest**](../Model/V1AdminLoginPostRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\V1AdminLoginPost200Response**](../Model/V1AdminLoginPost200Response.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1AdminLogoutPost()`

```php
v1AdminLogoutPost()
```

Invalidate the current admin session

Deletes the session row from the database. Idempotent — calling logout on an already-invalid token returns 204 anyway.

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
    $apiInstance->v1AdminLogoutPost();
} catch (Exception $e) {
    echo 'Exception when calling AdminApi->v1AdminLogoutPost: ', $e->getMessage(), PHP_EOL;
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

## `v1AdminMeGet()`

```php
v1AdminMeGet(): \Lockally\SDK\Model\V1AdminMeGet200Response
```

Get the current admin + tenant

Returns the admin profile + tenant for the session token presented in `Authorization: Bearer`. Used by the web console's layout load function to populate the sidebar.  Returns 403 if called with an API key (lk_live_*) bearer — admin context only exists for session tokens.

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
    $result = $apiInstance->v1AdminMeGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AdminApi->v1AdminMeGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\V1AdminMeGet200Response**](../Model/V1AdminMeGet200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
