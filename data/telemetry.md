# Telemetry in ASR

By default, telemetry is collected for impressions and various kinds of user interactions in AS Router. The data available to you depends on the type of message and the level of privacy protection required for your content.

This is an overview of the types of pings available to all templates:

### Impression ping

This reports the impression of Activity Stream Router.

```js
{
  "client_id": "n/a",
  "action": ["snippets_user_event" | "onboarding_user_event"],
  "impression_id": "{005deed0-e3e4-4c02-a041-17405fd703f6}",
  "source": "pocket",
  "addon_version": "20180710100040",
  "locale": "en-US",
  "source": "NEWTAB_FOOTER_BAR",
  "message_id": "some_snippet_id",
  "event": "IMPRESSION"
}
```

### Targeting error pings

This is triggered when an error has occurred when parsing/evaluating a JEXL targeting string in a message.

```js
{
  "client_id": "n/a",
  "action": "asrouter_undesired_event",
  "addon_version": "20180710100040",
  "impression_id": "{005deed0-e3e4-4c02-a041-17405fd703f6}",
  "locale": "en-US",
  "message_id": "some_message_id",
  "event": "TARGETING_EXPRESSION_ERROR",
  "value": ["MALFORMED_EXPRESSION" | "OTHER_ERROR"]
}
```

### User interaction pings

This reports user interactions with ASR messages. Please refer to the documentation for individual [Templates](../templates/templates/md) to see a more detailed list of user interaction pings available in those templates.

```js
{
  "client_id": "n/a",
  "action": ["snippets_user_event" | "onboarding_user_event"],
  "addon_version": "20180710100040",
  "impression_id": "{005deed0-e3e4-4c02-a041-17405fd703f6}",
  "locale": "en-US",
  "source": "NEWTAB_FOOTER_BAR",
  "message_id": "some_snippet_id",
  "event": ["CLICK_BUTTION" | "BLOCK" | ...]
}
```
