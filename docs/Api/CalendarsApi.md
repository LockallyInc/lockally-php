# Lockally\SDK\CalendarsApi

Calendars, events, members, policies, security, and integrations

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**addCalendarMember()**](CalendarsApi.md#addCalendarMember) | **POST** /v1/calendars/{id}/members | Add a member to a calendar |
| [**createCalendar()**](CalendarsApi.md#createCalendar) | **POST** /v1/calendars | Create a calendar |
| [**createCalendarEvent()**](CalendarsApi.md#createCalendarEvent) | **POST** /v1/calendars/{id}/events | Create an event in a calendar |
| [**createCalendarIntegration()**](CalendarsApi.md#createCalendarIntegration) | **POST** /v1/calendar-integrations | Create a calendar integration |
| [**deleteCalendar()**](CalendarsApi.md#deleteCalendar) | **DELETE** /v1/calendars/{id} | Delete a calendar |
| [**deleteCalendarEvent()**](CalendarsApi.md#deleteCalendarEvent) | **DELETE** /v1/calendars/{id}/events/{eventId} | Delete a calendar event |
| [**deleteCalendarIntegration()**](CalendarsApi.md#deleteCalendarIntegration) | **DELETE** /v1/calendar-integrations/{id} | Delete a calendar integration |
| [**getCalendar()**](CalendarsApi.md#getCalendar) | **GET** /v1/calendars/{id} | Get a calendar |
| [**getCalendarPolicies()**](CalendarsApi.md#getCalendarPolicies) | **GET** /v1/calendar-policies | Get calendar policies |
| [**getCalendarSecurity()**](CalendarsApi.md#getCalendarSecurity) | **GET** /v1/calendar-security | Get calendar security overview |
| [**listCalendarEvents()**](CalendarsApi.md#listCalendarEvents) | **GET** /v1/calendars/{id}/events | List events in a calendar |
| [**listCalendarIntegrations()**](CalendarsApi.md#listCalendarIntegrations) | **GET** /v1/calendar-integrations | List calendar integrations |
| [**listCalendarMembers()**](CalendarsApi.md#listCalendarMembers) | **GET** /v1/calendars/{id}/members | List calendar members |
| [**listCalendars()**](CalendarsApi.md#listCalendars) | **GET** /v1/calendars | List calendars |
| [**removeCalendarMember()**](CalendarsApi.md#removeCalendarMember) | **DELETE** /v1/calendars/{id}/members/{memberId} | Remove a member from a calendar |
| [**syncCalendarIntegration()**](CalendarsApi.md#syncCalendarIntegration) | **POST** /v1/calendar-integrations/{id}/sync | Trigger sync for a calendar integration |
| [**updateCalendar()**](CalendarsApi.md#updateCalendar) | **PATCH** /v1/calendars/{id} | Update a calendar |
| [**updateCalendarEvent()**](CalendarsApi.md#updateCalendarEvent) | **PATCH** /v1/calendars/{id}/events/{eventId} | Update a calendar event |
| [**updateCalendarIntegration()**](CalendarsApi.md#updateCalendarIntegration) | **PATCH** /v1/calendar-integrations/{id} | Update a calendar integration |
| [**updateCalendarMember()**](CalendarsApi.md#updateCalendarMember) | **PATCH** /v1/calendars/{id}/members/{memberId} | Update a calendar member&#39;s role |
| [**updateCalendarPolicies()**](CalendarsApi.md#updateCalendarPolicies) | **PATCH** /v1/calendar-policies | Update calendar policies |


## `addCalendarMember()`

```php
addCalendarMember($id, $add_calendar_member_request): \Lockally\SDK\Model\CalendarMember
```

Add a member to a calendar

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$add_calendar_member_request = new \Lockally\SDK\Model\AddCalendarMemberRequest(); // \Lockally\SDK\Model\AddCalendarMemberRequest

try {
    $result = $apiInstance->addCalendarMember($id, $add_calendar_member_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->addCalendarMember: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **add_calendar_member_request** | [**\Lockally\SDK\Model\AddCalendarMemberRequest**](../Model/AddCalendarMemberRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\CalendarMember**](../Model/CalendarMember.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createCalendar()`

```php
createCalendar($create_calendar_request): \Lockally\SDK\Model\Calendar
```

Create a calendar

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_calendar_request = new \Lockally\SDK\Model\CreateCalendarRequest(); // \Lockally\SDK\Model\CreateCalendarRequest

try {
    $result = $apiInstance->createCalendar($create_calendar_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->createCalendar: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_calendar_request** | [**\Lockally\SDK\Model\CreateCalendarRequest**](../Model/CreateCalendarRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Calendar**](../Model/Calendar.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createCalendarEvent()`

```php
createCalendarEvent($id, $create_calendar_event_request): \Lockally\SDK\Model\CalendarEvent
```

Create an event in a calendar

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$create_calendar_event_request = new \Lockally\SDK\Model\CreateCalendarEventRequest(); // \Lockally\SDK\Model\CreateCalendarEventRequest

try {
    $result = $apiInstance->createCalendarEvent($id, $create_calendar_event_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->createCalendarEvent: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **create_calendar_event_request** | [**\Lockally\SDK\Model\CreateCalendarEventRequest**](../Model/CreateCalendarEventRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\CalendarEvent**](../Model/CalendarEvent.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `createCalendarIntegration()`

```php
createCalendarIntegration($create_calendar_integration_request): \Lockally\SDK\Model\CalendarIntegration
```

Create a calendar integration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_calendar_integration_request = new \Lockally\SDK\Model\CreateCalendarIntegrationRequest(); // \Lockally\SDK\Model\CreateCalendarIntegrationRequest

try {
    $result = $apiInstance->createCalendarIntegration($create_calendar_integration_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->createCalendarIntegration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **create_calendar_integration_request** | [**\Lockally\SDK\Model\CreateCalendarIntegrationRequest**](../Model/CreateCalendarIntegrationRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\CalendarIntegration**](../Model/CalendarIntegration.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `deleteCalendar()`

```php
deleteCalendar($id)
```

Delete a calendar

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->deleteCalendar($id);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->deleteCalendar: ', $e->getMessage(), PHP_EOL;
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

## `deleteCalendarEvent()`

```php
deleteCalendarEvent($id, $event_id)
```

Delete a calendar event

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$event_id = 'event_id_example'; // string

try {
    $apiInstance->deleteCalendarEvent($id, $event_id);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->deleteCalendarEvent: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **event_id** | **string**|  | |

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

## `deleteCalendarIntegration()`

```php
deleteCalendarIntegration($id)
```

Delete a calendar integration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->deleteCalendarIntegration($id);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->deleteCalendarIntegration: ', $e->getMessage(), PHP_EOL;
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

## `getCalendar()`

```php
getCalendar($id): \Lockally\SDK\Model\Calendar
```

Get a calendar

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->getCalendar($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->getCalendar: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Calendar**](../Model/Calendar.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getCalendarPolicies()`

```php
getCalendarPolicies(): \Lockally\SDK\Model\CalendarPolicies
```

Get calendar policies

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getCalendarPolicies();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->getCalendarPolicies: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\CalendarPolicies**](../Model/CalendarPolicies.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `getCalendarSecurity()`

```php
getCalendarSecurity(): \Lockally\SDK\Model\GetCalendarSecurity200Response
```

Get calendar security overview

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->getCalendarSecurity();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->getCalendarSecurity: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\GetCalendarSecurity200Response**](../Model/GetCalendarSecurity200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listCalendarEvents()`

```php
listCalendarEvents($id, $from, $to): \Lockally\SDK\Model\ListCalendarEvents200Response
```

List events in a calendar

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$from = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime
$to = new \DateTime('2013-10-20T19:20:30+01:00'); // \DateTime

try {
    $result = $apiInstance->listCalendarEvents($id, $from, $to);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->listCalendarEvents: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **from** | **\DateTime**|  | [optional] |
| **to** | **\DateTime**|  | [optional] |

### Return type

[**\Lockally\SDK\Model\ListCalendarEvents200Response**](../Model/ListCalendarEvents200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listCalendarIntegrations()`

```php
listCalendarIntegrations(): \Lockally\SDK\Model\ListCalendarIntegrations200Response
```

List calendar integrations

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listCalendarIntegrations();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->listCalendarIntegrations: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\ListCalendarIntegrations200Response**](../Model/ListCalendarIntegrations200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listCalendarMembers()`

```php
listCalendarMembers($id): \Lockally\SDK\Model\ListCalendarMembers200Response
```

List calendar members

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->listCalendarMembers($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->listCalendarMembers: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\ListCalendarMembers200Response**](../Model/ListCalendarMembers200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `listCalendars()`

```php
listCalendars(): \Lockally\SDK\Model\ListCalendars200Response
```

List calendars

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->listCalendars();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->listCalendars: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\ListCalendars200Response**](../Model/ListCalendars200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `removeCalendarMember()`

```php
removeCalendarMember($id, $member_id)
```

Remove a member from a calendar

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$member_id = 'member_id_example'; // string

try {
    $apiInstance->removeCalendarMember($id, $member_id);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->removeCalendarMember: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **member_id** | **string**|  | |

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

## `syncCalendarIntegration()`

```php
syncCalendarIntegration($id): \Lockally\SDK\Model\CalendarIntegration
```

Trigger sync for a calendar integration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->syncCalendarIntegration($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->syncCalendarIntegration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\CalendarIntegration**](../Model/CalendarIntegration.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateCalendar()`

```php
updateCalendar($id, $update_calendar_request): \Lockally\SDK\Model\Calendar
```

Update a calendar

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$update_calendar_request = new \Lockally\SDK\Model\UpdateCalendarRequest(); // \Lockally\SDK\Model\UpdateCalendarRequest

try {
    $result = $apiInstance->updateCalendar($id, $update_calendar_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->updateCalendar: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_calendar_request** | [**\Lockally\SDK\Model\UpdateCalendarRequest**](../Model/UpdateCalendarRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\Calendar**](../Model/Calendar.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateCalendarEvent()`

```php
updateCalendarEvent($id, $event_id, $update_calendar_event_request): \Lockally\SDK\Model\CalendarEvent
```

Update a calendar event

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$event_id = 'event_id_example'; // string
$update_calendar_event_request = new \Lockally\SDK\Model\UpdateCalendarEventRequest(); // \Lockally\SDK\Model\UpdateCalendarEventRequest

try {
    $result = $apiInstance->updateCalendarEvent($id, $event_id, $update_calendar_event_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->updateCalendarEvent: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **event_id** | **string**|  | |
| **update_calendar_event_request** | [**\Lockally\SDK\Model\UpdateCalendarEventRequest**](../Model/UpdateCalendarEventRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\CalendarEvent**](../Model/CalendarEvent.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateCalendarIntegration()`

```php
updateCalendarIntegration($id, $update_calendar_integration_request): \Lockally\SDK\Model\CalendarIntegration
```

Update a calendar integration

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$update_calendar_integration_request = new \Lockally\SDK\Model\UpdateCalendarIntegrationRequest(); // \Lockally\SDK\Model\UpdateCalendarIntegrationRequest

try {
    $result = $apiInstance->updateCalendarIntegration($id, $update_calendar_integration_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->updateCalendarIntegration: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **update_calendar_integration_request** | [**\Lockally\SDK\Model\UpdateCalendarIntegrationRequest**](../Model/UpdateCalendarIntegrationRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\CalendarIntegration**](../Model/CalendarIntegration.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateCalendarMember()`

```php
updateCalendarMember($id, $member_id, $update_calendar_member_request): \Lockally\SDK\Model\CalendarMember
```

Update a calendar member's role

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$member_id = 'member_id_example'; // string
$update_calendar_member_request = new \Lockally\SDK\Model\UpdateCalendarMemberRequest(); // \Lockally\SDK\Model\UpdateCalendarMemberRequest

try {
    $result = $apiInstance->updateCalendarMember($id, $member_id, $update_calendar_member_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->updateCalendarMember: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **member_id** | **string**|  | |
| **update_calendar_member_request** | [**\Lockally\SDK\Model\UpdateCalendarMemberRequest**](../Model/UpdateCalendarMemberRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\CalendarMember**](../Model/CalendarMember.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `updateCalendarPolicies()`

```php
updateCalendarPolicies($update_calendar_policies_request): \Lockally\SDK\Model\CalendarPolicies
```

Update calendar policies

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\CalendarsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$update_calendar_policies_request = new \Lockally\SDK\Model\UpdateCalendarPoliciesRequest(); // \Lockally\SDK\Model\UpdateCalendarPoliciesRequest

try {
    $result = $apiInstance->updateCalendarPolicies($update_calendar_policies_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling CalendarsApi->updateCalendarPolicies: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **update_calendar_policies_request** | [**\Lockally\SDK\Model\UpdateCalendarPoliciesRequest**](../Model/UpdateCalendarPoliciesRequest.md)|  | |

### Return type

[**\Lockally\SDK\Model\CalendarPolicies**](../Model/CalendarPolicies.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
