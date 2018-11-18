---
name: Editing content
order: 2
---

# Editing content

Some IIIF fields can be edited in the Omeka UI.

## Labels

The easiest entry to change is the `dcterms:title` field on either a [Collection](/iiif-content/importing-content#importing-collections), [Manifest](/iiif-content/importing-content#importing-manifests) or [Canvas](/iiif-content/importing-content#importing-canvases). When you change this property, the IIIF label will be updated to reflect this. You can use this to change the labels that are displayed on the end-user pages in Omeka.

## Descriptions

The description can also be added to Collections, Manifests and Canvases. This update will be reflected in the JSON and on the website.

## Custom metadata

If you use Omeka to create custom RDF properties, these will be added to the IIIF JSON as custom metadata pairs. The label will be the RDF label, and the value(s) will be the value inputed. This can also be used to add searchable data that will be picked up by Omekas [build-in search](/iiif-content/searching-content)

## Linked resources

Collections can reference manifests and other collections. Manifests can reference canvases. When you import content you will see the links and relations created. You can edit these, remove them or create new ones and the changes will be reflected in the JSON and on the site. Be careful when changing these relations as you will have to keep track of changes you've made if you want to revert them at any time. See [limitations of IIIF content](/iiif-content/importing-content#limitations).
