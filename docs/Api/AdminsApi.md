# Lockally\SDK\AdminsApi

Tenant-admin team management (invite, list, disable, delete)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**v1AdminsGet()**](AdminsApi.md#v1AdminsGet) | **GET** /v1/admins | List tenant admins |
| [**v1AdminsIdDelete()**](AdminsApi.md#v1AdminsIdDelete) | **DELETE** /v1/admins/{id} | Delete an admin |
| [**v1AdminsIdPatch()**](AdminsApi.md#v1AdminsIdPatch) | **PATCH** /v1/admins/{id} | Update an admin |
| [**v1AdminsPost()**](AdminsApi.md#v1AdminsPost) | **POST** /v1/admins | Invite a new admin |


## `v1AdminsGet()`

```php
v1AdminsGet(): \Lockally\SDK\Model\V1AdminsGet200Response
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
    $result = $apiInstance->v1AdminsGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AdminsApi->v1AdminsGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\V1AdminsGet200Response**](../Model/V1AdminsGet200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1AdminsIdDelete()`

```php
v1AdminsIdDelete($id)
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
    $apiInstance->v1AdminsIdDelete($id);
} catch (Exception $e) {
    echo 'Exception when calling AdminsApi->v1AdminsIdDelete: ', $e->getMessage(), PHP_EOL;
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

## `v1AdminsIdPatch()`

```php
v1AdminsIdPatch($id, $v1_admins_id_patch_request): \Lockally\SDK\Model\AdminFull
```

Update an admin

Supply at least one of `password`, `display_name`, `role`, `disabled`.  **Safety rails.** A session bearer (adm_sess_*) cannot disable itself — use another admin or an API key (which bypasses the self-rail). Disabling the last active admin returns 409 to prevent orphaning the tenant from its console.

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
$v1_admins_id_patch_request = new \Lockally\SDK\Model\V1AdminsIdPatchRequest(); // \Lockally\SDK\Model\V1AdminsIdPatchRequest

try {
    $result = $apiInstance->v1AdminsIdPatch($id, $v1_admins_id_patch_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AdminsApi->v1AdminsIdPatch: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **v1_admins_id_patch_request** | [**\Lockally\SDK\Model\V1AdminsIdPatchRequest**](../Model/V1AdminsIdPatchRequest.md)|  | |

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

## `v1AdminsPost()`

```php
v1AdminsPost($v1_admins_post_request): \Lockally\SDK\Model\AdminFull
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
$v1_admins_post_request = new \Lockally\SDK\Model\V1AdminsPostRequest(); // \Lockally\SDK\Model\V1AdminsPostRequest

try {
    $result = $apiInstance->v1AdminsPost($v1_admins_post_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AdminsApi->v1AdminsPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **v1_admins_post_request** | [**\Lockally\SDK\Model\V1AdminsPostRequest**](../Model/V1AdminsPostRequest.md)|  | |

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
