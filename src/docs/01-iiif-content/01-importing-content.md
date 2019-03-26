---
name: Importing content
order: 1
---

# Importing content

How to import collections, manifests and canvases into the platform.

## Importing collections

On the main menu you will see a link <sup>(1)</sup> "Create IIIF Collection". Click on this button and it will take you to the normal Omeka item set form, but with the resource template and class already pre-filled. The only required field at this stage is *Collection URI* <sup>(2)</sup>  at the bottom. In the URI text box, enter the address of your IIIF collection and hit *save* in the top right corner.

<img src="/img/import-collection.png" />

When you import a collection, all of the manifests will also be imported as Omeka items, and each of the manifests canvases will also be imported as Omeka items.

This may take some time if the collection is large. If you are an Admin, in the menu you can click on "Jobs" and you will see the status of the imported content. Clicking on one of these items will let you see what was passed to the job, and scrolling to the bottom will show you a link to the raw logs form the import. This can be useful for debugging.

After importing a collection, you will be redirected to the created Omeka item. Once all of the attached manifests <sup>(2)</sup> are finished loading, you will be able to click on the button at the top above the item <sup>(1)</sup> in Omeka to see the JSON representation of the imported content. This is IIIF compliant copy of the resource imported and can be used externally if desired. It is also the IIIF content that drives the rest of the website.

<img src="/img/collection-view.png" />

## Importing manifests

One the main menu you will see a link "Create IIIF Manifest". Click on this button and it will take you to the normal Omeka item form, but with the Manifest resource template and `sc:Manifest` class pre-filled. The only required field is the *Manifest URI* at the bottom. In the URI text box enter the address of your IIIF manifest and hit *save* in the top right corner.

When you import manifests, all of the embedded canvases will be added as Omeka items into the platform.

After importing a manifest, you will be redirected to the create Omeka item. Once all of the attached canvases are finished loading, you will be able to click on the button at the top above the item in Omeka to see the JSON representation of the imported content.

## Importing canvases

Canvases are not deferenced. But you can create one from scratch. To do this you will need the RDF property `dcterms:source` and paste in the JSON for that canvas. You will also have to add in a valid identifier in the Canvas URI field and optionally attach a IIIF tile source. Once created, this Canvas can be added to existing manifests. When manually adding a canvas to a manifest ensure you set up a link both ways. (`Manifest.sc:hasCanvases` and `Canvas.dcterms:isPartOf`)

## Creating custom Collections

You can also create custom collections from the UI. If you choose "Create collection" and do not enter a UI, then an empty Collection will be created for you. You can add manifests to this collection using the "sc:hasManifests" property and they will be visible inside both the JSON and on the website for your collection.


## Reimporting resources

- You can, per site, choose a capture model from a remote source (URL) instead of importing to Omeka.
- You can also per site, configure if the site should use real IDs or Omeka id for IIIF resources, which is reflected in the targets of annotations
- When you import the same manifest of collection into the system, it will give you an error saying its already in
- When you import a collection that contains manifests already in the system, it will not re-import them and simply re-use them
- When you import a manifest that contains canvases already in the system, it will not re-import them and re-use and link
- When you import a manifest from a URL that does not match the `@id` of the resource, the URL is ignored and imported as the `@id`
- When you import collections or manifests the JSON field stored containing non-CMS content is now much smaller as relationships have been removed.

## Custom collections
You can now create custom collections that only exist in Omeka to create groups of already imported resources and drive new sites from them. The process for creating a new collection is the same as importing, you simply do not add a URI to an external collection. You can add as many manifests to that collection as you need. These can be used just like any other collection in the system, it will even include a IIIF resource link, if you wanted to use it with external tools. In the future you may be able to create custom manifests and canvases too in a similar way. Note: using "original ids" as an option on a site may not work with custom collections as they do not have an original ID.

## FAQ

**If you import a collection/manifest that has been added to or modified (for example more images added to that manifest), will it just see that the manifest is already in the system and give you an error or will it add the new canvases to the existing ones?**

*At the moment it will give you an error. The correct way to handle that case might be to have some "resync" functionality on the resource itself, to update the image list. What will work though, is if a manifest fundamentally changes, and you give it another ID, when you import it will re-use the existing canvases and only import the new ones or, alternatively, you can remove the manifest (which won't remove the canvases) and import the manifest again (it will have a different Omeka ID).*


**Is there an option to delete all manifests and canvases tied to a collection?**

*Not automatically no, but if you work from the inside out and run a query for canvases that have the field "isPartOf" equal to your manifest, and then from there you can use Omeka's bulk delete to remove the canvases, and finally then remove the manifest.*

