### There are two options for setup homepage:
1. **By default homepage displays 10 latest products** - default WordPress feature, `index.php` is a template.
    <details><summary>Show details</summary>
     <img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/homepage/homepage01.jpg" alt="Homepage default template">
    </details>

2. You can to setup static page as homepage, **Starter has custom template** `templates\page-home.php` specially for that.  
Create page firstly using template 'Home'.  
    Custom template has two features:   
   1. **Fullwidth-container carousel**.  
   You can to setup desktop only image and it will be used for all screens, but _usually aspect ratio of fullwidth-container carousel for desktop looks bad on mobile_ (due devices has too different screen aspect ratio) - so optionally you **can setup different images for tablet/mobile**.  
   _Best aspect ratio_ tip for each device provided.  
   Also optionally you can to _setup link for each slide_.
      <details><summary>Show details</summary>
       <img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/homepage/homepage03.jpg" alt="Homepage custom template - fullwidth-container carousel">
      </details>

   2. **Product featured lists.**  
   Starter home template allows to create product featured list with title which displays as carousels.
      <details><summary>Show details</summary>
       <img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/homepage/homepage04.jpg" alt="Homepage custom template - collections">
      </details>
    When page created - setup it as static page.
    <details><summary>Show details</summary>
     <img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/homepage/homepage02.jpg" alt="Homepage custom template">
    </details>
<br>



### Code
* ACF: `Home`
* css: `assets\scss\theme\pages\_home.scss`
* js: `assets\js\modules\home_page.js`
* tpl: `index.php` and `templates\page-home.php`