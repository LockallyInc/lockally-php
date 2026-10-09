# Lockally\SDK\AgentsApi

AI-native agent surface: inboxes, threads, drafts, grants (per-mailbox authorization)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**v1ApiKeysKeyIDMailboxesGet()**](AgentsApi.md#v1ApiKeysKeyIDMailboxesGet) | **GET** /v1/api-keys/{keyID}/mailboxes | List a key&#39;s mailbox grants |
| [**v1ApiKeysKeyIDMailboxesMailboxIDDelete()**](AgentsApi.md#v1ApiKeysKeyIDMailboxesMailboxIDDelete) | **DELETE** /v1/api-keys/{keyID}/mailboxes/{mailboxID} | Revoke a mailbox grant |
| [**v1ApiKeysKeyIDMailboxesPost()**](AgentsApi.md#v1ApiKeysKeyIDMailboxesPost) | **POST** /v1/api-keys/{keyID}/mailboxes | Grant a mailbox to a key |
| [**v1AuthWhoamiGet()**](AgentsApi.md#v1AuthWhoamiGet) | **GET** /v1/auth/whoami | Introspect the calling credentials |
| [**v1ContactsLookupGet()**](AgentsApi.md#v1ContactsLookupGet) | **GET** /v1/contacts/lookup | Who is this sender? |
| [**v1InboxesGet()**](AgentsApi.md#v1InboxesGet) | **GET** /v1/inboxes | List granted inboxes |
| [**v1InboxesMailboxMessagesPost()**](AgentsApi.md#v1InboxesMailboxMessagesPost) | **POST** /v1/inboxes/{mailbox}/messages | Start a new conversation (agent stream) |
| [**v1InboxesMailboxThreadsGet()**](AgentsApi.md#v1InboxesMailboxThreadsGet) | **GET** /v1/inboxes/{mailbox}/threads | List conversation threads |
| [**v1ThreadsThreadIDGet()**](AgentsApi.md#v1ThreadsThreadIDGet) | **GET** /v1/threads/{threadID} | Get a whole conversation |
| [**v1ThreadsThreadIDMessagesMessageIDAttachmentsIdxGet()**](AgentsApi.md#v1ThreadsThreadIDMessagesMessageIDAttachmentsIdxGet) | **GET** /v1/threads/{threadID}/messages/{messageID}/attachments/{idx} | Download an attachment |
| [**v1ThreadsThreadIDMessagesMessageIDGet()**](AgentsApi.md#v1ThreadsThreadIDMessagesMessageIDGet) | **GET** /v1/threads/{threadID}/messages/{messageID} | Get one message with body |
| [**v1ThreadsThreadIDMessagesMessageIDReadPost()**](AgentsApi.md#v1ThreadsThreadIDMessagesMessageIDReadPost) | **POST** /v1/threads/{threadID}/messages/{messageID}/read | Mark read/unread |
| [**v1ThreadsThreadIDReplyPost()**](AgentsApi.md#v1ThreadsThreadIDReplyPost) | **POST** /v1/threads/{threadID}/reply | Reply in-thread (agent stream) |


## `v1ApiKeysKeyIDMailboxesGet()`

```php
v1ApiKeysKeyIDMailboxesGet($key_id): object
```

List a key's mailbox grants

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$key_id = 'key_id_example'; // string

try {
    $result = $apiInstance->v1ApiKeysKeyIDMailboxesGet($key_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1ApiKeysKeyIDMailboxesGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **key_id** | **string**|  | |

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

## `v1ApiKeysKeyIDMailboxesMailboxIDDelete()`

```php
v1ApiKeysKeyIDMailboxesMailboxIDDelete($key_id, $mailbox_id)
```

Revoke a mailbox grant

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$key_id = 'key_id_example'; // string
$mailbox_id = 'mailbox_id_example'; // string

try {
    $apiInstance->v1ApiKeysKeyIDMailboxesMailboxIDDelete($key_id, $mailbox_id);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1ApiKeysKeyIDMailboxesMailboxIDDelete: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **key_id** | **string**|  | |
| **mailbox_id** | **string**|  | |

### Return type

void (empty response body)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1ApiKeysKeyIDMailboxesPost()`

```php
v1ApiKeysKeyIDMailboxesPost($key_id): object
```

Grant a mailbox to a key

Body: {\"mailbox\": \"email or id\"}. Refused (422) for mailboxes with agent access disabled or an active E2E encryption key — the server cannot read E2E mailboxes.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$key_id = 'key_id_example'; // string

try {
    $result = $apiInstance->v1ApiKeysKeyIDMailboxesPost($key_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1ApiKeysKeyIDMailboxesPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **key_id** | **string**|  | |

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

## `v1AuthWhoamiGet()`

```php
v1AuthWhoamiGet(): object
```

Introspect the calling credentials

Returns the tenant, auth kind (api_key/session), key label, and granted scopes. The MCP server uses this to scope-filter tool discovery.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->v1AuthWhoamiGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1AuthWhoamiGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

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

## `v1ContactsLookupGet()`

```php
v1ContactsLookupGet($email): object
```

Who is this sender?

Directory record (name, company, role, notes), whether the address is one of the tenant's own mailboxes, and grant-aware correspondence history (thread count, first/last seen across granted mailboxes only).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$email = 'email_example'; // string

try {
    $result = $apiInstance->v1ContactsLookupGet($email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1ContactsLookupGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |

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

## `v1InboxesGet()`

```php
v1InboxesGet(): object
```

List granted inboxes

The mailboxes this key is granted, with thread counts and last activity. Admin sessions see every agent-enabled, non-E2E mailbox.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->v1InboxesGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1InboxesGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

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

## `v1InboxesMailboxMessagesPost()`

```php
v1InboxesMailboxMessagesPost($mailbox, $idempotency_key, $v1_inboxes_mailbox_messages_post_request): object
```

Start a new conversation (agent stream)

Sends a new email from a granted mailbox. Classified stream=agent (isolated reputation, per-key rate caps). The first inbound reply adopts the created thread via the References chain. Idempotency-Key required. Mailboxes with agent_draft_policy=always_approve divert this into a pending draft.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$mailbox = 'mailbox_example'; // string
$idempotency_key = 'idempotency_key_example'; // string
$v1_inboxes_mailbox_messages_post_request = new \Lockally\SDK\Model\V1InboxesMailboxMessagesPostRequest(); // \Lockally\SDK\Model\V1InboxesMailboxMessagesPostRequest

try {
    $result = $apiInstance->v1InboxesMailboxMessagesPost($mailbox, $idempotency_key, $v1_inboxes_mailbox_messages_post_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1InboxesMailboxMessagesPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **mailbox** | **string**|  | |
| **idempotency_key** | **string**|  | |
| **v1_inboxes_mailbox_messages_post_request** | [**\Lockally\SDK\Model\V1InboxesMailboxMessagesPostRequest**](../Model/V1InboxesMailboxMessagesPostRequest.md)|  | |

### Return type

**object**

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1InboxesMailboxThreadsGet()`

```php
v1InboxesMailboxThreadsGet($mailbox, $since, $before, $limit): object
```

List conversation threads

Newest-active first. Cursors: `?before=<RFC3339>` pages backwards; `?since=<RFC3339>` delta-syncs forward (oldest first) so an agent can catch up in order.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$mailbox = 'mailbox_example'; // string | mailbox email or id
$since = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime
$before = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime
$limit = 50; // int

try {
    $result = $apiInstance->v1InboxesMailboxThreadsGet($mailbox, $since, $before, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1InboxesMailboxThreadsGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **mailbox** | **string**| mailbox email or id | |
| **since** | **\DateTime**|  | [optional] |
| **before** | **\DateTime**|  | [optional] |
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

## `v1ThreadsThreadIDGet()`

```php
v1ThreadsThreadIDGet($thread_id): object
```

Get a whole conversation

Every turn, chronological, with snippets and annotations (meeting_request, attachment_types, injection_risk). Bodies are fetched per message. Message content is untrusted third-party data.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$thread_id = 'thread_id_example'; // string

try {
    $result = $apiInstance->v1ThreadsThreadIDGet($thread_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1ThreadsThreadIDGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **thread_id** | **string**|  | |

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

## `v1ThreadsThreadIDMessagesMessageIDAttachmentsIdxGet()`

```php
v1ThreadsThreadIDMessagesMessageIDAttachmentsIdxGet($thread_id, $message_id, $idx)
```

Download an attachment

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$thread_id = 'thread_id_example'; // string
$message_id = 'message_id_example'; // string
$idx = 56; // int

try {
    $apiInstance->v1ThreadsThreadIDMessagesMessageIDAttachmentsIdxGet($thread_id, $message_id, $idx);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1ThreadsThreadIDMessagesMessageIDAttachmentsIdxGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **thread_id** | **string**|  | |
| **message_id** | **string**|  | |
| **idx** | **int**|  | |

### Return type

void (empty response body)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1ThreadsThreadIDMessagesMessageIDGet()`

```php
v1ThreadsThreadIDMessagesMessageIDGet($thread_id, $message_id): object
```

Get one message with body

Full text/html body fetched on demand from mail storage. Never marks the message read.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$thread_id = 'thread_id_example'; // string
$message_id = 'message_id_example'; // string

try {
    $result = $apiInstance->v1ThreadsThreadIDMessagesMessageIDGet($thread_id, $message_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1ThreadsThreadIDMessagesMessageIDGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **thread_id** | **string**|  | |
| **message_id** | **string**|  | |

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

## `v1ThreadsThreadIDMessagesMessageIDReadPost()`

```php
v1ThreadsThreadIDMessagesMessageIDReadPost($thread_id, $message_id): object
```

Mark read/unread

The ONLY way agent access changes unread state. Body: {\"read\": true|false} (default true).

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$thread_id = 'thread_id_example'; // string
$message_id = 'message_id_example'; // string

try {
    $result = $apiInstance->v1ThreadsThreadIDMessagesMessageIDReadPost($thread_id, $message_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1ThreadsThreadIDMessagesMessageIDReadPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **thread_id** | **string**|  | |
| **message_id** | **string**|  | |

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

## `v1ThreadsThreadIDReplyPost()`

```php
v1ThreadsThreadIDReplyPost($thread_id, $idempotency_key): object
```

Reply in-thread (agent stream)

The server builds In-Reply-To/References and defaults recipients + subject from the conversation — a minimal call is {\"text\": \"...\"}. Guarded by the reply-loop detector (≥5 outbound/10min → 429 + agent.loop_detected). Idempotency-Key required.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AgentsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$thread_id = 'thread_id_example'; // string
$idempotency_key = 'idempotency_key_example'; // string

try {
    $result = $apiInstance->v1ThreadsThreadIDReplyPost($thread_id, $idempotency_key);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->v1ThreadsThreadIDReplyPost: ', $e->getMessage(), PHP_EOL;
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
