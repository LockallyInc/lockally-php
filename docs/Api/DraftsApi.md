# Lockally\SDK\DraftsApi

Agent draft review and approval (HITL)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**approveDraft()**](DraftsApi.md#approveDraft) | **POST** /v1/drafts/{draftID}/approve | Approve a pending draft (human) |
| [**cancelDraft()**](DraftsApi.md#cancelDraft) | **POST** /v1/drafts/{draftID}/cancel | Withdraw a pending draft |
| [**createConversationDraft()**](DraftsApi.md#createConversationDraft) | **POST** /v1/inboxes/{mailbox}/drafts | Propose a new conversation as a draft |
| [**createReplyDraft()**](DraftsApi.md#createReplyDraft) | **POST** /v1/threads/{threadID}/drafts | Propose a reply as a draft |
| [**getDraft()**](DraftsApi.md#getDraft) | **GET** /v1/drafts/{draftID} | Get a draft |
| [**listDrafts()**](DraftsApi.md#listDrafts) | **GET** /v1/drafts | List drafts |
| [**rejectDraft()**](DraftsApi.md#rejectDraft) | **POST** /v1/drafts/{draftID}/reject | Reject a pending draft (human) |


## `approveDraft()`

```php
approveDraft($draft_id): \Lockally\SDK\Model\DraftResult
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
    $result = $apiInstance->approveDraft($draft_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->approveDraft: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **draft_id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\DraftResult**](../Model/DraftResult.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `cancelDraft()`

```php
cancelDraft($draft_id): \Lockally\SDK\Model\Draft
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
    $result = $apiInstance->cancelDraft($draft_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->cancelDraft: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **draft_id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Draft**](../Model/Draft.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createConversationDraft()`

```php
createConversationDraft($mailbox, $idempotency_key): \Lockally\SDK\Model\DraftResult
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
    $result = $apiInstance->createConversationDraft($mailbox, $idempotency_key);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->createConversationDraft: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **mailbox** | **string**|  | |
| **idempotency_key** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\DraftResult**](../Model/DraftResult.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createReplyDraft()`

```php
createReplyDraft($thread_id, $idempotency_key): \Lockally\SDK\Model\DraftResult
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
    $result = $apiInstance->createReplyDraft($thread_id, $idempotency_key);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->createReplyDraft: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **thread_id** | **string**|  | |
| **idempotency_key** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\DraftResult**](../Model/DraftResult.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getDraft()`

```php
getDraft($draft_id): \Lockally\SDK\Model\Draft
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
    $result = $apiInstance->getDraft($draft_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->getDraft: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **draft_id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Draft**](../Model/Draft.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listDrafts()`

```php
listDrafts($status, $limit): \Lockally\SDK\Model\DraftList
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
    $result = $apiInstance->listDrafts($status, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->listDrafts: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **status** | **string**|  | [optional] |
| **limit** | **int**|  | [optional] [default to 50] |

### Return type

[**\Lockally\SDK\Model\DraftList**](../Model/DraftList.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `rejectDraft()`

```php
rejectDraft($draft_id): \Lockally\SDK\Model\Draft
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
    $result = $apiInstance->rejectDraft($draft_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DraftsApi->rejectDraft: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **draft_id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Draft**](../Model/Draft.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
