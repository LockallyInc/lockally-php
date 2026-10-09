# Lockally\SDK\DraftsApi

Agent draft review and approval (HITL)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**v1DraftsDraftIDApprovePost()**](DraftsApi.md#v1DraftsDraftIDApprovePost) | **POST** /v1/drafts/{draftID}/approve | Approve a pending draft (human) |
| [**v1DraftsDraftIDCancelPost()**](DraftsApi.md#v1DraftsDraftIDCancelPost) | **POST** /v1/drafts/{draftID}/cancel | Withdraw a pending draft |
| [**v1DraftsDraftIDGet()**](DraftsApi.md#v1DraftsDraftIDGet) | **GET** /v1/drafts/{draftID} | Get a draft |
| [**v1DraftsDraftIDRejectPost()**](DraftsApi.md#v1DraftsDraftIDRejectPost) | **POST** /v1/drafts/{draftID}/reject | Reject a pending draft (human) |
| [**v1DraftsGet()**](DraftsApi.md#v1DraftsGet) | **GET** /v1/drafts | List drafts |
| [**v1InboxesMailboxDraftsPost()**](DraftsApi.md#v1InboxesMailboxDraftsPost) | **POST** /v1/inboxes/{mailbox}/drafts | Propose a new conversation as a draft |
| [**v1ThreadsThreadIDDraftsPost()**](DraftsApi.md#v1ThreadsThreadIDDraftsPost) | **POST** /v1/threads/{threadID}/drafts | Propose a reply as a draft |


## `v1DraftsDraftIDApprovePost()`

```php
v1DraftsDraftIDApprovePost($draft_id): object
```

Approve a pending draft (human)

Sends the draft exactly as reviewed, through the agent stream (loop detector included). Fires draft.approved.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DraftsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$draft_id = 'draft_id_example'; // string

try {
    $result = $apiInstance->v1DraftsDraftIDApprovePost($draft_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->v1DraftsDraftIDApprovePost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **draft_id** | **string**|  | |

### Return type

**object**

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1DraftsDraftIDCancelPost()`

```php
v1DraftsDraftIDCancelPost($draft_id): object
```

Withdraw a pending draft

Only the API key that created the draft may cancel it.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DraftsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$draft_id = 'draft_id_example'; // string

try {
    $result = $apiInstance->v1DraftsDraftIDCancelPost($draft_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->v1DraftsDraftIDCancelPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **draft_id** | **string**|  | |

### Return type

**object**

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1DraftsDraftIDGet()`

```php
v1DraftsDraftIDGet($draft_id): object
```

Get a draft

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DraftsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$draft_id = 'draft_id_example'; // string

try {
    $result = $apiInstance->v1DraftsDraftIDGet($draft_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->v1DraftsDraftIDGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **draft_id** | **string**|  | |

### Return type

**object**

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1DraftsDraftIDRejectPost()`

```php
v1DraftsDraftIDRejectPost($draft_id): object
```

Reject a pending draft (human)

Body: {\"reason\": \"...\"} (optional). Fires draft.rejected.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DraftsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$draft_id = 'draft_id_example'; // string

try {
    $result = $apiInstance->v1DraftsDraftIDRejectPost($draft_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->v1DraftsDraftIDRejectPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **draft_id** | **string**|  | |

### Return type

**object**

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1DraftsGet()`

```php
v1DraftsGet($status, $limit): object
```

List drafts

Filter with ?status=pending_approval|sent|rejected|cancelled. Keys see drafts of granted mailboxes; admin sessions see all.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DraftsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$status = 'status_example'; // string
$limit = 50; // int

try {
    $result = $apiInstance->v1DraftsGet($status, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->v1DraftsGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **status** | **string**|  | [optional] |
| **limit** | **int**|  | [optional] [default to 50] |

### Return type

**object**

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1InboxesMailboxDraftsPost()`

```php
v1InboxesMailboxDraftsPost($mailbox, $idempotency_key): object
```

Propose a new conversation as a draft

New-conversation drafts ALWAYS require human approval (policy flag new_thread). Idempotency-Key required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DraftsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$mailbox = 'mailbox_example'; // string
$idempotency_key = 'idempotency_key_example'; // string

try {
    $result = $apiInstance->v1InboxesMailboxDraftsPost($mailbox, $idempotency_key);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->v1InboxesMailboxDraftsPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **mailbox** | **string**|  | |
| **idempotency_key** | **string**|  | |

### Return type

**object**

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1ThreadsThreadIDDraftsPost()`

```php
v1ThreadsThreadIDDraftsPost($thread_id, $idempotency_key): object
```

Propose a reply as a draft

The safe default over /reply: the deterministic policy engine auto-sends clean in-thread replies and holds anything risky (PII, new recipients, injection-flagged threads, always-approve mailboxes) for human approval. Fires draft.pending_approval when held. Idempotency-Key required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DraftsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$thread_id = 'thread_id_example'; // string
$idempotency_key = 'idempotency_key_example'; // string

try {
    $result = $apiInstance->v1ThreadsThreadIDDraftsPost($thread_id, $idempotency_key);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->v1ThreadsThreadIDDraftsPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **thread_id** | **string**|  | |
| **idempotency_key** | **string**|  | |

### Return type

**object**

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
