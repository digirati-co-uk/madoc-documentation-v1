---
name: Platform configuration
order: 1
---

# Platform configuration

Some descriptions of the site configuration.

## Crowd sourcing modes

In addition to the Omeka default settings, we also add some custom settings to allow your platform to be more cusomtised. In order to get to these settings click on "Sites" and then click on your site. From the left menu, under your site, click on "Settings" (note: not the very bottom of the admin menu, under your site name) and then down at the bottom of that page you should see a form section called "Crowd sourcing". You can change any of these toggles.

### Enabling bookmarking

Allows users to bookmark content. This can be exposed back to users using our open source user bookmarks module, which show as a IIIF collection IIIF content bookmarked. These are [annotations stored](/crowdsourcing/annotation-format#bookmarking) in the configured Elucidate.

### Enabling mark as complete

This allows users to mark a page as complete and no further annotations should be added. This is a [single annotation](/crowdsourcing/annotation-format#marked-as-done) with a custom motivation. When this annotation exists on a crowdsourcing page, no crowdsourcing UI will be displayed. This can also be used to bubble statistics on how far through a crowd-sourced project you are.

### Enabling user created annotations

This allows registed uses to create annotations on the site. This also requires a valid [Capture model](/crowdsourcing/capture-models) to be [added to the site](/multisite/creating-new-site#adding-site-content)

### Enable user flagging

This add a button on IIIF content that allows IIIF content or pages to be flagged for review. The review is added as [an annotation](/crowdsourcing/annotation-format#flagging). We have created other open source software that can manage these types of annotations and redact Omeka or IIIF content in an administration UI. This is not included in the platform due to external requirements.

### Enable users to see annotations

This allows users to see annotations created by admins or other users. This can be used with the creation disabled to show static annotations created by a curator in a show-case site.

## Private sites

You can [make a site private](/multisite/creating-new-site#publishing-your-site) in the configuration and only allow certain registered users to see it.

## Opening user registrations

From the [Public User](/reference/modules/public-user) module you can toggle on or off user registrations, including the role that they are when they when they register.