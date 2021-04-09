# Gulp CMS_REF Replacement Plugin
Gulp plugin to replace all media occurrences in CSS files with
[FirstSpirit](http://www.e-spirit.com/de/product/advantage/advantages.html)
CMS_REF tags:

`url("../path/to/image-filename.jpg") → url("$CMS_REF(media:"image_filename")$")`

The generated reference name is essentially the filename without extension and
with all special chars replaced with underlines. A mapping object with filenames
(not paths!) as keys and reference names as values can also be passed to the
plugin:

```javascript
cmsref({
    "image-filename.jpg": "my_image_jpg"
})
```
## High resolution image naming convention
The common naming convention for high resolution images is to increase the pixelratio and place it inside of the filename.

`my-image.png` is also available for high resolution displays as `my-image@2x.png`.

This plugin will transform high resolution image naming convention like this:

`url("../path/to/my-image@2x.png") → url("$CMS_REF(media:"my_image_2x")$")`

Please note, that FirstSpirit will transform `my-image@2x.png` to `my_image_1`, because `my-image.png` will use the reference name already. This might be confusing. A recommendation is to set the reference name of retina images like above with `my_image_2x` to make clear which pixelratio will be used.