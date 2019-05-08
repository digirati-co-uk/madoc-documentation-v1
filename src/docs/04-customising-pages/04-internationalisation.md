---
name: Internationalisation
order: 4
---

# i18n
With the i18n module you have fine grained control over how Madoc itself is translated and also
the content in your site.

This module currently only supports `.mo` files, so `.po` files need to be converted. An application such as [Poedit]() can be used, and this will save both types of files for you. You generally start by downloading a `template.pot` file, and then copying across the `.mo` and optionally `.po` files into a specific folder for Madoc to pick up and use.

You can use the Omeka admin to see translations in the UI from the sites menu, shown below.

<img src="/img/i18n-menu.png" alt="Internationalisation menu" width="300" />

## Tour of the UI
From the admin UI, you can see for each site what translations are being loaded in and used. You can also download template files to start translating. Currently there is no way to see the translation progress for a given language for the whole site, but this will be a useful feature in the future. Additionally there is no editor or way to upload translations to the site currently, but is being investigated as a potential option.

When you first click into the translations section, you will see 2 groups, with 5 sections of translations. The first group is the Global translations that are applied to all of the sites in Madoc. These are the Omeka translations and the Madoc translations. The second group is for translations specific to this site and are for the current theme, the navigation and the pages.

<img src="/img/i18n-home.png" />

When you click into a section, you will be presented with a few options. First you'll see the folder where the translations live<sup>1</sup>. This is where you will want to copy in finished translations into. This can be done using Docker:

```diff
FROM digirati/madoc-platform:1.1.0

# Add our theme
ADD --chown=www-data:www-data ./nlw-madoc-theme /srv/omeka/themes/nlw-madoc-theme

+ # Add translations
+ ADD ./translations/omeka/es.mo /srv/omeka/application/language/es.mo
```

Next are the actions section<sup>2</sup>, containing links to download a `template.pot` file that you can use to start a new translation and also a link to see a visual representation of the template file in the browser, to better see how large the translation process may be.

<img src="/img/i18n-omeka.png" />

Below that are the list of languages that are currently translated, either fully or partially. You can click into each one to see how much has been translated so far<sup>3</sup>. Missing translations will be highlighted in yellow.

<img src="/img/i18n-view.png" width="400"/>

Finally, up at the top right, you will see any other actions that you can take, such as requesting new transaltions<sup>4</sup> if they are from Madoc or Omeka.


## Omeka translations
Out of the box Omeka comes with some translations for various languages. There is a [template.pot](https://github.com/omeka/omeka-s/blob/develop/application/language/template.pot) file that you can download to translate into more languages. It is advised that any translations made are contributed back to [Omeka-S](https://github.com/omeka/omeka-s/) in their repository<sup>4</sup>.

## Madoc translations
Similarly to Omeka, Madoc comes with its own translation template and any translations will be shipped with the Madoc Platform docker image.

## Site content translations
In Omeka you can translate some content at the source, such as manifest and canvases using Omeka's UI. For other pieces of content you can use external translations. This is useful for keep the editing UI simple and not overriding Omeka's defaults. These translations will live in their own folder in Omeka. `./translations/s/{site-slug}/{folder}` so you can easily organise them.

### Navigation translations
When you create navigation on the site, you may want to translate the labels in the menu. Once your menu is created, you can download the template file from the UI and then copy your completed `.mo` files into `./translations/s/{site-slug}/navigation`. Once copied in they will be picked up by Omeka and used when your sites language changes.

### Page translations
The way blocks are internationalised is as follows:
* You create a block with some localised content
* You mark the block with the locale
* Repeat this for each locale
* Only the blocks matching the users locale will be shown to them

This works great, but the downside is that the page-building can get messy if there are many languages or there are many different blocks. There is an alternative way. You can create your block in the default locale and mark the block as "default". This will ensure that it is displayed, it will also be translated.

You can find blocks marked as "Default" in the page translation section of the UI and view all of the strings needing to be translated. You can also download a template file containing the current snapshot of the translations. This allows you to create a full site of page blocks and then export them in one go to be translated.

Similar to the other translations, you can simply copy the completed `.mo` files into `./translations/s/{site-slug}/page-blocks` folder in your Dockerfile.

### Theme translations
If you create your own theme, you can add translations to that theme under the `./translations` folder of that theme. These will be picked up automatically and applied. Note: you must use `translate()` in your code to pass translations through. You can also find our translation extraction tools on our Github. (Twig + PHP).
