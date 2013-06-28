WebP Images with Modernizr
==========================

> WebP is a new image format that provides lossless and lossy compression for images on the web. WebP lossless images are 26% smaller in size compared to PNGs. WebP lossy images are 25-34% smaller in size compared to JPEG images at equivalent SSIM index. WebP supports lossless transparency (also known as alpha channel) with just 22% additional bytes. Transparency is also supported with lossy compression and typically provides 3x smaller file sizes compared to PNG when lossy compression is acceptable for the red/green/blue color channels.

*- Google*
  
  
This script offers a very easy way to detect if the browser supports WebP images and it replaces old images with new, sharper, faster and lighter WebP-images.
  
  
### Usage
The snippet requires Modernizr with a detection of [img-webp](http://modernizr.com/download/#-img_webp).
It also requires a feature coming in Modernizr 3.0.
So for now we need this [prolyfill](https://github.com/stucox/modernizr-on).
  
Here is the HTML, with a noscript fallback.
```html
<img data-jpg="image.jpg" data-webp="image.webp">
<noscript><img src="image.jpg"></noscript>
```

And here is the javascript that takes the data-info from which ever image is supported and puts it as src of the img-tag.
```javascript
Modernizr.on('webp', function (result) {
	var image = document.getElementsByTagName('img');
	if (result) {
		for (var i=0;i<image.length;i++) { 
			image[i].src = image[i].getAttribute('data-webp');
  		}
	}
  	else {
  		for (var i=0;i<image.length;i++) { 
			image[i].src = image[i].getAttribute('data-jpg');
  		}
  	}
});
```
  
  
#### Help
As you might have seen from the code above, this will replace the image event if there is no webp image on the server to replace the png with.
If you have a way to work around this, please let me know!

#### Feedback
If you've got any thoughts or idead about this, please  tweet at [@vorback](https://twitter.com/vorback).
I'm just as interested as you in new image formats and responsive techniques.