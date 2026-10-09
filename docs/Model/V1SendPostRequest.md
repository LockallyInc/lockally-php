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
**reply_to** | **string** | Where replies go. REQUIRED when &#x60;from&#x60; has no mailbox behind it, since a reply there would be delivered nowhere. A &#x60;Reply-To&#x60; entry in &#x60;headers&#x60; satisfies the same rule. The named form &#x60;Acme Support &lt;a@b.com&gt;&#x60; is also accepted. | [optional]
**reply_to_name** | **string** | Display name shown on &#x60;Reply-To&#x60;, e.g. &#x60;Acme Support&#x60;. Ignored without &#x60;reply_to&#x60;. Encoded and quoted for you, so accents, commas and quotes are all safe. | [optional]
**unsubscribe** | **bool** | Mark as opt-in/broadcast: skips suppressed recipients and adds a managed one-click List-Unsubscribe header. | [optional]
**template_id** | **string** | Render subject/text/html from a stored template (GET /v1/templates). Mutually exclusive with inline subject/text/html. | [optional]
**variables** | **array<string,string>** | Values substituted into the template&#39;s {{variable}} placeholders. | [optional]
**send_at** | **\DateTime** | Schedule delivery for a future RFC3339 time (≤ 30 days out). Omit or past &#x3D; send now. Cancel with DELETE /v1/messages/{id} while scheduled. | [optional]
**attachments** | [**\Lockally\SDK\Model\V1SendPostRequestAttachmentsInner[]**](V1SendPostRequestAttachmentsInner.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
