# Onboarding

The onboarding template is a takeover of the new tab page and has space for three messages at once:

![Screenshot of the onboarding](../assets/onboarding-example.png)

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
