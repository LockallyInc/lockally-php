# Lockally\SDK\MigrationsApi

Email migration from external providers (IMAP, Google, Microsoft)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**cancelMigration()**](MigrationsApi.md#cancelMigration) | **POST** /v1/migrations/{id}/cancel | Cancel a running migration |
| [**checkMigrationDNS()**](MigrationsApi.md#checkMigrationDNS) | **GET** /v1/migrations/{id}/dns-check | Check DNS readiness for cutover |
| [**createMigration()**](MigrationsApi.md#createMigration) | **POST** /v1/migrations | Create a migration |
| [**createMigrationCredential()**](MigrationsApi.md#createMigrationCredential) | **POST** /v1/migrations/credentials | Store a migration credential |
| [**deleteMigration()**](MigrationsApi.md#deleteMigration) | **DELETE** /v1/migrations/{id} | Delete a migration |
| [**deleteMigrationCredential()**](MigrationsApi.md#deleteMigrationCredential) | **DELETE** /v1/migrations/credentials/{id} | Delete a migration credential |
| [**deltaSyncMigration()**](MigrationsApi.md#deltaSyncMigration) | **POST** /v1/migrations/{id}/delta-sync | Run a delta sync |
| [**discoverMigration()**](MigrationsApi.md#discoverMigration) | **POST** /v1/migrations/{id}/discover | Discover source mailboxes |
| [**finalSyncMigration()**](MigrationsApi.md#finalSyncMigration) | **POST** /v1/migrations/{id}/final-sync | Run the final sync before cutover |
| [**getMigration()**](MigrationsApi.md#getMigration) | **GET** /v1/migrations/{id} | Get a migration |
| [**getMigrationProgress()**](MigrationsApi.md#getMigrationProgress) | **GET** /v1/migrations/{id}/progress | Get migration progress |
| [**listMigrationCredentials()**](MigrationsApi.md#listMigrationCredentials) | **GET** /v1/migrations/credentials | List migration credentials |
| [**listMigrationEvents()**](MigrationsApi.md#listMigrationEvents) | **GET** /v1/migrations/{id}/events | List migration events |
| [**listMigrationMailboxes()**](MigrationsApi.md#listMigrationMailboxes) | **GET** /v1/migrations/{id}/mailboxes | List migration mailboxes |
| [**listMigrations()**](MigrationsApi.md#listMigrations) | **GET** /v1/migrations | List migrations |
| [**mapMigration()**](MigrationsApi.md#mapMigration) | **POST** /v1/migrations/{id}/map | Map source to destination mailboxes |
| [**retryMigration()**](MigrationsApi.md#retryMigration) | **POST** /v1/migrations/{id}/retry | Retry a failed or cancelled migration |
| [**startMigration()**](MigrationsApi.md#startMigration) | **POST** /v1/migrations/{id}/start | Start the migration |
| [**updateMigration()**](MigrationsApi.md#updateMigration) | **PATCH** /v1/migrations/{id} | Update a migration |
| [**updateMigrationMailbox()**](MigrationsApi.md#updateMigrationMailbox) | **PATCH** /v1/migrations/{id}/mailboxes/{mbxId} | Update a migration mailbox |
| [**validateMigration()**](MigrationsApi.md#validateMigration) | **POST** /v1/migrations/{id}/validate | Validate migrated data |


## `cancelMigration()`

```php
cancelMigration($id): \Lockally\SDK\Model\DiscoverMigration202Response
```

Cancel a running migration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->cancelMigration($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->cancelMigration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\DiscoverMigration202Response**](../Model/DiscoverMigration202Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `checkMigrationDNS()`

```php
checkMigrationDNS($id): object
```

Check DNS readiness for cutover

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->checkMigrationDNS($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->checkMigrationDNS: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

**object**

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createMigration()`

```php
createMigration($create_migration_request): \Lockally\SDK\Model\Migration
```

Create a migration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_migration_request = new \Lockally\SDK\Model\CreateMigrationRequest(); // \Lockally\SDK\Model\CreateMigrationRequest

try {
    $result = $apiInstance->createMigration($create_migration_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->createMigration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_migration_request** | [**\Lockally\SDK\Model\CreateMigrationRequest**](../Model/CreateMigrationRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Migration**](../Model/Migration.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createMigrationCredential()`

```php
createMigrationCredential($create_migration_credential_request): \Lockally\SDK\Model\MigrationCredential
```

Store a migration credential

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_migration_credential_request = new \Lockally\SDK\Model\CreateMigrationCredentialRequest(); // \Lockally\SDK\Model\CreateMigrationCredentialRequest

try {
    $result = $apiInstance->createMigrationCredential($create_migration_credential_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->createMigrationCredential: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_migration_credential_request** | [**\Lockally\SDK\Model\CreateMigrationCredentialRequest**](../Model/CreateMigrationCredentialRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\MigrationCredential**](../Model/MigrationCredential.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteMigration()`

```php
deleteMigration($id)
```

Delete a migration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->deleteMigration($id);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->deleteMigration: ', $e->getMessage(), PHP_EOL;
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

## `deleteMigrationCredential()`

```php
deleteMigrationCredential($id)
```

Delete a migration credential

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->deleteMigrationCredential($id);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->deleteMigrationCredential: ', $e->getMessage(), PHP_EOL;
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

## `deltaSyncMigration()`

```php
deltaSyncMigration($id): \Lockally\SDK\Model\StartMigration202Response
```

Run a delta sync

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->deltaSyncMigration($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->deltaSyncMigration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\StartMigration202Response**](../Model/StartMigration202Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `discoverMigration()`

```php
discoverMigration($id): \Lockally\SDK\Model\DiscoverMigration202Response
```

Discover source mailboxes

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->discoverMigration($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->discoverMigration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\DiscoverMigration202Response**](../Model/DiscoverMigration202Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `finalSyncMigration()`

```php
finalSyncMigration($id): \Lockally\SDK\Model\StartMigration202Response
```

Run the final sync before cutover

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->finalSyncMigration($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->finalSyncMigration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\StartMigration202Response**](../Model/StartMigration202Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getMigration()`

```php
getMigration($id): \Lockally\SDK\Model\Migration
```

Get a migration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->getMigration($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->getMigration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Migration**](../Model/Migration.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getMigrationProgress()`

```php
getMigrationProgress($id): \Lockally\SDK\Model\MigrationProgress
```

Get migration progress

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->getMigrationProgress($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->getMigrationProgress: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\MigrationProgress**](../Model/MigrationProgress.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listMigrationCredentials()`

```php
listMigrationCredentials(): \Lockally\SDK\Model\ListMigrationCredentials200Response
```

List migration credentials

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listMigrationCredentials();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->listMigrationCredentials: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\ListMigrationCredentials200Response**](../Model/ListMigrationCredentials200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listMigrationEvents()`

```php
listMigrationEvents($id): \Lockally\SDK\Model\ListMigrationEvents200Response
```

List migration events

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->listMigrationEvents($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->listMigrationEvents: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\ListMigrationEvents200Response**](../Model/ListMigrationEvents200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listMigrationMailboxes()`

```php
listMigrationMailboxes($id): \Lockally\SDK\Model\ListMigrationMailboxes200Response
```

List migration mailboxes

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->listMigrationMailboxes($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->listMigrationMailboxes: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\ListMigrationMailboxes200Response**](../Model/ListMigrationMailboxes200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listMigrations()`

```php
listMigrations(): \Lockally\SDK\Model\ListMigrations200Response
```

List migrations

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listMigrations();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->listMigrations: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\ListMigrations200Response**](../Model/ListMigrations200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `mapMigration()`

```php
mapMigration($id, $map_migration_request): \Lockally\SDK\Model\DiscoverMigration202Response
```

Map source to destination mailboxes

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$map_migration_request = new \Lockally\SDK\Model\MapMigrationRequest(); // \Lockally\SDK\Model\MapMigrationRequest

try {
    $result = $apiInstance->mapMigration($id, $map_migration_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->mapMigration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **map_migration_request** | [**\Lockally\SDK\Model\MapMigrationRequest**](../Model/MapMigrationRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\DiscoverMigration202Response**](../Model/DiscoverMigration202Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `retryMigration()`

```php
retryMigration($id): \Lockally\SDK\Model\DiscoverMigration202Response
```

Retry a failed or cancelled migration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->retryMigration($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->retryMigration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\DiscoverMigration202Response**](../Model/DiscoverMigration202Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `startMigration()`

```php
startMigration($id): \Lockally\SDK\Model\StartMigration202Response
```

Start the migration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->startMigration($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->startMigration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\StartMigration202Response**](../Model/StartMigration202Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateMigration()`

```php
updateMigration($id, $update_migration_request): \Lockally\SDK\Model\Migration
```

Update a migration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$update_migration_request = new \Lockally\SDK\Model\UpdateMigrationRequest(); // \Lockally\SDK\Model\UpdateMigrationRequest

try {
    $result = $apiInstance->updateMigration($id, $update_migration_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->updateMigration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_migration_request** | [**\Lockally\SDK\Model\UpdateMigrationRequest**](../Model/UpdateMigrationRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Migration**](../Model/Migration.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateMigrationMailbox()`

```php
updateMigrationMailbox($id, $mbx_id, $update_migration_mailbox_request)
```

Update a migration mailbox

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$mbx_id = 'mbx_id_example'; // string
$update_migration_mailbox_request = new \Lockally\SDK\Model\UpdateMigrationMailboxRequest(); // \Lockally\SDK\Model\UpdateMigrationMailboxRequest

try {
    $apiInstance->updateMigrationMailbox($id, $mbx_id, $update_migration_mailbox_request);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->updateMigrationMailbox: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **mbx_id** | **string**|  | |
| **update_migration_mailbox_request** | [**\Lockally\SDK\Model\UpdateMigrationMailboxRequest**](../Model/UpdateMigrationMailboxRequest.md)|  | |

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

## `validateMigration()`

```php
validateMigration($id): \Lockally\SDK\Model\StartMigration202Response
```

Validate migrated data

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MigrationsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->validateMigration($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MigrationsApi->validateMigration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\StartMigration202Response**](../Model/StartMigration202Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
