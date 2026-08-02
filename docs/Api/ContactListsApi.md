# Lockally\SDK\ContactListsApi



All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**addContactListMember()**](ContactListsApi.md#addContactListMember) | **POST** /v1/contact-lists/{id}/members | Add a member to a contact list |
| [**createContactList()**](ContactListsApi.md#createContactList) | **POST** /v1/contact-lists | Create a contact list |
| [**deleteContactList()**](ContactListsApi.md#deleteContactList) | **DELETE** /v1/contact-lists/{id} | Delete a contact list |
| [**getContactList()**](ContactListsApi.md#getContactList) | **GET** /v1/contact-lists/{id} | Get a contact list with members |
| [**listContactLists()**](ContactListsApi.md#listContactLists) | **GET** /v1/contact-lists | List contact lists |
| [**removeContactListMember()**](ContactListsApi.md#removeContactListMember) | **DELETE** /v1/contact-lists/{id}/members/{contactId} | Remove a member from a contact list |
| [**updateContactList()**](ContactListsApi.md#updateContactList) | **PATCH** /v1/contact-lists/{id} | Update a contact list |


## `addContactListMember()`

```php
addContactListMember($id, $add_contact_list_member_request)
```

Add a member to a contact list

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$add_contact_list_member_request = new \Lockally\SDK\Model\AddContactListMemberRequest(); // \Lockally\SDK\Model\AddContactListMemberRequest

try {
    $apiInstance->addContactListMember($id, $add_contact_list_member_request);
} catch (Exception $e) {
    echo 'Exception when calling ContactListsApi->addContactListMember: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **add_contact_list_member_request** | [**\Lockally\SDK\Model\AddContactListMemberRequest**](../Model/AddContactListMemberRequest.md)|  | |

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

## `createContactList()`

```php
createContactList($create_contact_list_request): \Lockally\SDK\Model\ContactList
```

Create a contact list

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_contact_list_request = new \Lockally\SDK\Model\CreateContactListRequest(); // \Lockally\SDK\Model\CreateContactListRequest

try {
    $result = $apiInstance->createContactList($create_contact_list_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactListsApi->createContactList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_contact_list_request** | [**\Lockally\SDK\Model\CreateContactListRequest**](../Model/CreateContactListRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\ContactList**](../Model/ContactList.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteContactList()`

```php
deleteContactList($id)
```

Delete a contact list

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->deleteContactList($id);
} catch (Exception $e) {
    echo 'Exception when calling ContactListsApi->deleteContactList: ', $e->getMessage(), PHP_EOL;
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

## `getContactList()`

```php
getContactList($id): \Lockally\SDK\Model\GetContactList200Response
```

Get a contact list with members

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->getContactList($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactListsApi->getContactList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\GetContactList200Response**](../Model/GetContactList200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listContactLists()`

```php
listContactLists(): \Lockally\SDK\Model\ListContactLists200Response
```

List contact lists

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listContactLists();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactListsApi->listContactLists: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\ListContactLists200Response**](../Model/ListContactLists200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `removeContactListMember()`

```php
removeContactListMember($id, $contact_id)
```

Remove a member from a contact list

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$contact_id = 'contact_id_example'; // string

try {
    $apiInstance->removeContactListMember($id, $contact_id);
} catch (Exception $e) {
    echo 'Exception when calling ContactListsApi->removeContactListMember: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **contact_id** | **string**|  | |

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

## `updateContactList()`

```php
updateContactList($id, $update_contact_list_request): \Lockally\SDK\Model\ContactList
```

Update a contact list

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\ContactListsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$update_contact_list_request = new \Lockally\SDK\Model\UpdateContactListRequest(); // \Lockally\SDK\Model\UpdateContactListRequest

try {
    $result = $apiInstance->updateContactList($id, $update_contact_list_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ContactListsApi->updateContactList: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_contact_list_request** | [**\Lockally\SDK\Model\UpdateContactListRequest**](../Model/UpdateContactListRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\ContactList**](../Model/ContactList.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
