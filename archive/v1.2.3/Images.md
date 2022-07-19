### Decor graphics
For decor elements uses **svg image spritesheet** `assets\svg-icons.svg` via `starter_get_svg` function.  
File `assets\svg-icons.svg` loads via XHR (XmlHttpRequest - i.e. pure 'ajax') in `footer.php` to make it cacheable.  
By default Starter uses [bootstrap icons](https://icons.getbootstrap.com/).
#### How to use
```php
<?php echo starter_get_svg( array( 'icon' => 'bi-pen' ) ); ?>
```
It output inline svg which displays in the same high quality on screen with any pixel density because it's vector:
```html
<svg class="icon-bi-pen" aria-hidden="true" role="img">
  <use href="#bi-pen" xlink:href="#bi-pen"></use>
</svg>
```
<details><summary><strong>Add bootstrap svg example</strong></summary>
  <a href="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.2.0/screenshots/bootstrapsvg.mp4">Download this video example</a><br>
  <img width="600" src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.2.0/screenshots/bootstrapsvg.gif" alt="Add bootstrap svg">
</details>
<br><br>



### Content images
Optimized and converted **to webp** by [EWWW Image Optimizer plugin](https://wordpress.org/plugins/ewww-image-optimizer/). Each **image slices by each 200px** (200px, 400px, 600px etc) for deliver **best image sizes** for each device.  

*If you are not familiar with **image srcset and sizes attributes** it could be complicated quickly understand this logic, but in fact it's very easy to use in Starter theme - you can to see below `Add image example` firstly.*

Since version 4.4 WordPress supports responsive images, shortly **how it works**: `<img>` contain attribute `srcset` (autogenerated) with array of all available image sizes for current image and attribute `sizes` (setup by developer) with info about what image width should be for specific viewport width. **Browser** using attributes sizes and knowlenge about screen density (yes, browser knows that!)  **download best image size** (for current situation) from srcset attribute.  
[Detailed article about WordPress images](https://www.smashingmagazine.com/2016/09/responsive-images-in-wordpress-with-art-direction/)

#### How to use
Starter uses function `starter_img_func` which require `img_sizes` (sizes attribute) and `img_id` (image ID).
```php
<picture>
  <?php
    echo starter_img_func([
      'img_src'   => 'w800',
      'img_sizes' => '(max-width: 575px) calc(100vw - 10px), (max-width: 767px) 530px, (max-width: 991px) 340px, (max-width: 1199px) 460px, 550px',
      'img_id'    => $starter_img
    ]);
  ?>
</picture>
```
It output next markup to frontend:
```html
<picture>
	<source
		type="image/webp"
		srcset="/wp-content/uploads/2020/09/t-shirt-with-logo-1.jpg.webp 800w,
			/wp-content/uploads/2020/09/t-shirt-with-logo-1-150x150.jpg.webp 150w,
			/wp-content/uploads/2020/09/t-shirt-with-logo-1-200x200.jpg.webp 200w,
			/wp-content/uploads/2020/09/t-shirt-with-logo-1-400x400.jpg.webp 400w,
			/wp-content/uploads/2020/09/t-shirt-with-logo-1-600x600.jpg.webp 600w"
		sizes="(max-width: 575px) calc(100vw - 10px),
			(max-width: 767px) 530px,
			(max-width: 991px) 340px,
			(max-width: 1199px) 460px, 550px">
	<img class="img-fluid" loading="lazy" src="/wp-content/uploads/2020/09/t-shirt-with-logo-1.jpg" alt="t-shirt-with-logo-1.jpg" width="800" height="800">
</picture>
```

All images loads with native browser lazyload (attribute `loading="lazy"`).
<details id="content_img_example"><summary><strong>Add image example</strong></summary>
  Everything what you need <strong>to provide optimized image size</strong> for specific device - it's to setup <strong>correct sizes attribute</strong>: go through <strong>each breakpoint</strong> and setup image size. Breakpoint depends on your styles, in an example below used default bootstrap => default bootstrap breakpoints.
  <a href="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.2.0/screenshots/addimg.mp4">Download this video example</a><br>
  <img width="600" src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.2.0/screenshots/addimg.gif" alt="Add image">
</details>
<br><br>



### Content images: item boxes with aspect ratio on responsive.
**The problem**: it's a common issue when clients asking to make the same product item height - but they use images with *different aspect ratio*. If just to setup height for all screens - *image will lost aspect ratio on responsive* (due width changes on responsive).  
**The solution**: **go through each breakpoint and setup height** keeping aspect ratio. Starter uses scss mixin `imgHeightItem` which makes this process so fast and easy: mixin accepts two parameters `aspect ratio` and `array of image width for each breakpoint` - that's array exactly the same which used in sizes attribute (previous [chapter](#user-content-content-images)). Using these two parameters *mixin calulate correct height for each breakpoint*.  
**How to use**: copy-paste array from html to css and setup desired aspect ratio!
<br><br>



### Code
* img: `assets\svg-icons.svg` - svg spritesheet with decor images/icons
* js: `footer.php` - at the end of file contain script for load svg file (just above)
* php:
     * `inc\icon-functions.php` (fork of twentyseventeen/inc/icon-functions.php).  
     * `inc\image.php` - content image functions