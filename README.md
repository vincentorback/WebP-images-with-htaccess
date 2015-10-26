# WebP Images with htaccess
This snippet offers an easy way to detect if the browser [supports WebP](http://caniuse.com/#search=webp) images and then if there is a WebP images located at the same path as the originally provided image with the same file name, it replaces it with that WebP image. Read more about the WebP format [at Google](https://developers.google.com/speed/webp/).

**If you can, use the `<picture>`-element instead of this solution.**

## Usage
Place the following in your .htaccess file and jpg/png images will be replaced with webp images if found in the same folder.
```htaccess
<IfModule mod_rewrite.c>
	RewriteEngine On
	RewriteCond %{HTTP_ACCEPT} image/webp
	RewriteCond %{DOCUMENT_ROOT}/$1.webp -f
	RewriteRule (.+)\.(jpe?g|png)$ $1.webp [T=image/webp,E=accept:1]
</IfModule>

<IfModule mod_headers.c>
	Header append Vary Accept env=REDIRECT_accept
</IfModule>

AddType image/webp .webp
```

## Other solutions

#### HTML (Preferred solution)
```html
<picture>
  <source srcset="/path/to/image.webp" type="image/webp">
  <img src="/path/to/image.jpg" alt="">
</picture>
```

#### JavaScript
This is the .htaccess solution. Another way is to use JavaScript. [Read more here](https://github.com/vincentorback/WebP-Images-with-javascript).

## Feedback
If you’ve got any thoughts or ideas about this, please make an [issue](https://github.com/vincentorback/WebP-images-with-htaccess/issues), a [pull request](https://github.com/vincentorback/WebP-images-with-htaccess/pulls) or hit me up on [Twitter](https://twitter.com/vorback)!
I’m just as interested as you in new image formats and responsive techniques.
