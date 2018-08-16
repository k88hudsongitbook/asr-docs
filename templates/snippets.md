# Snippets

The snippets template shows up fixed to the bottom of the New Tab Page.

![Screenshot of the new tab page snippet](../assets/snippet-example.png)

## Fields

The following fields are configurable via the `content` property of message definitions.

{% hint style='info' %}
To learn more about how to use and format special field types like `RichText` and `SpecialAction`, click on type definition next to the field name to see more documentation.
{% endhint %}

* `title` : *string [PlainText](../api/template-fields.md#plaintext)* – A bold title displayed before the body `text`.
* `text` : *string [RichText](../api/template-fields.md#richtext-and-richlink), required* – Main body text of snippet.
* `icon` : *string Url* – Snippet icon. 64x64px. SVG or PNG preferred.
* `button_label` : *string PlainText* – Text for a button next to main snippet text.
* `button_url` : *string Url* – A url for the button to link to.
* `button_action` : *object [SpecialAction](../api/special-actions.md)* – An special action that the button triggers.
* `button_color` : *string Color* – The text color of the button. It should be a valid CSS color including the leading `#`.
* `button_background_color` : *string Color* – The background color of the button. It should be a valid CSS color including the leading `#`.
* `tall` : *boolean* – To be used by fundraising only, increases height to roughly 120px. Defaults to false.
* `links` : *object{[RichLink](../api/template-fields.md#richtext-and-richlink)}* – An object containing references to `RichLink`s for use in the `text` field.

## User Interaction Telemetry

The following user interactions are instrumented in this template, in addition to the [universally available telemetry](../data/telemetry.md):

### CLICK_BUTTON

The user has clicked the button.

```js
{
  "client_id": "n/a",
  "action": "snippets_user_event",
  "addon_version": "20180710100040",
  "impression_id": "{005deed0-e3e4-4c02-a041-17405fd703f6}",
  "locale": "en-US",
  "source": "NEWTAB_FOOTER_BAR",
  "message_id": "some_snippet_id",
  "event": "CLICK_BUTTION",
}
```

### CLICK_BUTTON {CUSTOM}

A use has clicked a custom link defined in the `links` property. If a custom `metric` value was supplied in the `links` property, it will be included in the `value` field.

For example, where the link definition is `{url: "foo.com", metric: ""my_custom_metric_id"}`:

```js
{
  "client_id": "n/a",
  "action": "snippets_user_event",
  "addon_version": "20180710100040",
  "impression_id": "{005deed0-e3e4-4c02-a041-17405fd703f6}",
  "locale": "en-US",
  "source": "NEWTAB_FOOTER_BAR",
  "message_id": "some_snippet_id",
  "event": "CLICK_BUTTION",
  "value": "my_custom_metric_id"
}
```

### BLOCK

The user has closed the snippet via the top corner "x" button.

```js
{
  "client_id": "n/a",
  "action": "snippets_user_event",
  "addon_version": "20180710100040",
  "impression_id": "{005deed0-e3e4-4c02-a041-17405fd703f6}",
  "locale": "en-US",
  "source": "NEWTAB_FOOTER_BAR",
  "message_id": "some_snippet_id",
  "event": "CLICK_BUTTION"
}
```
