---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Release Notes - 2026

## Release 2026.3

<figure><img src=".gitbook/assets/Release 2026.3.png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="169.2421875">Release 2026.3</th><th>2 June 2026</th></tr></thead><tbody><tr><td>iOS version</td><td>2.99.3</td></tr><tr><td>Android version</td><td>2.92.3</td></tr><tr><td>Jigx Builder</td><td>1.44.0</td></tr></tbody></table>

### <i class="fa-rocket-launch">:rocket-launch:</i> Announcement : Introducing JigxForms

**What  is JigxForms?** \
AI-powered forms. Built for the field. Ready anytime, anywhere.\
Create and submit powerful, customizable forms, directly from your phone.

<a href="https://jigx.com/products/jigx-for-acumatica/jigxforms/?utm_source=docs.jigx.com" class="button primary" data-icon="rocket-launch">Register now for JigxForms!  </a>

### Mobile Apps

#### New features & improvements

* Added support for **packages** - solutions composed inside other solutions. A jig can navigate into a package, execute its actions, with expression-resolved targets, and pass callback actions for the package to invoke back. The package property (target solution name) is available in the [action.go-to](https://docs.jigx.com/examples/readme/actions/go-to#accessing-a-jig-in-another-solution) and [execute.action](https://execute.actionhttps/docs.jigx.com/examples/readme/actions/execute-action#cross-solution-action-access). Package `onLoad`, `datasources`, and `@ctx.solution.*` state are scoped to the package. The app switcher now hides package, form, and data solutions, showing only real apps.
* **Solution title** available in expressions - The `=@ctx.solution.title` expression is now supported in YAML configurations, allowing you to reference the solution's display title (as defined in `index.jigx`) directly within your jigs. This follows the same pattern as other solution metadata properties such as `=@ctx.solution.name`, `=@ctx.solution.id`, and `=@ctx.solution.organizationId`. Use this expression wherever you need to dynamically display or reference the solution title, for example, in screen headers, labels, banners, or conditional logic, without hardcoding the title string into individual components.

#### Bug Fixes

* **Persistent file storage for media, signatures, and generated outputs** - Media picker selections, captured signatures, and generated PDFs and files are now written to permanent storage locations that survive cache purges, app restarts, and low-memory events. On iOS, media and signatures are saved to `Library/Application Support` (excluded from iCloud backup), and generated PDFs and files are saved to `Documents/Generated PDFs` and `Documents/Generated Files` respectively. On Android, outputs are directed to internal storage and the documents directory. A loading indicator is displayed in the media field while the background copy is in progress, keeping the experience responsive. This resolves a number of issues where files appeared to save successfully but were lost after the OS purged temporary or cache directories.
* Fixed an incorrect item height calculation in list widgets that caused list items to not properly fill the available container space. Items now render at the correct height regardless of screen size or the number of items in the list.
* Fixed an issue on the sign-in screen where the on-screen keyboard remained visible when entering the SSO flow from the email field, covering the SSO options modal and making it difficult or impossible to interact with. The keyboard is now dismissed before the SSO options modal opens, ensuring it is fully visible and accessible.
* Fixed an issue where `component.grid` rendered slowly on Android, with tiles appearing sequentially after the rest of the screen had already loaded. The per-tile entrance animation that triggered off-screen layer processing has been removed on both Android and iOS, so grid tiles now appear in a single frame and render consistently across platforms.
* Remove orphaned cached files during a full entity sync to prevent unbounded storage growth.
* Resolved issues affecting file uploads and downloads when using the Dynamic Data provider on unreliable network connections. File uploads and downloads now correctly transition to a Failed status when a network error occurs, instead of remaining indefinitely in an Uploading or Downloading state. Active file transfers on slow but functioning connections are no longer incorrectly cancelled by connection timeout checks during the transfer process.

### Components and jig types

#### New features & improvements

* [Web-view](https://docs.jigx.com/examples/readme/components/web-view) component - Add `allowInAppRedirect` option to `component.web-view`, when enabled, Jigx deeplinks navigate within the app, regular URLs open in an in-app browser, and other schemes delegate to the system.
* Added the `listHeader` property to [jig.list](https://jig.listhttps/docs.jigx.com/examples/readme/jig-types/jig_list), enabling fully configurable custom child components in the list header. This eliminates the need to use `jig.default` with `component.list` as a workaround for custom list header content, while maintaining the performance benefits of `jig.list`. The existing `header` /`jig-header` property remains reserved for configuring the hero header.

### Jigx Management

* Bug fixes, performance improvements, and usability improvements.

### Updates to Quick-Start sample solutions

<table><thead><tr><th width="146.08984375">Solution</th><th>Additions</th></tr></thead><tbody><tr><td>jigx-samples</td><td>List jig with listHeader</td></tr><tr><td> </td><td>List jig with listHeader &#x26; jig-header</td></tr><tr><td></td><td>Changed CSV data files to JSON files to upload to Management</td></tr></tbody></table>

## Release 2026.2

<figure><img src=".gitbook/assets/Release 2026.2.png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="169.2421875">Release 2026.2</th><th>22 May 2026</th></tr></thead><tbody><tr><td>iOS version</td><td>2.90.4</td></tr><tr><td>Android version</td><td>2.83.4</td></tr><tr><td>Jigx Builder</td><td>1.43.4</td></tr></tbody></table>

### <i class="fa-rocket-launch">:rocket-launch:</i> Announcement : Introducing JigxForms

**What  is JigxForms?** \
AI-powered forms. Built for the field. Ready anytime, anywhere.\
Create and submit powerful, customizable forms, directly from your phone.

<a href="https://jigx.com/products/jigx-for-acumatica/jigxforms/?utm_source=docs.jigx.com" class="button primary" data-icon="rocket-launch">Register now for JigxForms!  </a>

### Mobile Apps

#### Bug Fixes

* Fixed progressive performance degradation on Android.
* Resolved an issue where newly created users in existing or new organizations could see the “No Solution” screen in the mobile app, despite solutions being assigned correctly. This was caused by an update to the backend identity provider which introduced non-standard user IDs (GUIDs) for newly created users. This caused validation checks used during solution assignment to fail

### Actions

#### New features & improvements

* Add `page` property to [action.generate-pdf](https://docs.jigx.com/examples/readme/actions/generate-pdf) to control paper `size` (letter, legal, tabloid, a4, a3), `orientation` (portrait, landscape), custom dimensions (width/height in PDF points), and `margins` (uniform number or per-side object). Fix iOS PDF generation to paginate multi-page content correctly instead of producing a single oversized page.
* A new `onAppActivated` [event](https://docs.jigx.com/examples/readme/events) is available on solution and jig level, allowing you to define actions that automatically execute when the app returns to the foreground from the background or inactive state. This is useful for refreshing data or triggering syncs when a user returns to the app mid-session. Note that `onAppActivated` does not fire on initial app launch, only on subsequent foreground transitions.

### Builder

#### New features & improvements

* REST functions have been enhancement to allow the  `UseLocal:true` property to be used with secrets.
* [Index.jigx](https://docs.jigx.com/building-apps-with-jigx/ui/home-hub/index-settings) - You can now use the `bundleId` property in the `dependencies` section of the index.jigx file to restrict a solution to specific mobile app bundle IDs. This enhancement allows greater control over which branded or distributed mobile apps can load a solution. This enhancement is useful for managing solution availability across multiple branded mobile apps or deployment environments.

### Jigx Management

* Bug fixes, performance improvements, and usability improvements.

## Release 2026.1

<figure><img src=".gitbook/assets/Release 2026.1.png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="169.2421875">Release 2026.1</th><th>20 May 2026</th></tr></thead><tbody><tr><td>iOS version</td><td>2.80.0</td></tr><tr><td>Android version</td><td>2.73.0 </td></tr><tr><td>Jigx Builder</td><td>1.42.0</td></tr></tbody></table>

### <i class="fa-rocket-launch">:rocket-launch:</i> Announcement : Introducing JigxForms

**What  is JigxForms?** \
AI-powered forms. Built for the field. Ready anytime, anywhere.\
Create and submit powerful, customizable forms, directly from your phone.

<a href="https://jigx.com/products/jigx-for-acumatica/jigxforms/?utm_source=docs.jigx.com" class="button primary" data-icon="rocket-launch">Register now for JigxForms!  </a>

### Mobile Apps

#### **New features & improvements**

* All **input components** that support the `isRequired` property have been enhanced to provide a clearer visual indicator for mandatory fields. When `isRequired` is set to `true`, the field label now displays an _asterisk_ (\*) instead of the previous _(optional)_ text. This change brings the visual design in line with common UI standards and improves form clarity for users completing required information.

#### Bug Fixes

* Resolved an issue where resetting a list’s `amount.state` on a default jig did not work as expected. The state now resets correctly, ensuring consistent behavior when clearing or reinitializing list data.
* Fixed a backward compatibility issue with the `numberOfLines` property that caused display problems in swipeable lists. The UI now renders correctly, ensuring text truncation and layout behave as expected across both new and existing configurations.
* Fixed an issue where the `signature-field` did not respect the disabled configuration. Even when configured with `isDisabled: true`, the field remained interactive.
* Fixed an issue that caused signatures saved to dynamic files to display with a black background. Signatures now render with a white background in the app.
* Improved geolocation loading performance on Android 16, resolving an issue that caused slow load times.
* Improved continue logging alert wording and appearance.
* Fixed an issue where setting `isDisabled: true` on a `media-field` blocked all interaction, preventing users from viewing existing media. Tapping a disabled media field now opens the detail modal so existing media can be viewed. Add and delete actions remain blocked as expected.

### Components and jig types

#### New features & improvements

* [Banner](https://docs.jigx.com/examples/readme/components/banner) - The `component.banner` introduces a consistent and flexible way to display prominent, text-based messages directly within your Jigx screens. It standardizes how messages are presented with built-in styling, contextual icons, and optional actions for user interaction. Banners make it easy to communicate system states, important information, or contextual guidance in a visually distinct area of your app. Whether you’re confirming success, warning about an issue, or guiding users through next steps, Banners ensure critical messages stand out without disrupting the user flow. Banners can include actions such as Retry or Dismiss. Common use cases include:
  * _Error_ — “Something went wrong. Please try again.”
  * _Warning_ — “Changes not saved.”
  * _Success_ — “Your settings were updated successfully.”
  * _Informational Text_ — Highlight short messages or announcements that need visual emphasis within a section or card, such as updates, notices, or reminders.
* [Sections](https://docs.jigx.com/examples/readme/components/section) - The `component.section` has been enhanced to support `actions`, `icons` and `styling` on the section header, allowing you to add interactive options such as “Show More” directly within the section title area. This enhancement provides a smoother and more intuitive user experience, resulting in faster navigation and improved usability across your screens.
* Default [placeholder](https://docs.jigx.com/examples/readme/jig-types/common-jig-type-properties/placeholders) Enhancement **-** When configuring screens that use array-based data (such as lists or dropdown components), the app now displays a default placeholder whenever no data is available. If you prefer not to show a placeholder, you can control this by setting a when condition on the component so it only renders when data exists. When configuring screens that use array-based data (such as lists or dropdown components), the app now displays a default placeholder whenever no data is available. If you prefer not to show a placeholder, you can control this by setting a when condition on the component so it only renders when data exists.
* Enhanced lists to support multi-column layouts using the new `numberOfColumns` property, ideal for product catalogs, category menus, and compact dashboards. Multi-column layouts apply only to vertical lists and are supported exclusively in [component.product-item](https://docs.jigx.com/examples/readme/components/list/product-item) and [component.menu-item](https://docs.jigx.com/examples/readme/components/list/menu-item).
* [Menu-item](https://docs.jigx.com/examples/readme/components/list/menu-item) - Added a new list child component, the `menu-item` is a lightweight list-item designed for quick selection and navigation. It’s ideal for presenting categories, filters, or simple choices that guide you to the next screen or refine the data being displayed. Use a menu-item when you want users to tap an option to view related content, for example, selecting a project, choosing a day of the week, or filtering items by category.&#x20;
* [Header](https://docs.jigx.com/examples/readme/components/jig-header) - Introduced new `tiny` height option, providing greater flexibility for space-constrained UI layouts. This option complements the existing `small` and `medium` header sizes. You can now display a hero-style header even when no child components are present, simply assign a `height` value to the header. If no `height` is provided, the header defaults to a compact size.
* Enhanced [amount control](https://docs.jigx.com/examples/readme/components/amount-control) - The `amount-control` can now be used as a standalone component which provides a simple and intuitive way to adjust numeric values using plus and minus buttons. It’s ideal for shopping carts, quantity selectors, and any form where values need to increase or decrease in defined steps.
* The [product-item](https://docs.jigx.com/examples/readme/components/list/product-item) has been enhanced with the following:
  * Support for two distinct visual types to better fit your design needs.
    * `default` : The classic list row style. Best for dense lists where vertical space is at a premium.
    * `card` : A boxed, card-style presentation with elevation. Best for emphasizing individual items, especially when used with column (numberOfColumns) layouts.
  * Updated pricing colors: The current `price` now displays in red and the `discounted` amount in black, reversing the previous color hierarchy.
  * The bulk remove option (previously indicated by an 'X' icon) has been removed from the component and is no longer available.
  * Decimal formatting: You must explicitly handle decimal precision and formatting in data or expressions. Failure to format decimals (e.g., limiting to 2 decimal places) may result in UI alignment issues when multiple decimal points are displayed.
* [Rating](https://docs.jigx.com/examples/readme/components/rating) - The Rating component allows users to capture and display ratings within the app. It is commonly used in frontline workflows such as service feedback, inspections, and performance scoring.
* [Summary](https://docs.jigx.com/examples/readme/components/summary) component has been enhanced to include a `progress` value, which is useful for displaying completion or status over time, such as task progress, goals, or performance metrics. The value is shown as a visual progress indicator, making it easy to track how much has been completed at a glance.
* [Slider](https://docs.jigx.com/examples/readme/components/slider) - Use the `slider` component to select a numeric value within a defined range by dragging a thumb control. Typical use cases include price ranges, quantity selection, thresholds, and score inputs.
* The [bottomSheet](https://docs.jigx.com/examples/readme/jig-types/common-jig-type-properties/bottomsheet-_beta_#bottomsheet-set-to-open-by-default-when-the-parent-jig-opens) `initialValue` property now supports expressions, for example, `initialValue: =@ctx.solution.state.defaultSheet`.
* Added support for `component.field-row` with flex styling, enabling precise control over the proportional width of input components within a row. This allows for more flexible and responsive form layouts.
* Added `videoQualityPreset` property to `media-field`, `avatar-field`, and `action.open-media-picker`, enabling control over video compression on iOS - helping reduce file sizes or preserve original quality as needed.
*   Added two new optional properties on [`jig.list`](https://jig.listhttps/docs.jigx.com/examples/readme/jig-types/jig_list):

    * `initialItemCount` - number of items to render on the first frame. Lower = faster initial display; higher = more upfront rendering. Accepts a number or expression.
    * `scrollRenderBuffer` - multiplier for how many viewports of content to keep rendered off-screen while scrolling. Lower = less memory; higher = smoother fast scrolling. Accepts a number or expression.

    The list's default behavior is improved - A FlatList now uses the calculated item-count based on screen/item height instead of a hardcoded 25, and `windowSize` defaults to 5 instead of 2.
* [jig.tabs](https://docs.jigx.com/examples/readme/jig-types/jig_tabs) - The tab navigation bar now automatically hides when only 1 tab is present in a jig.

#### Bug Fixes

* Fixed an issue where the media picker did not enforce the `maximumFileSize` restriction when opening, and file size validation errors were not displayed to the user.
* Add automatic file upload/download for `media`, `signature`, and `avatar` fields. Files now persist across form reopens with diff-based upload logic (only new files uploaded, removed files deleted). Per-field datasources enable efficient file comparison. Implements round-trip file persistence: capture → upload → reopen → display.

### Actions

#### New features & improvements

* [Show-alert action](https://docs.jigx.com/examples/readme/actions/show-alert) - The new `action.show-alert` provides a flexible way to deliver context-aware notifications without interrupting user flow. Configure alerts with a `title`, `description`, `icon`, and `style`, and choose whether they appear as a `toast` or `modal`. You also have full control over dismiss timing and behavior. This action introduces support for `groupId`, allowing related alerts to be grouped and reducing repeated or duplicate messages, especially useful for handling recurring errors. These enhancements offer clearer communication, prevent alert overload, and ensure users receive timely information in a consistent and non-disruptive way. In addition to screen actions, `show-alert` is also available within functions, allowing you to configure user-friendly alerts for errors coming from the remote systems.&#x20;
* Two improvements to state management actions:
  * **New:** `action.reset-component-state` - Reset component state. Optionally target specific components by `instanceId`, or omit to reset all components.
  * **Enhanced:** `action.reset-solution-state` - The `changes` parameter is now optional. Omit it to reset all solution state keys at once.
* Added `videoQualityPreset` property to  `action.open-media-picker`, enabling control over video compression on iOS - helping reduce file sizes or preserve original quality as needed.
* [action.go-back](https://docs.jigx.com/examples/readme/actions/go-back) - Add support for navigating to a specific jig using the go-back action's `to` option.
* [Action-evaluate](https://docs.jigx.com/examples/readme/actions/evaluate) - An action that evaluates any data structure. The `action.evaluate` action evaluates any value you pass into the options `value` property. It supports objects, arrays, primitives, and nested combinations of all three. Expressions are evaluated first. Any `TextLocale` or `TextWithFormat` values in the result are then resolved to strings. The final result is stored in outputs `value` and keeps the original shape.
* Added the [onBlur](https://docs.jigx.com/examples/readme/events) event which is triggered when you leave a form field, for example, when you tap into another field, close a picker, or dismiss the keyboard. It allows you to run actions after the user finishes interacting with a field, rather than on every value change. `OnBlur` only applies to certain form fields.
* Added  `=@ctx.actions.<id>.state.isPending` expression to track whether an async action is currently executing. Returns `true` while an async action is in progress and `false` when idle. Supported for all async actions. Sync-only actions (e.g. `go-to`, `set-state`, `reset-state`) always return `false`.

### Builder

#### New features & improvements

*   Enhancement to [REST functions](https://docs.jigx.com/building-apps-with-jigx/data/data-providers/rest/rest-error-handling) now include the  `show-alert` action within `errors` in functions, allowing you to display alerts automatically when errors occur.

    This enhancement enables you to:

    * Configure **custom alerts** that trigger on function errors.
    * Configure customized [OAuth error messages](https://docs.jigx.com/administration/organization-settings/oauth-configurations#configuring-oauth-error-messages) in function errors.
    * Define **actions** directly on those alerts (e.g., _Retry_, _Dismiss_).
    * Use `groupId` to group related alerts and control how repeated error notifications are handled.

    This integration provides greater flexibility and visibility during error handling, helping users quickly understand and respond to issues within the app.
* A unified approach for [text style and formatting options](https://docs.jigx.com/examples/readme/components/common-component-properties#text-or-label) has been introduced to simplify how you configure text across components. This enhancement standardizes the way line options (such as `fontSize`, `isBold`, `color`, and `numberOfLines`) are defined in YAML, ensuring a consistent structure and behavior across all components that display text.
* **Instantly visualize color values in Builder** - a color decorator has been added to the YAML editor in Jigx Builder, making it easier to visually identify color values directly within your jigx configuration files. Color details also appear in hover pop-ups, providing quick previews and hex values, ensuring accuracy when selecting or adjusting colors.
* Automatic [change queuing for Dynamic Data tables](https://docs.jigx.com/building-apps-with-jigx/data/offline-remote-data-handling#dynamic-data-change-tracking-and-queuing) (`default/tableName`) — All local database operations (CRUD, SQL, and find/replace) now track and queue changes using a temporary table workflow. Changes are detected, batched (INSERT/UPDATE/DELETE), and prepared for sync automatically. Includes built-in error handling and guaranteed cleanup, with no changes required to existing implementations.
* [Global datasources now support inputs](https://docs.jigx.com/building-apps-with-jigx/data/datasources#global-datasource-inputs) - A global datasource can be instantiated multiple times within a Jig, each with its own input values. Use `ctx.inputs` inside the global datasource configuration to access them, the same way inputs work in custom components.
*   [Cross-package data access and action execution](https://docs.jigx.com/building-apps-with-jigx/data/datasources/cross-solution-data-access)

    You can now query data from and execute actions in another installed solution directly from your datasource or jig configuration. Add a `package` property to any entity definition in a `datasource.sqlite` config to include data from another solution's SQLite database. In your SQL query, reference cross-package tables using `[package-name].[entity-name]` notation, making it straightforward to `JOIN` or `UNION ALL` data across solutions in a single query. To execute an action from another solution, add a `package` property to `action.execute-action` alongside the action name and any parameters. This release also adds a `performOperations` property to `guard` functions, giving you explicit control over whether table write operations run after a guard executes, useful when the default behavior (run on guard failure) does not fit your logic.

#### Bug fixes:

* Fixed an issue where using a shared expression inside a `when` condition did not evaluate correctly. This occurred in cases where the shared expression referenced `ctx.datasource` and was used within an `onFocus` event. The condition now evaluates properly, ensuring consistent behavior whether the expression is used directly in the `when` condition or referenced through a shared expression.

### Jigx Management

* Bug fixes, performance improvements, and usability improvements.

### Known Issues

*   _Referenced actions for_ `jig.tabs` _not executing at runtime_ - Referenced actions configured within jig.tabs are currently detected in Builder, but fail to run in the app. At runtime, the action returns a “no configuration found for … action” error, indicating that the referenced action is not being resolved correctly.

    _Workaround:_ None at this time.&#x20;
*   _Header image not displaying when iOS preview is triggered -_ When a jig is configured with iOS `preview`, the header image does not display in the preview window. This occurs only when preview is invoked, normal navigation into the jig displays the header image as expected.

    _Workaround:_ None currently available.

### Updates to Quick-Start sample solutions

<table><thead><tr><th width="146.08984375">Solution</th><th>Additions</th></tr></thead><tbody><tr><td>jigx-samples</td><td>Banner component</td></tr><tr><td> </td><td>Sections component</td></tr><tr><td> </td><td>Show-alert action</td></tr><tr><td></td><td>Menu-item component</td></tr><tr><td></td><td>Product-item component</td></tr><tr><td></td><td>Amount-control component</td></tr><tr><td></td><td>Rating component</td></tr><tr><td></td><td>Summary (progress) component</td></tr></tbody></table>
