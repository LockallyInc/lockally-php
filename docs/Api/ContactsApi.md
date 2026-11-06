# Lockally\SDK\ContactsApi

Contact records (internal and external)

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**bulkUpsertExternalContacts()**](ContactsApi.md#bulkUpsertExternalContacts) | **PUT** /v1/contacts/external/{system} | Create or update up to 500 contacts by their ids in another system |
| [**createContact()**](ContactsApi.md#createContact) | **POST** /v1/contacts | Create a contact |
| [**deleteContact()**](ContactsApi.md#deleteContact) | **DELETE** /v1/contacts/{id} | Delete a contact |
| [**deleteExternalContact()**](ContactsApi.md#deleteExternalContact) | **DELETE** /v1/contacts/external/{system}/{external_id} | Delete a contact by its id in another system |
| [**getContact()**](ContactsApi.md#getContact) | **GET** /v1/contacts/{id} | Get a contact |
| [**getContactLists()**](ContactsApi.md#getContactLists) | **GET** /v1/contacts/{id}/lists | Get lists a contact belongs to |
| [**getExternalContact()**](ContactsApi.md#getExternalContact) | **GET** /v1/contacts/external/{system}/{external_id} | Get a contact by its id in another system |
| [**listContacts()**](ContactsApi.md#listContacts) | **GET** /v1/contacts | List contacts |
| [**updateContact()**](ContactsApi.md#updateContact) | **PATCH** /v1/contacts/{id} | Update a contact |
| [**upsertExternalContact()**](ContactsApi.md#upsertExternalContact) | **PUT** /v1/contacts/external/{system}/{external_id} | Create or update a contact by its id in another system |


## `bulkUpsertExternalContacts()`

```php
bulkUpsertExternalContacts($system, $bulk_upsert_external_contacts_request): \Lockally\SDK\Model\BulkUpsertExternalContacts200Response
```

Create or update up to 500 contacts by their ids in another system

For a sync. Each row stands alone: a bad row is reported in `results` with its index and the rest are stored, so the response is 200 whenever the request itself is well formed. Read `failed` and `results`. Two rows with the same `external_id` in one request are refused (the later one), because which is current cannot be known. Rerunning the same payload updates rather than duplicates.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$system = 'system_example'; // string
$bulk_upsert_external_contacts_request = new \Lockally\SDK\Model\BulkUpsertExternalContactsRequest(); // \Lockally\SDK\Model\BulkUpsertExternalContactsRequest

try {
    $result = $apiInstance->bulkUpsertExternalContacts($system, $bulk_upsert_external_contacts_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactsApi->bulkUpsertExternalContacts: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **system** | **string**|  | |
| **bulk_upsert_external_contacts_request** | [**\Lockally\SDK\Model\BulkUpsertExternalContactsRequest**](../Model/BulkUpsertExternalContactsRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\BulkUpsertExternalContacts200Response**](../Model/BulkUpsertExternalContacts200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createContact()`

```php
createContact($create_contact_request): \Lockally\SDK\Model\Contact
```

Create a contact

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_contact_request = new \Lockally\SDK\Model\CreateContactRequest(); // \Lockally\SDK\Model\CreateContactRequest

try {
    $result = $apiInstance->createContact($create_contact_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactsApi->createContact: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_contact_request** | [**\Lockally\SDK\Model\CreateContactRequest**](../Model/CreateContactRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Contact**](../Model/Contact.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteContact()`

```php
deleteContact($id)
```

Delete a contact

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->deleteContact($id);
} catch (Exception $e) {
    echo 'Exception when calling ContactsApi->deleteContact: ', $e->getMessage(), PHP_EOL;
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

## `deleteExternalContact()`

```php
deleteExternalContact($system, $external_id)
```

Delete a contact by its id in another system

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$system = 'system_example'; // string | Your label for the system the record comes from, for example `salesforce`, `hubspot` or `odoo`. 1 to 64 characters: lowercase letters, digits, dot, underscore or hyphen (upper case is folded).
$external_id = 'external_id_example'; // string | The record's id in that system, kept exactly as given (case matters). 1 to 255 characters, no spaces. URL-encode it.

try {
    $apiInstance->deleteExternalContact($system, $external_id);
} catch (Exception $e) {
    echo 'Exception when calling ContactsApi->deleteExternalContact: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **system** | **string**| Your label for the system the record comes from, for example &#x60;salesforce&#x60;, &#x60;hubspot&#x60; or &#x60;odoo&#x60;. 1 to 64 characters: lowercase letters, digits, dot, underscore or hyphen (upper case is folded). | |
| **external_id** | **string**| The record&#39;s id in that system, kept exactly as given (case matters). 1 to 255 characters, no spaces. URL-encode it. | |

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

## `getContact()`

```php
getContact($id): \Lockally\SDK\Model\Contact
```

Get a contact

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->getContact($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactsApi->getContact: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Contact**](../Model/Contact.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getContactLists()`

```php
getContactLists($id): \Lockally\SDK\Model\GetContactLists200Response
```

Get lists a contact belongs to

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->getContactLists($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactsApi->getContactLists: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\GetContactLists200Response**](../Model/GetContactLists200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getExternalContact()`

```php
getExternalContact($system, $external_id): \Lockally\SDK\Model\Contact
```

Get a contact by its id in another system

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$system = 'system_example'; // string | Your label for the system the record comes from, for example `salesforce`, `hubspot` or `odoo`. 1 to 64 characters: lowercase letters, digits, dot, underscore or hyphen (upper case is folded).
$external_id = 'external_id_example'; // string | The record's id in that system, kept exactly as given (case matters). 1 to 255 characters, no spaces. URL-encode it.

try {
    $result = $apiInstance->getExternalContact($system, $external_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactsApi->getExternalContact: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **system** | **string**| Your label for the system the record comes from, for example &#x60;salesforce&#x60;, &#x60;hubspot&#x60; or &#x60;odoo&#x60;. 1 to 64 characters: lowercase letters, digits, dot, underscore or hyphen (upper case is folded). | |
| **external_id** | **string**| The record&#39;s id in that system, kept exactly as given (case matters). 1 to 255 characters, no spaces. URL-encode it. | |

### Return type

[**\Lockally\SDK\Model\Contact**](../Model/Contact.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listContacts()`

```php
listContacts($q, $type, $department, $status, $source): \Lockally\SDK\Model\ListContacts200Response
```

List contacts

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$q = 'q_example'; // string | Free-text search across name, email, company
$type = 'type_example'; // string | Filter by contact_type
$department = 'department_example'; // string | Filter by department
$status = 'status_example'; // string | Filter by status
$source = 'source_example'; // string | Filter by source

try {
    $result = $apiInstance->listContacts($q, $type, $department, $status, $source);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactsApi->listContacts: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **q** | **string**| Free-text search across name, email, company | [optional] |
| **type** | **string**| Filter by contact_type | [optional] |
| **department** | **string**| Filter by department | [optional] |
| **status** | **string**| Filter by status | [optional] |
| **source** | **string**| Filter by source | [optional] |

### Return type

[**\Lockally\SDK\Model\ListContacts200Response**](../Model/ListContacts200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateContact()`

```php
updateContact($id, $update_contact_request): \Lockally\SDK\Model\Contact
```

Update a contact

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$update_contact_request = new \Lockally\SDK\Model\UpdateContactRequest(); // \Lockally\SDK\Model\UpdateContactRequest

try {
    $result = $apiInstance->updateContact($id, $update_contact_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactsApi->updateContact: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_contact_request** | [**\Lockally\SDK\Model\UpdateContactRequest**](../Model/UpdateContactRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Contact**](../Model/Contact.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `upsertExternalContact()`

```php
upsertExternalContact($system, $external_id, $external_contact_input): \Lockally\SDK\Model\Contact
```

Create or update a contact by its id in another system

Idempotent: the path is the identity, so sending the same request twice cannot create a second contact, and you never need to store our id. Returns 201 when the contact was created and 200 when it already existed. The body is the full representation: a field you leave out is cleared. Email is an ordinary attribute, not a key, so changing it updates the same contact. `mailboxes:write` is also accepted.

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$system = 'system_example'; // string | Your label for the system the record comes from, for example `salesforce`, `hubspot` or `odoo`. 1 to 64 characters: lowercase letters, digits, dot, underscore or hyphen (upper case is folded).
$external_id = 'external_id_example'; // string | The record's id in that system, kept exactly as given (case matters). 1 to 255 characters, no spaces. URL-encode it.
$external_contact_input = new \Lockally\SDK\Model\ExternalContactInput(); // \Lockally\SDK\Model\ExternalContactInput

try {
    $result = $apiInstance->upsertExternalContact($system, $external_id, $external_contact_input);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactsApi->upsertExternalContact: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **system** | **string**| Your label for the system the record comes from, for example &#x60;salesforce&#x60;, &#x60;hubspot&#x60; or &#x60;odoo&#x60;. 1 to 64 characters: lowercase letters, digits, dot, underscore or hyphen (upper case is folded). | |
| **external_id** | **string**| The record&#39;s id in that system, kept exactly as given (case matters). 1 to 255 characters, no spaces. URL-encode it. | |
| **external_contact_input** | [**\Lockally\SDK\Model\ExternalContactInput**](../Model/ExternalContactInput.md)|  | |

### Return type

[**\Lockally\SDK\Model\Contact**](../Model/Contact.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
