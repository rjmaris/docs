# getImage

The `getImage` hook is triggered when a thumbnail is generated and allows you to
add a custom routine. It passes the path, the width and height, the mode, the
cache name and the file object as arguments and expects a path as return value.

> **Tag** Available from version 2.8.0-RC1.


## Parameters

1. *string* `$image`

    The image location, relative to Contao root.

2. *int* `$width`

    The target image width.

3. *int* `$height`

    The target image height.

4. *string* `$strCacheName`

    The cache file name generated from source file name, width, height and mode
    setting. The cache file includes the path to `system/html/`.

5. *object* `$objFile`

    A [File](../api/File.md) object from the source image.

6. *string* `$target`

    The target location where the image should be stored. This will be `null` in
    most cases, if not you should ignore `$strCacheName`.


## Return Values

If you want to override Contao's [Controller::getImage](../api/Controller/getImage.md)
method, return a string to the new image. Otherwise return the boolean `false`.


## Example

```php
<?php

// config.php
$GLOBALS['TL_HOOKS']['getImage'][] = array('MyClass', 'myGetImage');

// MyClass.php
public function myGetImage($image, $width, $height, $mode, $strCacheName, $objFile, $target)
{
    return MyImage::generateThumbnail($image, $widht, $height, $mode);
}
```


## More information


### References

- [system/modules/core/library/Contao/Image.php](https://github.com/contao/core/blob/3.5.0/system/modules/core/library/Contao/Image.php#L477-L490)


### See also

- [`Controller::getImage`](../api/Controller/getImage.md) – Resize an image.
