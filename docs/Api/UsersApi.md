# Lockally\SDK\UsersApi

End-user (mailbox user) lifecycle

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createUser()**](UsersApi.md#createUser) | **POST** /v1/users | Create a user |
| [**deleteUser()**](UsersApi.md#deleteUser) | **DELETE** /v1/users/{id} | Delete a user |
| [**getUser()**](UsersApi.md#getUser) | **GET** /v1/users/{id} | Get a user |
| [**listUsers()**](UsersApi.md#listUsers) | **GET** /v1/users | List users |
| [**updateUser()**](UsersApi.md#updateUser) | **PATCH** /v1/users/{id} | Update a user |


## `createUser()`

```php
createUser($create_user_request): \Lockally\SDK\Model\User
```

Create a user

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_user_request = new \Lockally\SDK\Model\CreateUserRequest(); // \Lockally\SDK\Model\CreateUserRequest

try {
    $result = $apiInstance->createUser($create_user_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->createUser: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_user_request** | [**\Lockally\SDK\Model\CreateUserRequest**](../Model/CreateUserRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\User**](../Model/User.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteUser()`

```php
deleteUser($id)
```

Delete a user

Soft-deletes the user by setting status to deprovisioned.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->deleteUser($id);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->deleteUser: ', $e->getMessage(), PHP_EOL;
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

## `getUser()`

```php
getUser($id): \Lockally\SDK\Model\User
```

Get a user

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->getUser($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->getUser: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\User**](../Model/User.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listUsers()`

```php
listUsers($limit): \Lockally\SDK\Model\ListUsers200Response
```

List users

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$limit = 100; // int

try {
    $result = $apiInstance->listUsers($limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->listUsers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **limit** | **int**|  | [optional] [default to 100] |

### Return type

[**\Lockally\SDK\Model\ListUsers200Response**](../Model/ListUsers200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateUser()`

```php
updateUser($id, $update_user_request): \Lockally\SDK\Model\User
```

Update a user

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\UsersApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$update_user_request = new \Lockally\SDK\Model\UpdateUserRequest(); // \Lockally\SDK\Model\UpdateUserRequest

try {
    $result = $apiInstance->updateUser($id, $update_user_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling UsersApi->updateUser: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_user_request** | [**\Lockally\SDK\Model\UpdateUserRequest**](../Model/UpdateUserRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\User**](../Model/User.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
