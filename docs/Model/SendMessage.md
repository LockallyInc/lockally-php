# SendMessage

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**from** | **string** | Sender address, alone or as &#x60;Acme Orders &lt;orders@acme.com&gt;&#x60;. |
**from_name** | **string** | Display name shown next to &#x60;from&#x60;. Must match a name given in &#x60;from&#x60;. Cannot contain &#x60;@&#x60; or control characters. | [optional]
**to** | **string[]** |  |
**cc** | **string[]** |  | [optional]
**bcc** | **string[]** |  | [optional]
**subject** | **string** |  | [optional]
**text** | **string** |  | [optional]
**html** | **string** |  | [optional]
**headers** | **array<string,string>** |  | [optional]
**reply_to** | **string** | Where replies go. Required when &#x60;from&#x60; has no mailbox behind it. The named form &#x60;Acme Support &lt;a@b.com&gt;&#x60; is also accepted. | [optional]
**reply_to_name** | **string** | Display name shown on &#x60;Reply-To&#x60;. Ignored without &#x60;reply_to&#x60;. | [optional]
**unsubscribe** | **bool** |  | [optional]
**template_id** | **string** |  | [optional]
**variables** | **array<string,string>** |  | [optional]
**send_at** | **\DateTime** |  | [optional]
**attachments** | [**\Lockally\SDK\Model\SendEmailRequestAttachmentsInner[]**](SendEmailRequestAttachmentsInner.md) |  | [optional]

[[Back to Model list]](../../README.md#models) [[Back to API list]](../../README.md#endpoints) [[Back to README]](../../README.md)
