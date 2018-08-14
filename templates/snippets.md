# Snippets

The snippets template shows up fixed to the bottom of the New Tab Page.

![Screenshot of the new tab page snippet](../assets/snippet-example.png)

## Fields

The following fields are configurable via the `content` property of message definitions. For more comprehensive technical documentation

* `title` : *string (plain text)* – A bold title displayed before the body `text`.
* `text` : *string (rich text), required* – Main body text of snippet. This is a `RichText` field, meaning a subset of HTML (i, b, u, strong, em, br) and links (defined via the `links` property)  are allowed.
* `icon` : *string (url)* – Snippet icon. 64x64px. SVG or PNG preferred.
* `button_label` : *string (plain text)* – Text for a button next to main snippet text that links to button_url. Requires `button_url` or `button_action`.
* `button_url` : *string (url)* – A url for a button, if one exists.
* `button_action` : *string* – An special action that the button triggers.
* `button_color` : *string (hex color)* – The text color of the button. It should be a valid CSS color including the leading `#`.
* `button_background_color` : *string (hex color)* – The background color of the button. It should be a valid CSS color including the leading `#`.
* `tall` : *boolean* – To be used by fundraising only, increases height to roughly 120px. Defaults to false.
* `links` : *Object* – An object containing references to `Links`, each of which have a `link_url` or `link_action` and a `metric` property. These can be referenced in `text` by key name.
