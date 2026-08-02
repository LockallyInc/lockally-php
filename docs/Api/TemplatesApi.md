# Lockally\SDK\TemplatesApi

Reusable email templates with {{variable}} substitution

All URIs are relative to https://api.lockally.com, except if the operation defines another base path.

| Method | HTTP request | Description |
| ------------- | ------------- | ------------- |
| [**v1TemplatesGet()**](TemplatesApi.md#v1TemplatesGet) | **GET** /v1/templates | List templates |
| [**v1TemplatesIdDelete()**](TemplatesApi.md#v1TemplatesIdDelete) | **DELETE** /v1/templates/{id} | Delete a template |
| [**v1TemplatesIdGet()**](TemplatesApi.md#v1TemplatesIdGet) | **GET** /v1/templates/{id} | Get a template |
| [**v1TemplatesIdPut()**](TemplatesApi.md#v1TemplatesIdPut) | **PUT** /v1/templates/{id} | Update a template |
| [**v1TemplatesPost()**](TemplatesApi.md#v1TemplatesPost) | **POST** /v1/templates | Create a template |


## `v1TemplatesGet()`

```php
v1TemplatesGet(): \Lockally\SDK\Model\V1TemplatesGet200Response
```

List templates

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\TemplatesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);

try {
    $result = $apiInstance->v1TemplatesGet();
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TemplatesApi->v1TemplatesGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**\Lockally\SDK\Model\V1TemplatesGet200Response**](../Model/V1TemplatesGet200Response.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1TemplatesIdDelete()`

```php
v1TemplatesIdDelete($id)
```

Delete a template

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\TemplatesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $apiInstance->v1TemplatesIdDelete($id);
} catch (Exception $e) {
    echo 'Exception when calling TemplatesApi->v1TemplatesIdDelete: ', $e->getMessage(), PHP_EOL;
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

## `v1TemplatesIdGet()`

```php
v1TemplatesIdGet($id): \Lockally\SDK\Model\Template
```

Get a template

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\TemplatesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string

try {
    $result = $apiInstance->v1TemplatesIdGet($id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TemplatesApi->v1TemplatesIdGet: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |

### Return type

[**\Lockally\SDK\Model\Template**](../Model/Template.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1TemplatesIdPut()`

```php
v1TemplatesIdPut($id, $template_input): \Lockally\SDK\Model\Template
```

Update a template

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\TemplatesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$id = 'id_example'; // string
$template_input = new \Lockally\SDK\Model\TemplateInput(); // \Lockally\SDK\Model\TemplateInput

try {
    $result = $apiInstance->v1TemplatesIdPut($id, $template_input);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TemplatesApi->v1TemplatesIdPut: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **id** | **string**|  | |
| **template_input** | [**\Lockally\SDK\Model\TemplateInput**](../Model/TemplateInput.md)|  | |

### Return type

[**\Lockally\SDK\Model\Template**](../Model/Template.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)

## `v1TemplatesPost()`

```php
v1TemplatesPost($template_input): \Lockally\SDK\Model\Template
```

Create a template

### Example

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');


// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\TemplatesApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$template_input = new \Lockally\SDK\Model\TemplateInput(); // \Lockally\SDK\Model\TemplateInput

try {
    $result = $apiInstance->v1TemplatesPost($template_input);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling TemplatesApi->v1TemplatesPost: ', $e->getMessage(), PHP_EOL;
}
```

### Parameters

| Name | Type | Description  | Notes |
| ------------- | ------------- | ------------- | ------------- |
| **template_input** | [**\Lockally\SDK\Model\TemplateInput**](../Model/TemplateInput.md)|  | |

### Return type

[**\Lockally\SDK\Model\Template**](../Model/Template.md)

### Authorization

[bearerAuth](../../README.md#bearerAuth)

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`, `application/problem+json`

[[Back to top]](#) [[Back to API list]](../../README.md#endpoints)
[[Back to Model list]](../../README.md#models)
[[Back to README]](../../README.md)
