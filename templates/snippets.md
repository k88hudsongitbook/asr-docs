# Snippets

The snippets template shows up fixed to the bottom of the New Tab Page.

![Screenshot of the new tab page snippet](../assets/snippet-example.png)

## Fields

The following fields are configurable via the `content` property of message definitions. For more comprehensive technical documentation

* `title` : *string PlainText* – A bold title displayed before the body `text`.
* `text` : *string [RichText](../api/template-fields.md#richtext-and-richlink), required* – Main body text of snippet. See [Rich Text documentation](../api/template-fields.md#richtext-and-richlink) for more information about adding links and other rich text features.
* `icon` : *string Url* – Snippet icon. 64x64px. SVG or PNG preferred.
* `button_label` : *string PlainText* – Text for a button next to main snippet text that links to button_url. Requires `button_url` or `button_action`.
* `button_url` : *string Url* – A url for a button, if one exists.
* `button_action` : *object [SpecialAction](../api/special-actions.md)* – An special action that the button triggers. See [Special Action documentation](../api/special-actions.md) for more information about what actions are available and how to format them.
* `button_color` : *string Color* – The text color of the button. It should be a valid CSS color including the leading `#`.
* `button_background_color` : *string Color* – The background color of the button. It should be a valid CSS color including the leading `#`.
* `tall` : *boolean* – To be used by fundraising only, increases height to roughly 120px. Defaults to false.
* `links` : *object{[RichLink]((../api/template-fields.md#richtext-and-richlink))}* – An object containing references to `RichLink`s for use in the `text` field. See [Rich Link documentation](../api/template-fields.md#richtext-and-richlink) for more information.
