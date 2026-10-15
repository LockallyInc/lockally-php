# Lockally\SDK\DomainsApi

Tenant-owned mail domains and DNS verification

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**createDomain()**](DomainsApi.md#createDomain) | **POST** /v1/domains | Register a domain |
| [**deleteDomain()**](DomainsApi.md#deleteDomain) | **DELETE** /v1/domains/{domain} | Delete a domain |
| [**disableReturnPath()**](DomainsApi.md#disableReturnPath) | **DELETE** /v1/domains/{domain}/return-path | Turn off the custom Return-Path |
| [**enableReturnPath()**](DomainsApi.md#enableReturnPath) | **POST** /v1/domains/{domain}/return-path | Turn on the custom Return-Path |
| [**getDomain()**](DomainsApi.md#getDomain) | **GET** /v1/domains/{domain} | Get a domain |
| [**getReturnPath()**](DomainsApi.md#getReturnPath) | **GET** /v1/domains/{domain}/return-path | Get the custom Return-Path |
| [**listDomains()**](DomainsApi.md#listDomains) | **GET** /v1/domains | List domains |
| [**verifyDomain()**](DomainsApi.md#verifyDomain) | **POST** /v1/domains/{domain}/verify | Force-poll DNS verification |
| [**verifyReturnPath()**](DomainsApi.md#verifyReturnPath) | **POST** /v1/domains/{domain}/return-path/verify | Check the custom Return-Path records |


## `createDomain()`

```php
createDomain($create_domain_request): \Lockally\SDK\Model\Domain
```

Register a domain

Registers a new domain for the calling tenant. Generates a DKIM keypair and verification token. Returns DNS instructions the tenant must publish under their own DNS (verification TXT, SPF include, DKIM TXT, MX records to `mx1`/`mx2.lockally.com`, DMARC seed).  **Idempotent** — re-posting the same domain returns the existing record with the same DKIM keys and token (regenerating would break the tenant's published DNS). Returns 200 on idempotent hit, 201 on first create.  Returns 409 if the domain is already claimed by a different tenant.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DomainsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_domain_request = new \Lockally\SDK\Model\CreateDomainRequest(); // \Lockally\SDK\Model\CreateDomainRequest

try {
    $result = $apiInstance->createDomain($create_domain_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DomainsApi->createDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_domain_request** | [**\Lockally\SDK\Model\CreateDomainRequest**](../Model/CreateDomainRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Domain**](../Model/Domain.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteDomain()`

```php
deleteDomain($domain)
```

Delete a domain

Removes the domain registration. Refuses with 409 if any mailbox is still attached — delete the mailboxes first.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DomainsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$domain = 'domain_example'; // string

try {
    $apiInstance->deleteDomain($domain);
} catch (Exception $e) {
    echo 'Exception when calling DomainsApi->deleteDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **domain** | **string**|  | |

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

## `disableReturnPath()`

```php
disableReturnPath($domain)
```

Turn off the custom Return-Path

API mail uses the sender's own address as the envelope sender again, from the next message.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DomainsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$domain = 'domain_example'; // string

try {
    $apiInstance->disableReturnPath($domain);
} catch (Exception $e) {
    echo 'Exception when calling DomainsApi->disableReturnPath: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **domain** | **string**|  | |

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

## `enableReturnPath()`

```php
enableReturnPath($domain): \Lockally\SDK\Model\ReturnPath
```

Turn on the custom Return-Path

Moves it to `pending` and returns the two records to publish on `bounces.<domain>`. Nothing changes for mail until they are confirmed with the verify call. The domain must be verified. Available on every plan except Free.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DomainsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$domain = 'domain_example'; // string

try {
    $result = $apiInstance->enableReturnPath($domain);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DomainsApi->enableReturnPath: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **domain** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\ReturnPath**](../Model/ReturnPath.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getDomain()`

```php
getDomain($domain): \Lockally\SDK\Model\Domain
```

Get a domain

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DomainsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$domain = 'domain_example'; // string

try {
    $result = $apiInstance->getDomain($domain);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DomainsApi->getDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **domain** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Domain**](../Model/Domain.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getReturnPath()`

```php
getReturnPath($domain): \Lockally\SDK\Model\ReturnPath
```

Get the custom Return-Path

A custom Return-Path moves the envelope sender of mail sent through the API from this domain onto `bounces.<domain>`. Bounce reports then come back to Lockally instead of the sending mailbox, and a bounce that arrives after delivery marks the message bounced, suppresses the address and fires `delivery.bounced`. Mail sent from webmail or mail apps is not affected. DKIM stays signed by the domain itself. `status` is `off`, `pending` (records not confirmed yet) or `active`.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DomainsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$domain = 'domain_example'; // string

try {
    $result = $apiInstance->getReturnPath($domain);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DomainsApi->getReturnPath: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **domain** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\ReturnPath**](../Model/ReturnPath.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listDomains()`

```php
listDomains(): \Lockally\SDK\Model\ListDomains200Response
```

List domains

Returns every domain registered under the calling tenant.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DomainsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listDomains();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DomainsApi->listDomains: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\ListDomains200Response**](../Model/ListDomains200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `verifyDomain()`

```php
verifyDomain($domain): \Lockally\SDK\Model\Domain
```

Force-poll DNS verification

Synchronously checks the `_lockally-verify.<domain>` TXT record against the stored verification token. Returns 200 either way: the returned `verified` boolean tells you whether DNS now confirms. Caller polls until `verified: true`. In v2 a background worker auto-polls and fires a `domain.verified` webhook.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DomainsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$domain = 'domain_example'; // string

try {
    $result = $apiInstance->verifyDomain($domain);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DomainsApi->verifyDomain: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **domain** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Domain**](../Model/Domain.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `verifyReturnPath()`

```php
verifyReturnPath($domain): \Lockally\SDK\Model\ReturnPath
```

Check the custom Return-Path records

Looks up the MX and SPF records on `bounces.<domain>`. Returns 200 either way: while a record is missing the status stays `pending` and `check` says which one. Once both are found the Return-Path becomes `active` and the send path starts using it.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\DomainsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$domain = 'domain_example'; // string

try {
    $result = $apiInstance->verifyReturnPath($domain);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling DomainsApi->verifyReturnPath: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **domain** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\ReturnPath**](../Model/ReturnPath.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
