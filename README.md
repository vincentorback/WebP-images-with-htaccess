# WebP images with htaccess
This snippet detects if the browser [supports WebP](http://caniuse.com/#search=webp) images and then serves a .webp image instead of jpg/png if a .webp file is available at the same location as the supplied jpg/png. Read more about the WebP format [at Google](https://developers.google.com/speed/webp/).

[**If you can, use the `<picture>`-element instead of this solution!**](#preferred-solution)

## Usage
Place the following in your .htaccess file and jpg/png images will be replaced with WebP images if found in the same folder.
```apache
<IfModule mod_rewrite.c>
  RewriteEngine On

  # Check if browser support WebP images
  RewriteCond %{HTTP_ACCEPT} image/webp

  # Check if WebP replacement image exists
  RewriteCond %{DOCUMENT_ROOT}/$1.webp -f

  # Serve WebP image instead
  RewriteRule (.+)\.(jpe?g|png)$ $1.webp [T=image/webp,E=accept:1]
</IfModule>

<IfModule mod_headers.c>
	Header append Vary Accept env=REDIRECT_accept
</IfModule>

<IfModule mod_mime.c>
  AddType image/webp .webp
</IfModule>
```

## Preferred solution
```html
<picture>
  <source srcset="/path/to/image.webp" type="image/webp">
  <img src="/path/to/image.jpg" alt="">
</picture>
```
