WebP Images with htaccess
==========================

> WebP is a new image format that provides lossless and lossy compression for images on the web. WebP lossless images are 26% smaller in size compared to PNGs. WebP lossy images are 25-34% smaller in size compared to JPEG images at equivalent SSIM index. WebP supports lossless transparency (also known as alpha channel) with just 22% additional bytes. Transparency is also supported with lossy compression and typically provides 3x smaller file sizes compared to PNG when lossy compression is acceptable for the red/green/blue color channels.

*- [Google](https://developers.google.com/speed/webp/)*


This snippet offers a very easy way to detect if the browser supports WebP images and then replaces jpg and png images if they have a webp images located at the same path with the same file name.


### Usage
```htaccess
<IfModule mod_rewrite.c>
	RewriteEngine On
	RewriteCond %{HTTP_USER_AGENT} !(Chrome\/[0-8]|Android\s[0-3])\.
	RewriteCond %{HTTP_USER_AGENT} Chrome [OR]
	RewriteCond %{HTTP_ACCEPT} image/webp
	RewriteCond %{DOCUMENT_ROOT}/$1.webp -f
	RewriteRule ^(images.+)\.(jpe?g|png)$ $1.webp [T=image/webp,E=accept:1]
</IfModule>

<IfModule mod_headers.c>
	Header append Vary Accept env=REDIRECT_accept
</IfModule>

AddType image/webp .webp
```


#### Other soultions
This is the javascript solution. A far more easier solution is to a use the .htaccess file. Read more [here](https://github.com/vincentorback/WebP-images-with-htaccess).



#### Feedback
If you've got any thoughts or idead about this, please make an [issue](https://github.com/vincentorback/WebP-images-with-htaccess/issues) or make a pull request!
I'm just as interested as you in new image formats and responsive techniques.