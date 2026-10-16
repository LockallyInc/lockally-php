# Lockally\SDK\AdminsApi

Tenant-admin team management (invite, list, disable, delete)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**deleteAdmin()**](AdminsApi.md#deleteAdmin) | **DELETE** /v1/admins/{id} | Delete an admin |
| [**inviteAdmin()**](AdminsApi.md#inviteAdmin) | **POST** /v1/admins | Invite a new admin |
| [**listAdmins()**](AdminsApi.md#listAdmins) | **GET** /v1/admins | List tenant admins |
| [**updateAdmin()**](AdminsApi.md#updateAdmin) | **PATCH** /v1/admins/{id} | Update an admin |


## `deleteAdmin()`

```php
deleteAdmin($id)
```

Delete an admin

Hard-delete. Cascade-drops the admin's sessions (immediate revocation). Same safety rails as PATCH disabled=true.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AdminsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->deleteAdmin($id);
} catch (Exception $e) {
    echo 'Exception when calling AdminsApi->deleteAdmin: ', $e->getMessage(), PHP_EOL;
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

## `inviteAdmin()`

```php
inviteAdmin($invite_admin_request): \Lockally\SDK\Model\AdminFull
```

Invite a new admin

Creates a new tenant admin. If `password` is omitted, lockally generates a 16-char password and returns it ONCE in the response. Email is case-insensitive and unique per tenant.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AdminsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$invite_admin_request = new \Lockally\SDK\Model\InviteAdminRequest(); // \Lockally\SDK\Model\InviteAdminRequest

try {
    $result = $apiInstance->inviteAdmin($invite_admin_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AdminsApi->inviteAdmin: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **invite_admin_request** | [**\Lockally\SDK\Model\InviteAdminRequest**](../Model/InviteAdminRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\AdminFull**](../Model/AdminFull.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listAdmins()`

```php
listAdmins(): \Lockally\SDK\Model\ListAdmins200Response
```

List tenant admins

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AdminsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listAdmins();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AdminsApi->listAdmins: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\ListAdmins200Response**](../Model/ListAdmins200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateAdmin()`

```php
updateAdmin($id, $update_admin_request): \Lockally\SDK\Model\AdminFull
```

Update an admin

Supply at least one of `password`, `display_name`, `role`, `disabled`.  **Safety rails.** A session bearer (adm_sess_*) cannot disable itself, use another admin or an API key (which bypasses the self-rail). Disabling the last active admin returns 409 to prevent orphaning the tenant from its console.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AdminsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$update_admin_request = new \Lockally\SDK\Model\UpdateAdminRequest(); // \Lockally\SDK\Model\UpdateAdminRequest

try {
    $result = $apiInstance->updateAdmin($id, $update_admin_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AdminsApi->updateAdmin: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_admin_request** | [**\Lockally\SDK\Model\UpdateAdminRequest**](../Model/UpdateAdminRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\AdminFull**](../Model/AdminFull.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
