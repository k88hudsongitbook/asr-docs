# Onboarding

The onboarding template is a takeover of the new tab page and has space for three messages at once:

![Screenshot of the onboarding overlay](../assets/onboarding-example.png)

Note that for the onboarding template, **each message maps to a single panel, not the entire overlay**.

## Fields

The following fields are configurable via the `content` property of message definitions.

{% hint style='info' %}
To learn more about how to use and format special field types like `RichText` and `SpecialAction`, click on type definition next to the field name to see more documentation.
{% endhint %}

* `title` : *string PlainText, required* – A bold title displayed before the body `text`.
* `text` : *string [RichText](../api/template-fields.md#richtext-and-richlink), required* – Main body text of snippet.
* `icon` : *string OnboardingIcon* – An identifier for one of the implemented onboarding icons e.g. `addons`. Icons are 240px x 200px.
* `button_label` : *string PlainText* – Text for the button at the bottom of the card.
* `button_action` : *object [SpecialAction](../api/special-actions.md)* – An special action that the button triggers.

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
  "event": "CLICK_BUTTION"
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
