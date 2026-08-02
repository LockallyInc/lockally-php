# Lockally\SDK\MailboxesApi

Mailboxes on verified tenant domains

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**addSharedMember()**](MailboxesApi.md#addSharedMember) | **POST** /v1/mailboxes/{email}/members | Add a shared mailbox member |
| [**listSharedMembers()**](MailboxesApi.md#listSharedMembers) | **GET** /v1/mailboxes/{email}/members | List shared mailbox members |
| [**removeSharedMember()**](MailboxesApi.md#removeSharedMember) | **DELETE** /v1/mailboxes/{email}/members/{memberEmail} | Remove a shared mailbox member |
| [**v1MailboxesEmailDelete()**](MailboxesApi.md#v1MailboxesEmailDelete) | **DELETE** /v1/mailboxes/{email} | Soft-delete a mailbox |
| [**v1MailboxesEmailExportDownloadGet()**](MailboxesApi.md#v1MailboxesEmailExportDownloadGet) | **GET** /v1/mailboxes/{email}/export/download | Download a previously-issued mailbox export |
| [**v1MailboxesEmailExportPost()**](MailboxesApi.md#v1MailboxesEmailExportPost) | **POST** /v1/mailboxes/{email}/export | Request a mailbox export |
| [**v1MailboxesEmailGet()**](MailboxesApi.md#v1MailboxesEmailGet) | **GET** /v1/mailboxes/{email} | Get a mailbox |
| [**v1MailboxesEmailPatch()**](MailboxesApi.md#v1MailboxesEmailPatch) | **PATCH** /v1/mailboxes/{email} | Update a mailbox |
| [**v1MailboxesEmailVacationDelete()**](MailboxesApi.md#v1MailboxesEmailVacationDelete) | **DELETE** /v1/mailboxes/{email}/vacation | Remove the vacation responder |
| [**v1MailboxesEmailVacationGet()**](MailboxesApi.md#v1MailboxesEmailVacationGet) | **GET** /v1/mailboxes/{email}/vacation | Get the vacation responder |
| [**v1MailboxesEmailVacationPut()**](MailboxesApi.md#v1MailboxesEmailVacationPut) | **PUT** /v1/mailboxes/{email}/vacation | Set the vacation responder |
| [**v1MailboxesGet()**](MailboxesApi.md#v1MailboxesGet) | **GET** /v1/mailboxes | List mailboxes |
| [**v1MailboxesPost()**](MailboxesApi.md#v1MailboxesPost) | **POST** /v1/mailboxes | Create a mailbox |
| [**v1VacationGet()**](MailboxesApi.md#v1VacationGet) | **GET** /v1/vacation | List all vacation responders |


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

## `v1MailboxesEmailDelete()`

```php
v1MailboxesEmailDelete($email)
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
    $apiInstance->v1MailboxesEmailDelete($email);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->v1MailboxesEmailDelete: ', $e->getMessage(), PHP_EOL;
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

## `v1MailboxesEmailExportDownloadGet()`

```php
v1MailboxesEmailExportDownloadGet($email, $token): \SplFileObject
```

Download a previously-issued mailbox export

Public endpoint (no Authorization header). Validates the one-shot token from the URL, marks it used, and streams an mbox file. Second GET with the same token returns 404 — tokens are single-use.

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
    $result = $apiInstance->v1MailboxesEmailExportDownloadGet($email, $token);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->v1MailboxesEmailExportDownloadGet: ', $e->getMessage(), PHP_EOL;
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

## `v1MailboxesEmailExportPost()`

```php
v1MailboxesEmailExportPost($email): \Lockally\SDK\Model\V1MailboxesEmailExportPost201Response
```

Request a mailbox export

Issues a one-shot \"presigned\" download URL for the mailbox's content in mbox format. The URL works without an Authorization header — the token in the query string is the authz. TTL is 5 minutes; the token is consumed on first GET.  **v1 caveat:** the synthesized mbox only contains outbound mail (from `lockally.messages`). v2 swaps in Stalwart's export primitive for full inbox + folder structure + flags. The endpoint contract stays unchanged.

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
    $result = $apiInstance->v1MailboxesEmailExportPost($email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->v1MailboxesEmailExportPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\V1MailboxesEmailExportPost201Response**](../Model/V1MailboxesEmailExportPost201Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1MailboxesEmailGet()`

```php
v1MailboxesEmailGet($email): \Lockally\SDK\Model\Mailbox
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
    $result = $apiInstance->v1MailboxesEmailGet($email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->v1MailboxesEmailGet: ', $e->getMessage(), PHP_EOL;
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

## `v1MailboxesEmailPatch()`

```php
v1MailboxesEmailPatch($email, $v1_mailboxes_email_patch_request): \Lockally\SDK\Model\Mailbox
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
$v1_mailboxes_email_patch_request = new \Lockally\SDK\Model\V1MailboxesEmailPatchRequest(); // \Lockally\SDK\Model\V1MailboxesEmailPatchRequest

try {
    $result = $apiInstance->v1MailboxesEmailPatch($email, $v1_mailboxes_email_patch_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->v1MailboxesEmailPatch: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |
| **v1_mailboxes_email_patch_request** | [**\Lockally\SDK\Model\V1MailboxesEmailPatchRequest**](../Model/V1MailboxesEmailPatchRequest.md)|  | |

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

## `v1MailboxesEmailVacationDelete()`

```php
v1MailboxesEmailVacationDelete($email)
```

Remove the vacation responder

Idempotent — 204 whether or not a row existed.

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
    $apiInstance->v1MailboxesEmailVacationDelete($email);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->v1MailboxesEmailVacationDelete: ', $e->getMessage(), PHP_EOL;
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

## `v1MailboxesEmailVacationGet()`

```php
v1MailboxesEmailVacationGet($email): \Lockally\SDK\Model\VacationResponder
```

Get the vacation responder

Returns the stored vacation rule or 404 if none is set.

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
    $result = $apiInstance->v1MailboxesEmailVacationGet($email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->v1MailboxesEmailVacationGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\VacationResponder**](../Model/VacationResponder.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1MailboxesEmailVacationPut()`

```php
v1MailboxesEmailVacationPut($email, $v1_mailboxes_email_vacation_put_request): \Lockally\SDK\Model\VacationResponder
```

Set the vacation responder

Upsert — same endpoint creates or replaces the rule. Clears `synced_at`; the rule is staged on lockally until a sync worker pushes it to the mail server.

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
$v1_mailboxes_email_vacation_put_request = new \Lockally\SDK\Model\V1MailboxesEmailVacationPutRequest(); // \Lockally\SDK\Model\V1MailboxesEmailVacationPutRequest

try {
    $result = $apiInstance->v1MailboxesEmailVacationPut($email, $v1_mailboxes_email_vacation_put_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->v1MailboxesEmailVacationPut: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |
| **v1_mailboxes_email_vacation_put_request** | [**\Lockally\SDK\Model\V1MailboxesEmailVacationPutRequest**](../Model/V1MailboxesEmailVacationPutRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\VacationResponder**](../Model/VacationResponder.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1MailboxesGet()`

```php
v1MailboxesGet($limit): \Lockally\SDK\Model\V1MailboxesGet200Response
```

List mailboxes

Returns mailboxes under the calling tenant — active and soft-deleted. `?limit=N` between 1 and 200 (default 50).

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
    $result = $apiInstance->v1MailboxesGet($limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->v1MailboxesGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **limit** | **int**|  | [optional] [default to 50] |

### Return type

[**\Lockally\SDK\Model\V1MailboxesGet200Response**](../Model/V1MailboxesGet200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1MailboxesPost()`

```php
v1MailboxesPost($v1_mailboxes_post_request): \Lockally\SDK\Model\Mailbox
```

Create a mailbox

Creates a mailbox on a tenant-verified domain. If `password` is omitted, lockally generates a 16-char password and returns it in the response — shown once.  **Gate.** The mailbox's domain must already be registered AND verified for this tenant (via `/v1/domains` + `/v1/domains/{domain}/verify`).  **Idempotent.** Re-posting the same email returns the existing mailbox UNTOUCHED — password is NOT regenerated. To change a password, use PATCH instead.

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
$v1_mailboxes_post_request = new \Lockally\SDK\Model\V1MailboxesPostRequest(); // \Lockally\SDK\Model\V1MailboxesPostRequest

try {
    $result = $apiInstance->v1MailboxesPost($v1_mailboxes_post_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->v1MailboxesPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **v1_mailboxes_post_request** | [**\Lockally\SDK\Model\V1MailboxesPostRequest**](../Model/V1MailboxesPostRequest.md)|  | |

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

## `v1VacationGet()`

```php
v1VacationGet(): \Lockally\SDK\Model\V1VacationGet200Response
```

List all vacation responders

Returns every vacation responder for the calling tenant.

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

try {
    $result = $apiInstance->v1VacationGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling MailboxesApi->v1VacationGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\V1VacationGet200Response**](../Model/V1VacationGet200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
