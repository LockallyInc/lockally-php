# V1SendPostRequest

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**from** | **string** |  |
**to** | **string[]** |  |
**cc** | **string[]** |  | [optional]
**bcc** | **string[]** |  | [optional]
**subject** | **string** |  | [optional]
**text** | **string** | Plain-text body. Required if &#x60;html&#x60; is absent. | [optional]
**html** | **string** | HTML body. Required if &#x60;text&#x60; is absent. | [optional]
**headers** | **array<string,string>** |  | [optional]
**unsubscribe** | **bool** | Mark as opt-in/broadcast: skips suppressed recipients and adds a managed one-click List-Unsubscribe header. | [optional]
**template_id** | **string** | Render subject/text/html from a stored template (GET /v1/templates). Mutually exclusive with inline subject/text/html. | [optional]
**variables** | **array<string,string>** | Values substituted into the template&#39;s {{variable}} placeholders. | [optional]
**send_at** | **\DateTime** | Schedule delivery for a future RFC3339 time (≤ 30 days out). Omit or past &#x3D; send now. Cancel with DELETE /v1/messages/{id} while scheduled. | [optional]
**attachments** | [**\Lockally\SDK\Model\V1SendPostRequestAttachmentsInner[]**](V1SendPostRequestAttachmentsInner.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
