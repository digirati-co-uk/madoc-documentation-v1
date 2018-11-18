---
name: Importing content
order: 1
---

# Importing content

How to import collections, manifests and canvases into the platform.

## Importing collections

On the main menu you will see a link "Create IIIF Collection". Click on this button and it will take you to the normal Omeka item set form, but with the resource template and class already pre-filled. The only required field at this stage is *Collection URI*  at the bottom. In the URI text box, enter the address of your IIIF collection and hit *save* in the top right corner.

When you import a collection, all of the manifests will also be imported as Omeka items, and each of the manifests canvases will also be imported as Omeka items.

This may take some time if the collection is large. If you are an Admin, in the menu you can click on "Jobs" and you will see the status of the imported content. Clicking on one of these items will let you see what was passed to the job, and scrolling to the bottom will show you a link to the raw logs form the import. This can be useful for debugging.

After importing a collection, you will be redirected to the created Omeka item. Once all of the attached manifests are finished loading, you will be able to click on the button at the top above the item in Omeka to see the JSON representation of the imported content. This is IIIF compliant copy of the resource imported and can be used externally if desired. It is also the IIIF content that drives the rest of the website.

## Importing manifests

One the main menu you will see a link "Create IIIF Manifest". Click on this button and it will take you to the normal Omeka item form, but with the Manifest resource template and `sc:Manifest` class pre-filled. The only required field is the *Manifest URI* at the bottom. In the URI text box enter the address of your IIIF manifest and hit *save* in the top right corner.

When you import manifests, all of the embedded canvases will be added as Omeka items into the platform. 

After importing a manifest, you will be redirected to the create Omeka item. Once all of the attached canvases are finished loading, you will be able to click on the button at the top above the item in Omeka to see the JSON representation of the imported content.

## Importing canvases

Canvases are not deferenced. But you can create one from scratch. To do this you will need the RDF property `dcterms:source` and paste in the JSON for that canvas. You will also have to add in a valid identifier in the Canvas URI field and optionally attach a IIIF tile source. Once created, this Canvas can be added to existing manifests. When manually adding a canvas to a manifest ensure you set up a link both ways. (`Manifest.sc:hasCanvases` and `Canvas.dcterms:isPartOf`)

## Limitations

The main limitation to our module is the inability to import multiple instances of the same content. Some content may be in an indetermined state if you import the same collection, manifest or canvas into the platform. You MAY be able to import the same IIIF content if they are added to different sites, but this is not officially supported in the platform.

The second limitation is the size of image assets when generating thumbnails. This can cause 2 problems: 

* Huge amount of time to import
* Crashing if memory or network issues occur

There is no good way to recover after a failure at this point. If you do run into this issue you will have to go into the content management site and manually remove the content.
