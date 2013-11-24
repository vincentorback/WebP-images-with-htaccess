WebP Images with htaccess
==========================

> WebP is a new image format that provides lossless and lossy compression for images on the web. WebP lossless images are 26% smaller in size compared to PNGs. WebP lossy images are 25-34% smaller in size compared to JPEG images at equivalent SSIM index. WebP supports lossless transparency (also known as alpha channel) with just 22% additional bytes. Transparency is also supported with lossy compression and typically provides 3x smaller file sizes compared to PNG when lossy compression is acceptable for the red/green/blue color channels.

*- Google*
  
  

### Usage
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


#### Feedback
If you've got any thoughts or idead about this, please tweet at [@vorback](https://twitter.com/vorback).
I'm just as interested as you in new image formats and responsive techniques.
