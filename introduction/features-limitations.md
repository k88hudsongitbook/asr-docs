# Features and Limitations

In its current form, AS Router is designed to communicate with users via a standard message format and a set of UI templates. Those messages can contain targeting information to determine to whom messages are shown and when they can appear.

Some telemetry can be collected about these messages and how users interact with them. As with other telemetry in Firefox, the extent to which telemetry can be collected and analysed depends on the **sensitivity/risk of the targeting information and content** of the message.

## UI

Messages should follow our general design guidelines and must use one of our existing templates. Anything exposed by the template API may be customized on a per-message basis (this includes things like button colours, button labels, etc.) but messages may **not** contain custom CSS or javascript.

## Update cycles

If delivered by a **Remote Provider** such as Snippets, messages may be updated and changed between release cycles.

If delivered by a **Local Provider** such as Onboarding, messages must ride the Firefox release trains.

New targeting, telemetry, and custom user actions must ride the Firefox release trains. Template changes are generally expected to ride trains, but in urgent circumstances can be requested to update

## Localization

Messages from Remote Providers can be delivered to different locales via server-side filtering on the remote endpoint or with client-side targeting.

Messages that are landed in Firefox can be localized by Firefox's internal localization team, but must be finalized early enough in the release cycle for localizatio to be completed.

## Channels

Messages may be released to any combination of any Firefox channels, including Nightly, Beta, and Release.

## Targeting

A wide range of targeting capabilities are available to determine when and to whom messages should be shown. Please refer to the targeting section of this documentation.

