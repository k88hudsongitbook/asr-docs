# Special Actions

The following special actions are available to messages via the various buttons and link fields such as `link_action` and `button_action`. Special actions always have a `type` param, and may have a `data` param to pass additional information necessary for the action.

### INSTALL_ADDON_FROM_URL

```js
{
  type: "INSTALL_ADDON_FROM_URL",
  data: {url: "https://addons.mozilla.org/en-US/firefox/addon/ghostery"}
}
```

Installs a given addon given a URL.

data params:
* `url` : *string (url)* – The URL pointing to the addon


### OPEN_PRIVATE_BROWSER_WINDOW",

```js
{type: "OPEN_PRIVATE_BROWSER_WINDOW",}
```

Opens a new window with private browsing.

data params:: none

### OPEN_ABOUT_PAGE

```js
{
  type: "OPEN_ABOUT_PAGE",
  data: {url: "preferences"}
}
```

Opens an about page such as about:preferences.

data params:
*  `page` : *string* – The URL of the about page without an about: prefix, e.g. `"preferences"` for about:preferences
