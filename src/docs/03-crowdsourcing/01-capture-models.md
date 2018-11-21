---
name: Capture models
order: 1
---

# Capture models

A capture model is a JSON-LD document that describes both the UI for creating an annotation and the structure that the annotation should look like. It can also structure a choice of capture models, that will be shown in the annotation UI.

## Importing capture models

From the admin menu, down at the bottom there is an option "Capture model importer". You can click on this, choose a JSON file from your computer and then choose a site to assign the model to. Once you click save your capture model will be imported and added to the selected site. You can always add this to multiple sites by adding it to the [site pool](/multisite/creating-new-site#adding-site-content).

## Choices

You can add multiple capture models and create a choice between them. This will show and allow the user to drill in to which choice they want. These choices can be as deep as required. You can also reuse the same capture models for the leaves of the choices.

## Inputs

There are a variety of input types that can be used to build up your capture model. 

### Text box
A simple text input.

### Hidden
A hidden input that will be part of the end annotation but not presented to the user to edit.

### Textarea
A simple text area.

### HTML Field
A text area with a WYSIWYG configured for simple HTML.

### Dropdown list
A list of strings that can be chosen.

### Combo box (proposed)
An autocomplete that needs to be configured with an endpoint, or static list of items.

### Date picker
A simple date picker.

### Map picker
A google map integration that allows a point on a map to be selected, returned as LatLng.

### Radio (proposed)
Choice presented as radios.

### Checkbox (proposed)
Multiple choice, presented as a list of checkboxes, or a boolean flag with a single checkbox.

## Selectors
When an annotation is created the user is optionally prompted to select a region of the image to annotate. This is the various selectors that are supported in Madoc specification, some implemented and some proposed.

### Whole canvas
This is the default in absence of a selector and will simply select the entire resource being annotated.

### Box
A simple box selector that lets the user move and resize a box that's dropped onto the resource. The properties recorded are height, width, x and y.

### Ellipse (proposed)
Similar to the box selector, but instead an ellipse shape is dropped. This would be saved as an SVG selector (see below).

### SVG (proposed)
A selector type where an SVG shape is the output. This is still a proposed format and the exact UI tooling to facilitate this is not yet defined.

### Polygon (proposed)
A selector that would output an SVG path, allowing points to be placed on an image to build up an irregular shape for more precise annotations. Suitable for dense images.

### Pin
Similar to the box selector but the output has a fixed height and width of 1px and the UI does not allow resizing. Used for highlighting points, opposed to regions. 

## Advanced
Some advanced features in the capture model specification.

### Fallback model
Used in conjunction with a dropdown or autocomplete. If an entry doesn't exist in the autocomplete a new entry can be added using a capture model. This requires infrastructure to work, as the annotations need to be captured and added into the source of the autocomplete or dropdown data source.

### Nullable capture model
This is a component that enhances a boolean. For example "Is there a person in this image?" could be the boolean, and the optional extra information would be actually identifying the person. This again requires infrastructure to handle the person independently, annotations that come out of this process are usually not in a final state to be presented back and require a backend to extract and format.

## Settings - annotation format
There are some dials and configuration that changes the output format of the annotations. We have a few flavours that work well to produce [standard annotation formats](/crowdsourcing/annotation-format).
### Combine annotations
Boolean, if set to true this will combine all fields in the capture model into a single annotation. When set to false, each piece of the capture model will be saved as an individual annotation.

### Serialize annotation
If set to true this will use the RDF in the capture model and build up a JSON-LD document based on the input from the user and save this as a body in the annotation. This can be used in conjunction with human readable and label parts to still allow your annotation to be displayed in a human readable way.

### External annotation
This is an advanced feature that, when configured correctly, allows you to store annotations in Omeka as Omeka items based on the resource templates attached to the capture models and the RDF tags that make them up.

### Human readable field of annotation
Mark the annotation as human readable and when building the annotation up, annotation studio will identify human readable fields and add them as textual bodies to the annotation.

### Motivation of annotation
This allows a custom motivation (default: tagging) to be applied to the annotations on the way out. For example transcriptions may have a motivation of "transcribing" or "describing".

### Purpose of annotation
Same as the motivation, but for the purpose field in the annotation model.

### Label parts of annotation
The RDF term from the final RDF format of the capture model output that should be used as the label field of the annotation.

### Body type of annotation
When bodies are added to annotations, this type will be added. Default: TextualBody.
