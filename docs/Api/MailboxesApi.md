# Lockally\SDK\MailboxesApi

Mailboxes on verified tenant domains

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**addSharedMember()**](MailboxesApi.md#addSharedMember) | **POST** /v1/mailboxes/{email}/members | Add a shared mailbox member |
| [**createMailbox()**](MailboxesApi.md#createMailbox) | **POST** /v1/mailboxes | Create a mailbox |
| [**deleteMailbox()**](MailboxesApi.md#deleteMailbox) | **DELETE** /v1/mailboxes/{email} | Soft-delete a mailbox |
| [**downloadMailboxExport()**](MailboxesApi.md#downloadMailboxExport) | **GET** /v1/mailboxes/{email}/export/download | Download a previously-issued mailbox export |
| [**exportMailbox()**](MailboxesApi.md#exportMailbox) | **POST** /v1/mailboxes/{email}/export | Request a mailbox export |
| [**getMailbox()**](MailboxesApi.md#getMailbox) | **GET** /v1/mailboxes/{email} | Get a mailbox |
| [**listMailboxes()**](MailboxesApi.md#listMailboxes) | **GET** /v1/mailboxes | List mailboxes |
| [**listSharedMembers()**](MailboxesApi.md#listSharedMembers) | **GET** /v1/mailboxes/{email}/members | List shared mailbox members |
| [**removeSharedMember()**](MailboxesApi.md#removeSharedMember) | **DELETE** /v1/mailboxes/{email}/members/{memberEmail} | Remove a shared mailbox member |
| [**updateMailbox()**](MailboxesApi.md#updateMailbox) | **PATCH** /v1/mailboxes/{email} | Update a mailbox |


## `addSharedMember()`

```php
addSharedMember($email, $add_shared_member_request): \Lockally\SDK\Model\SharedMember
```

Add a shared mailbox member

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MailboxesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email = 'email_example'; // string
$add_shared_member_request = new \Lockally\SDK\Model\AddSharedMemberRequest(); // \Lockally\SDK\Model\AddSharedMemberRequest

try {
    $result = $apiInstance->addSharedMember($email, $add_shared_member_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->addSharedMember: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |
| **add_shared_member_request** | [**\Lockally\SDK\Model\AddSharedMemberRequest**](../Model/AddSharedMemberRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\SharedMember**](../Model/SharedMember.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createMailbox()`

```php
createMailbox($create_mailbox_request): \Lockally\SDK\Model\Mailbox
```

Create a mailbox

Creates a mailbox on a tenant-verified domain. If `password` is omitted, lockally generates a 16-char password and returns it in the response, shown once.  **Gate.** The mailbox's domain must already be registered AND verified for this tenant (via `/v1/domains` + `/v1/domains/{domain}/verify`).  **Idempotent.** Re-posting the same email returns the existing mailbox UNTOUCHED, password is NOT regenerated. To change a password, use PATCH instead.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MailboxesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_mailbox_request = new \Lockally\SDK\Model\CreateMailboxRequest(); // \Lockally\SDK\Model\CreateMailboxRequest

try {
    $result = $apiInstance->createMailbox($create_mailbox_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->createMailbox: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_mailbox_request** | [**\Lockally\SDK\Model\CreateMailboxRequest**](../Model/CreateMailboxRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Mailbox**](../Model/Mailbox.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteMailbox()`

```php
deleteMailbox($email)
```

Soft-delete a mailbox

Sets `soft_deleted_at = now()` and `hard_delete_after = now() + 90d` per design D25. A background sweep (planned) will hard-delete after the window. The mailbox is also disabled immediately.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MailboxesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email = 'email_example'; // string

try {
    $apiInstance->deleteMailbox($email);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->deleteMailbox: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |

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

## `downloadMailboxExport()`

```php
downloadMailboxExport($email, $token): \SplFileObject
```

Download a previously-issued mailbox export

Public endpoint (no Authorization header). Validates the one-shot token from the URL, marks it used, and streams an mbox file. Second GET with the same token returns 404, tokens are single-use.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



$apiInstance = new Lockally\SDK\Api\MailboxesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$email = 'email_example'; // string
$token = 'token_example'; // string

try {
    $result = $apiInstance->downloadMailboxExport($email, $token);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->downloadMailboxExport: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |
| **token** | **string**|  | |

### Return type

**\SplFileObject**

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/mbox`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `exportMailbox()`

```php
exportMailbox($email): \Lockally\SDK\Model\ExportMailbox201Response
```

Request a mailbox export

Issues a one-shot \"presigned\" download URL for the mailbox's content in mbox format. The URL works without an Authorization header, the token in the query string is the authz. TTL is 5 minutes; the token is consumed on first GET.  **v1 caveat:** the synthesized mbox only contains outbound mail (sent mail only). A later version will cover received mail for full inbox + folder structure + flags. The endpoint contract stays unchanged.  **Scope changed:** this used to accept `mailboxes:read`. It takes any mailbox in the tenant and returns that mailbox's mail, so it now requires `tenant:admin`, matching `POST /v1/ediscovery/export`. A key scoped `mailboxes:read` gets 403 and has to be reissued; admin console sessions are unaffected.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MailboxesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email = 'email_example'; // string

try {
    $result = $apiInstance->exportMailbox($email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->exportMailbox: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\ExportMailbox201Response**](../Model/ExportMailbox201Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getMailbox()`

```php
getMailbox($email): \Lockally\SDK\Model\Mailbox
```

Get a mailbox

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MailboxesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email = 'email_example'; // string

try {
    $result = $apiInstance->getMailbox($email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->getMailbox: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Mailbox**](../Model/Mailbox.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listMailboxes()`

```php
listMailboxes($limit): \Lockally\SDK\Model\ListMailboxes200Response
```

List mailboxes

Returns mailboxes under the calling tenant, active and soft-deleted. `?limit=N` between 1 and 200 (default 50).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MailboxesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$limit = 50; // int

try {
    $result = $apiInstance->listMailboxes($limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->listMailboxes: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **limit** | **int**|  | [optional] [default to 50] |

### Return type

[**\Lockally\SDK\Model\ListMailboxes200Response**](../Model/ListMailboxes200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listSharedMembers()`

```php
listSharedMembers($email): \Lockally\SDK\Model\ListSharedMembers200Response
```

List shared mailbox members

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MailboxesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email = 'email_example'; // string

try {
    $result = $apiInstance->listSharedMembers($email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->listSharedMembers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\ListSharedMembers200Response**](../Model/ListSharedMembers200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `removeSharedMember()`

```php
removeSharedMember($email, $member_email)
```

Remove a shared mailbox member

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MailboxesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email = 'email_example'; // string
$member_email = 'member_email_example'; // string

try {
    $apiInstance->removeSharedMember($email, $member_email);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->removeSharedMember: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |
| **member_email** | **string**|  | |

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

## `updateMailbox()`

```php
updateMailbox($email, $update_mailbox_request): \Lockally\SDK\Model\Mailbox
```

Update a mailbox

Supply at least one of `password`, `quota_bytes`, `disabled`. Returns the updated mailbox.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\MailboxesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email = 'email_example'; // string
$update_mailbox_request = new \Lockally\SDK\Model\UpdateMailboxRequest(); // \Lockally\SDK\Model\UpdateMailboxRequest

try {
    $result = $apiInstance->updateMailbox($email, $update_mailbox_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->updateMailbox: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |
| **update_mailbox_request** | [**\Lockally\SDK\Model\UpdateMailboxRequest**](../Model/UpdateMailboxRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Mailbox**](../Model/Mailbox.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
