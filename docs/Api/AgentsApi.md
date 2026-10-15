# Lockally\SDK\AgentsApi

AI-native agent surface: inboxes, threads, drafts, grants (per-mailbox authorization)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**downloadThreadAttachment()**](AgentsApi.md#downloadThreadAttachment) | **GET** /v1/threads/{threadID}/messages/{messageID}/attachments/{idx} | Download an attachment |
| [**getThread()**](AgentsApi.md#getThread) | **GET** /v1/threads/{threadID} | Get a whole conversation |
| [**getThreadMessage()**](AgentsApi.md#getThreadMessage) | **GET** /v1/threads/{threadID}/messages/{messageID} | Get one message with body |
| [**grantApiKeyMailbox()**](AgentsApi.md#grantApiKeyMailbox) | **POST** /v1/api-keys/{keyID}/mailboxes | Grant a mailbox to a key |
| [**listApiKeyMailboxes()**](AgentsApi.md#listApiKeyMailboxes) | **GET** /v1/api-keys/{keyID}/mailboxes | List a key&#39;s mailbox grants |
| [**listInboxes()**](AgentsApi.md#listInboxes) | **GET** /v1/inboxes | List granted inboxes |
| [**listThreads()**](AgentsApi.md#listThreads) | **GET** /v1/inboxes/{mailbox}/threads | List conversation threads |
| [**lookupContact()**](AgentsApi.md#lookupContact) | **GET** /v1/contacts/lookup | Who is this sender? |
| [**markThreadMessageRead()**](AgentsApi.md#markThreadMessageRead) | **POST** /v1/threads/{threadID}/messages/{messageID}/read | Mark read/unread |
| [**replyToThread()**](AgentsApi.md#replyToThread) | **POST** /v1/threads/{threadID}/reply | Reply in-thread (agent stream) |
| [**revokeApiKeyMailbox()**](AgentsApi.md#revokeApiKeyMailbox) | **DELETE** /v1/api-keys/{keyID}/mailboxes/{mailboxID} | Revoke a mailbox grant |
| [**startConversation()**](AgentsApi.md#startConversation) | **POST** /v1/inboxes/{mailbox}/messages | Start a new conversation (agent stream) |
| [**whoami()**](AgentsApi.md#whoami) | **GET** /v1/auth/whoami | Introspect the calling credentials |


## `downloadThreadAttachment()`

```php
downloadThreadAttachment($thread_id, $message_id, $idx)
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
    $apiInstance->downloadThreadAttachment($thread_id, $message_id, $idx);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->downloadThreadAttachment: ', $e->getMessage(), PHP_EOL;
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

## `getThread()`

```php
getThread($thread_id): \Lockally\SDK\Model\Thread
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
    $result = $apiInstance->getThread($thread_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->getThread: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **thread_id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Thread**](../Model/Thread.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getThreadMessage()`

```php
getThreadMessage($thread_id, $message_id): \Lockally\SDK\Model\ThreadMessageBody
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
    $result = $apiInstance->getThreadMessage($thread_id, $message_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->getThreadMessage: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **thread_id** | **string**|  | |
| **message_id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\ThreadMessageBody**](../Model/ThreadMessageBody.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `grantApiKeyMailbox()`

```php
grantApiKeyMailbox($key_id): \Lockally\SDK\Model\MailboxGrant
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
    $result = $apiInstance->grantApiKeyMailbox($key_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->grantApiKeyMailbox: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **key_id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\MailboxGrant**](../Model/MailboxGrant.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listApiKeyMailboxes()`

```php
listApiKeyMailboxes($key_id): \Lockally\SDK\Model\MailboxGrantList
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
    $result = $apiInstance->listApiKeyMailboxes($key_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->listApiKeyMailboxes: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **key_id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\MailboxGrantList**](../Model/MailboxGrantList.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listInboxes()`

```php
listInboxes(): \Lockally\SDK\Model\InboxList
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
    $result = $apiInstance->listInboxes();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->listInboxes: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\InboxList**](../Model/InboxList.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listThreads()`

```php
listThreads($mailbox, $since, $before, $limit): \Lockally\SDK\Model\ThreadList
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
    $result = $apiInstance->listThreads($mailbox, $since, $before, $limit);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->listThreads: ', $e->getMessage(), PHP_EOL;
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

[**\Lockally\SDK\Model\ThreadList**](../Model/ThreadList.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `lookupContact()`

```php
lookupContact($email): \Lockally\SDK\Model\ContactLookup
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
    $result = $apiInstance->lookupContact($email);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->lookupContact: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **email** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\ContactLookup**](../Model/ContactLookup.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `markThreadMessageRead()`

```php
markThreadMessageRead($thread_id, $message_id): \Lockally\SDK\Model\MarkReadResult
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
    $result = $apiInstance->markThreadMessageRead($thread_id, $message_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->markThreadMessageRead: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **thread_id** | **string**|  | |
| **message_id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\MarkReadResult**](../Model/MarkReadResult.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `replyToThread()`

```php
replyToThread($thread_id, $idempotency_key): \Lockally\SDK\Model\AgentSendResult
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
    $result = $apiInstance->replyToThread($thread_id, $idempotency_key);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->replyToThread: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **thread_id** | **string**|  | |
| **idempotency_key** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\AgentSendResult**](../Model/AgentSendResult.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `revokeApiKeyMailbox()`

```php
revokeApiKeyMailbox($key_id, $mailbox_id)
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
    $apiInstance->revokeApiKeyMailbox($key_id, $mailbox_id);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->revokeApiKeyMailbox: ', $e->getMessage(), PHP_EOL;
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

## `startConversation()`

```php
startConversation($mailbox, $idempotency_key, $start_conversation_request): \Lockally\SDK\Model\AgentSendResult
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
$start_conversation_request = new \Lockally\SDK\Model\StartConversationRequest(); // \Lockally\SDK\Model\StartConversationRequest

try {
    $result = $apiInstance->startConversation($mailbox, $idempotency_key, $start_conversation_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->startConversation: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **mailbox** | **string**|  | |
| **idempotency_key** | **string**|  | |
| **start_conversation_request** | [**\Lockally\SDK\Model\StartConversationRequest**](../Model/StartConversationRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\AgentSendResult**](../Model/AgentSendResult.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `whoami()`

```php
whoami(): \Lockally\SDK\Model\Whoami
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
    $result = $apiInstance->whoami();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AgentsApi->whoami: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\Whoami**](../Model/Whoami.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
