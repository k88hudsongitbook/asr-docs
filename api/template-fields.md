# Template Field Types

## RichText and RichLink

Template fields that are defined as `RichText` allow both a subset of HTML (i, b, u, strong, em, br) as well custom links defined via a `links` property.

If a tag that is not on the allowed is used, the text content will be extracted and displayed.

Grouping multiple allowed elements is not possible, only the first level will be used: `<u><b>text</b></u>` will be interpreted as `<u>text</u>`.

Take a look at the following example, where the `text` field is a `RichText` type field:

```js
{
  "content": {
    "text": "Hello! Visit <homepage>mozilla.org</homepage> and change some <aboutprefs>prefs</aboutprefs>!"
    "links": {
      "homepage": {
        "link_url": "https://mozilla.org",
        "metric": "homepage_click"
      },
      "aboutprefs": {
        "link_action": {"type": "OPEN_ABOUT_PAGE", "data": {"page": "preferences"}}
      }
    }
  }
}
```

Each property defined in `links` is a `RichLink` available to the `RichText` field via an html-link syntax. `RichLink`s must define one of the following properties:

* `link_url` : *string Url* – a regular external URL.
* `link_action` : *object [SpecialAction](./special-actions.md)* – a special action such as opening about:preferences or triggering something in the Firefox UI. A complete list of implemented special actions can be found the in the [Special Actions](./special-actions.md) documentation.

If you need a special flag to collect metrics for engagement with a link, you can also add the following property:

* `metric` : *string* – this string will be included in event telemetry for when a user clicks the link.
