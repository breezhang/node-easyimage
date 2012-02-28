EasyImage
=========

EasyImage is built on top of ImageMagick, so make sure ImageMagick is installed on your system.

**Note**: the current version does not work under Windows.

On Ubuntu

    $ apt-get install imagemagick

On Mac OS X

    $ brew install imagemagick

On CentOS

    $ yum install imagemagick

## Installation

    $ npm install easyimage

## Usage

    var easyim = require('easyimage');

EasyImage offers these methods:

	easyim.info(<image_path>, <callback_function>) - to retrieve information about an image
	easyim.convert(<options>, <callback_function>) - to convert an image from one format to another
	easyim.resize(<options>, <callback_function>) - to resize an image
	easyim.crop(<options>, <callback_function>) - to crop an image
	easyim.rescrop(<options>, <callback_function>) - to resize and crop and image in one go, useful for creating thumbnails
	easyim.exec(<command>, <callback_function>) - when you want to call a custom command to ImageMagick

 The EasyImage options object can have these properties depending on 
 the method. Unrelated options are ignored.
 
	src - path to source image
	dst - path to destination image
	width - width of resized image
	height - height of resized image
	cropwidth - width of cropped image
	cropheight - height of cropped image
	x - x offset for cropping
	y - y offset for cropping
	gravity - crop position [NorthWest | North | NorthEast | West | Center | East | SouthWest | South | SouthEast]

## Examples

Example 1

    easyim.info('sample-images/kitten.jpg', function(err, stdout, stderr) {
      if (err) throw err;
      console.log(stdout);
    });

Example 2

    easyim.rescrop(
      {
         src:'sample-images/kitten.jpg', dst:'kitten-thumbnail.jpg',
         width:500, height:500,
         cropwidth:128, cropheight:128,
         x:0, y:0
         },
      function(err, stdout, stderr) {
         if (err) throw err;
         console.log('Resized and cropped');
      }
    );

For more examples check out test.js.

## License (MIT)

Copyright (c) 2012 Hack Sparrow

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
