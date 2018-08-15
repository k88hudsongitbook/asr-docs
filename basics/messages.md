## Messages

An "message", or `ASRouterMessage`, is the smallest individual unit of content defined by any provider. An example of this would be an individual snippet, an individual pane in an onboarding display, or a particular CFR message.

### Overview

`ASRouterMessage`s be JSON or javascript objects that are serializable to JSON. Here is an example:

```javascript
{
  id: "ONBOARDING_1",
  template: "simple_snippet",
  content: {
    title: "Find it faster",
    body: "Access all of your favorite search engines with a click. Search the whole Web or just one website from the search box."
  },
  targeting: "hasFxAccount && !addonsInfo.addons['activity-stream@mozilla.org']",
  frequency: {
    lifetime: 20,
    custom: [{period: "daily", cap: 5}, {period: 3600000, cap: 1}]
  }
}
```

`ASRouterMessages` may have the following properties, some of which are required. Details of each property follows this table:

Field name | Type     | Required
---        | ---      | ---
`id`       | `string` | Yes
`template` | `string` | Yes
`publish_start` | `Date` | No
`publish_end` | `Date` | No
`content` | `object` | Yes
`bundled` | `integer` | No
`order` | `integer` | No
`campaign` | `string` | No
`targeting` | `string` `JEXL` | No
`trigger` | `string` | No
`frequency` | `object` | No
`frequency.lifetime` | `integer` | No
`frequency.custom` | `array` | No

### id
A unique identifier for the message that should not conflict with any other previous message.

e.g. `ONBOARDING_1`

### template
An id matching an existing Activity Stream Router template

[See example](https://github.com/mozilla/activity-stream/blob/33669c67c2269078a6d3d6d324fb48175d98f634/system-addon/content-src/message-center/templates/SimpleSnippet.jsx)

### publish_start
When to start showing the message

e.g. `1524474850876`

### content
An object containing all variables/props to be rendered in the template. Subset of allowed tags detailed below.

[See example below](#html-subset)


### bundled
The number of messages of the same template this one should be shown with.


#### Bundled Message example
The following 2 messages have a `bundled` property, indicating that they should be shown together, since they have the same template. The number `2` indicates that this message should be shown in a bundle of 2 messages of the same template. The order property defines that ONBOARDING_2 should be shown after ONBOARDING_3 in the bundle.
```javascript
{
  id: "ONBOARDING_2",
  template: "onboarding",
  bundled: 2,
  order: 2,
  content: {
    title: "Private Browsing",
    body: "Browse by yourself. Private Browsing with Tracking Protection blocks online trackers that follow you around the web."
  },
  targeting: "",
  trigger: "firstRun"
}
{
  id: "ONBOARDING_3",
  template: "onboarding",
  bundled: 2,
  order: 1,
  content: {
    title: "Find it faster",
    body: "Access all of your favorite search engines with a click. Search the whole Web or just one website from the search box."
  },
  targeting: "",
  trigger: "firstRun"
}
```

### order
If bundled with other messages of the same template, which order should this one be placed in? Defaults to 0 if no order is desired

[See example above](#a-bundled-message-example)

### campaign
Campaign id that the message belongs to.

e.g. `RustWebAssembly`

### targeting
A [JEXL expression](http://normandy.readthedocs.io/en/latest/user/filter_expressions.html#jexl-basics) with all targeting information needed in order to decide if the message is shown | Not yet implemented, [Examples](#targeting-attributes)

### trigger
An event or condition upon which the message will be immediately shown. This can be combined with `targeting`. Messages that define a trigger will not be shown during non-trigger-based passive message rotation.

### frequency
A definition for frequency cap information for the message

```
lifetime : integer
custom : Array<{cap, period}>
```

#### frequency.lifetime
The maximum number of lifetime impressions for the message.

#### frequency.custom
An array of frequency cap definition objects including `period`, a time period in milliseconds
and `cap`, a max number of impressions for that period.
