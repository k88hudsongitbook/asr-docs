# Template Field Types

## RichText and RichLink

Template fields that are defined as `RichText` allow both a subset of HTML (i, b, u, strong, em, br) as well custom links defined via a `links` property. Take a look at the following example, where the `text` field is a `RichText` type field:

```js
{
  "content": {
    "text": "Hello! Visit <homepage>mozilla.org</homepage> and change some <aboutprefs>prefs</aboutprefs>!"
    "links": {
      "homepage": {"link_url": "https://mozilla.org"},
      "aboutprefs": {"link_action": {"type": "OPEN_ABOUT_PAGE", "data": {"page": "preferences"}}},
    }
  }
}
```

Each property defined in `links` is a `RichLink` available to the `RichText` field via an html-link syntax. `RichLink`s can either define a `link_url`, which is a regular external URL, or a a `link_action`, which is a special action such as opening about:preferences or triggering something in the Firefox UI. A complete list of implemented special actions can be found the in the [Special Actions](./special-actions.md) documentation.
