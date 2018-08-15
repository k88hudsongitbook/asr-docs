
### Targeting

For a more in-depth explanation of JEXL syntax you can read the [Normady project docs](https://normandy.readthedocs.io/en/stable/user/filters.html#jexl-basics).

Currently we expose the following targeting attributes that can be used by messages:

Name | Type | Example value | Description
---  | ---  | ---           | ---
`addonsInfo` | `Object` | [example below](#addonsinfo-example) | Information about the addons the user has installed
`devToolsOpenedCount` | `Integer` | Number of usages of the web console or scratchpad
`hasFxAccount` | `Boolean` | `true` | Does the user have a firefox account
`isDefaultBrowser` | `Boolean` or `null` | Is Firefox the user's default browser? If we could not determine the default browser, this value is `null`
`profileAgeCreated` | Number | `1522843725924` | Profile creation timestamp
`profileAgeReset` | `Number` or `undefined` | `1522843725924` | When (if) the profile was reset
`searchEngines` | `Object` | [example below](#searchengines-example) | Information about the current and available search engines

#### addonsInfo Example

```javascript
{
  "addons": {
    ...
    "activity-stream@mozilla.org": {
      "version": "2018.07.06.1113-783442c0",
      "type": "extension",
      "isSystem": true,
      "isWebExtension": false,
      "name": "Activity Stream",
      "userDisabled": false,
      "installDate": "2018-03-10T03:41:06.000Z"
    }
  },
  "isFullData": true
}
```

#### searchEngines Example

```javascript
{
  "searchEngines": {
    "current": "google",
    "installed": ["google", "amazondotcom", "duckduckgo"]
  }
}
```

#### Usage
A message needs to contain the `targeting` property (JEXL string) which is evaluated against the provided attributes.
Examples:

```javascript
{
  "id": "7864",
  "content": {...},
  // simple equality check
  "targeting": "hasFxAccount == true"
}

{
  "id": "7865",
  "content": {...},
  // using JEXL transforms and combining two attributes
  "targeting": "hasFxAccount == true && profileAgeCreated > '2018-01-07'|date"
}

{
  "id": "7866",
  "content": {...},
  // targeting addon information
  "targeting": "addonsInfo.addons['activity-stream@mozilla.org'].name == 'Activity Stream'"
}
```
