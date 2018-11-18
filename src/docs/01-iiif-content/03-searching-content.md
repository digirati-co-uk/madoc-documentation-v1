---
name: Searching content
order: 3
---

# Searching content

Omeka-s has a built in search on the admin and public site. You can use this to provide some basic search functionality and better organise your content.

## Admin UI searching

In the Admin UI you can see that there are a few custom search queries already defined. If you click on "Items" in the left menu you will see under the menu there is

* Manifests
* Canvases
* Capture model fields

Clicking on any of these will show you the item list filtered by that type. You can also search using Omekas built in search. See [Omeka-S Documentation](https://omeka.org/s/docs/user-manual/search/) for details.

### Custom metadata

You can add [custom RDF properties](/iiif-content/editing-content#custom-metadata) to IIIF resources. When you add these properties the values will become searchable in Omekas free-text search. You can also use the Admin UI to search by field on these custom properties to better refine your searches.

## Site search

In our custom modules, you can use this custom metadata to organise or tag your content and use search terms to populate IIIF search queries for the Manifest, Canvas and Collection list media blocks. These are found on [Site pages](/customising-pages/site-pages) and [IIIF Pages](/customising-pages/iiif-pages).

You can experiement with this by simply using the search box on the default Omeka theme in the top right on any created site.

*__Note:__ Annotations are not stored in Omeka and are therefore not searchable in this UI.*