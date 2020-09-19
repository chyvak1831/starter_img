# STARTER

Starter WooCommerce theme.  
Open source, free to use - [MIT](https://choosealicense.com/licenses/mit/) license.



# Table of content

- [About](#-about)
- [Installation & Usage](#-installation--usage)
  - [Requirements](#-requirements)
  - [Setup](#-setup)
  - [Build commands](#-build-commands)
  - [Highly recommended/integrated to theme plugins](#recommended_plugins)
- [Comments](#-comments)
- [Filters](#-filters)
  - [Display types](#%EF%B8%8F%EF%B8%8F-display-types)
  - [Color filter](#-color-filter)
  - [Frontend filter logic](#-frontend-filter-logic)
- [Fonts](#-fonts)
- [Menus](#-menus)
- [Theme Structure](#-theme-structure)
- [Contributing](#-contributing)
- [License](#-license)
***
<br>



# ❔ About
This theme **keeps your time**: it provides main ecommerce pages ready to easy and fast customize (home, catalog, single page) and a few great **features which usually used or must have**.

#### ✔️ Pros
✓ easy to customize layout  
✓ load speed ready  
✓ retina ready  
✓ extended by a few cool features  

#### ‼️ Cons
frontend plugins are require code integration (shortcodes or functions usually) - due theme does not used hooks (i.e. just "install plugin and activate" - does not works)
***
<br>



# 🔧 Installation & Usage

### ✅ Requirements
Probably Starter will works with other plugin versions - but with versions below it's tested.
* [WordPress](https://wordpress.org/) >= 5.5
* [ACF](https://wordpress.org/plugins/advanced-custom-fields/) >= 5.9.0
  <details><summary>Show details</summary>
  You can to install: "ACF Pro" - all features available or Basic ACF - is not available Home Page features and you'll not see comment images in admin due gallery and repeater features are not available in free version.<br>
  After installation go to ACF and sync fields.
  <img src="https://github.com/chyvak1831/starter_img/blob/master/acf_sync.jpg?raw=true" alt="ACF sync settings"></details>
* [Classic Editor](https://wordpress.org/plugins/classic-editor/) >= 1.6
* [EWWW Image Optimizer](https://wordpress.org/plugins/ewww-image-optimizer/) >= 5.7.0
  <details><summary>Show details</summary>
  After installation go to EWWW setting and enable 'WebP Conversion' & 'Force WebP'.
  <img src="https://github.com/chyvak1831/starter_img/blob/master/ewww.jpg?raw=true" alt="EWWW settings"></details>
*  [TinyMCE Advanced](https://wordpress.org/plugins/tinymce-advanced/) >= 5.5.0
    <details><summary>Show details</summary>
    After installation go to settings
    <img src="https://github.com/chyvak1831/starter_img/blob/master/wysiwyg_01.jpg?raw=true" alt="TinyMCE settings 1">
    <img src="https://github.com/chyvak1831/starter_img/blob/master/wysiwyg_02.jpg?raw=true" alt="TinyMCE settings 2">
    <img src="https://github.com/chyvak1831/starter_img/blob/master/wysiwyg_03.jpg?raw=true" alt="TinyMCE settings 3">
    and import settings
    
      ```json
      {
        "settings": {
          "toolbar_1":"bold,italic,underline,forecolor,blockquote,bullist,numlist,alignleft,aligncenter,alignright,alignjustify,link,unlink,undo,redo,wp_adv",
          "toolbar_2":"formatselect,fontselect,fontsizeselect,styleselect,pastetext,removeformat,fullscreen",
          "toolbar_3":"",
          "toolbar_4":"",
          "options":"advlist,menubar_block,merge_toolbars",
          "plugins":"advlist",
          "toolbar_block":"core\/image,core\/image",
          "toolbar_block_side":"tadv\/sup,tadv\/sub,core\/strikethrough,core\/code,tadv\/mark,tadv\/removeformat",
          "panels_block":"tadv\/color-panel,tadv\/background-color-panel",
          "toolbar_classic_block":"formatselect,bold,italic,blockquote,bullist,numlist,alignleft,aligncenter,alignright,link,forecolor,backcolor,table,wp_help"
        },
        "admin_settings": {
          "options":"hybrid_mode,classic_paragraph_block,table_resize_bars,table_grid,table_tab_navigation,table_advtab",
          "disabled_editors":""
        }
      }
    ```
    </details>
* [WooCommerce](https://wordpress.org/plugins/woocommerce/) >= 4.4.1
* [W3 Total Cache](https://wordpress.org/plugins/w3-total-cache/) >= 0.14.4
* [Node.js](https://nodejs.org/) >= 14.8.0

### 🔧 Setup
1. Install  [Requirements](#requirements)
2. Install gulp globally (if it's not installed yet) - do it once
    ```bash
    npm i --global gulp-cli
    ```
3. Go to theme folder and run cmd/terminal and install packages
    ```bash
    npm i
    ```

### 🚀 Build commands
Default task (for development):
  ```bash
  gulp
  ```  
Production task:
  ```bash
  gulp production
  ```
***
<br>



# 💬 Comments
Used **default wordpress comment** feature extended by custom cool features: recaptcha, ajax for submit comment and load to front, image field, extended rating.  
### More documentation and examples *coming soon*!
***
<br>



# 🔍 Filters
Starter uses **default woo filter** feature (supported **price** and **attributes** filters) extended by custom cool features.  
Widget area for add filters to archive is **'Archive product'**.  
How to work with default woo filter widgets - there are a lot info in internet, for example official docs https://docs.woocommerce.com/document/woocommerce-widgets/ or see below *'Filter display types GIF example'*.
<br>

### 📄〽️〰️ Display types
Fitlers has two custom selects for setup display type on front.

#### How to use
1. Open widgets
2. Add fitler (or expand existing) and **setup display types** for dekstop and mobile (by default used 'list' type)
<details><summary><strong>Filter display types GIF example</strong></summary>
  <img src="https://github.com/chyvak1831/starter_img/blob/master/displaytype.gif?raw=true" alt="Filter: display type">
</details>

#### How it works?
To filter class fork ```inc\woocommerce\filterclass-wc-widget-layered-nav.php``` added ACF ```Filter widget``` for dekstop/mobile display types and added required minimum markup for dropdown and collapse. Filter diplay type settings handled via css ```woo/_filters.scss```.
<br>

### 🔴⚫🔵 Color filter

#### How to use
1. Open any attribute
2. Add color
<details><summary><strong>Color filter GIF example</strong></summary>
  <img src="https://github.com/chyvak1831/starter_img/blob/master/colorfilter.gif?raw=true" alt="Color filter">
</details>

#### How it works?
To filter class fork ```inc\woocommerce\filterclass-wc-widget-layered-nav.php``` added ACF ```Color taxonomy``` and required minimum markup. Styled in file ```woo/_filters.scss```.
<br>

### 💭 Frontend filter logic
Default woo uses for filter links: by each click page reloads with new query string in URL.  
Starter **uses fork of default woo filters** ```inc\woocommerce\filterclass-wc-widget-layered-nav.php``` where link logic replaced into checkboxes: by each click filter only getting select status (checkbox checked or unchecked) without page reloading, i.e. **in fact filters are collects via js** ```filters.js```. When user selected filters - he can submit form and page reloads.
<details><summary><strong>Frontend filter logic GIF example</strong></summary>
  <img src="https://github.com/chyvak1831/starter_img/blob/master/colorfilter.gif?raw=true" alt="Frontend filter logic">
</details>

In future filters will be added ajax support so all will works without reloads. 

### Code
* ACF: ```Filter widget``` and ```Color taxonomy```
* css: ```woo/_filters.scss```
* js: ```filters.js```
* tpl:
    * ```woocommerce/archive-product.php```:
      * `<!-- get active filters - used when 'No products found' so .js_form_filter form is empty -->` - get active filters
      * `<!-- filters --`> - filters markup
    * ```woocommerce/content-widget-price-filter.php``` - ovverride default woo price filter tpl
* logic:
    * ```inc/woocommerce/filter/filter.php``` - unregister default attr fitler and register fork; customize price filter layout - add data from ACF; Change Price Filter Widget Increment; customize text in Sort select; Register Archive page widget area
    * ```inc/woocommerce/filter/class-wc-widget-layered-nav.php``` - fork of default woo Widget filter
***
<br>



# 🔠 Fonts
By default used 'Open Sans' font family.  

#### How to use
1. Select any **google fonts**
2. Copy-paste **embed code** into ```Appearance->Customize->Site Identity```
3. Add **one** default font-family - used by default for whole site and as default font in wysiwyg editor  
<details><summary><strong>Fonts GIF example</strong></summary>
  <img src="https://github.com/chyvak1831/starter_img/blob/master/fonts.gif?raw=true" alt="Fonts">
</details>

#### Benefits:  
✓ add any google font family so fast & easy  
✓ use any google font family in WYSIWYG. All fonts displays correctly in WYSIWYG.  
✓ use any font-weight! For example 'Open Sans' with font-weight: 100 displays in admin 'Open Sans Light'
<br>

#### Code
Whole code placed into file ```inc\tiny-mce-advanced.php comment``` "Google fonts feature"

***
<br>



# 📁 Theme structure

```bash
themes/starter/   # → Root of Starter theme
├── assets/                                 # → Theme assets: css, js, svg icons
│   ├── css/                                # → Autogenerated from scss/
│   ├── js/                                 # → Scripts
│   │   ├── blueimp/                        # → Fileuploader plugin
│   │   ├── modules/                        # → Custom script sources
│   │   │   ├── comment.js                  # → Script for comments
│   │   │   ├── common.js                   # → Different common functions
│   │   │   ├── filters.js                  # → Filter scripts (archive page)
│   │   │   ├── home_page.js                # → Custom homepage tpl scripts
│   │   │   ├── product_add_remove.js       # → Functions for add/remove button
│   │   │   ├── product_hover.js            # → Display image on product hover 
│   │   │   ├── single_product.js           # → Single product page functions
│   │   │   └── step_nav.js                 # → Script for faq prev/next navigation
│   │   ├── iosPreloadFix.js                # → Bugfix for replace 'preload' into 'stylesheet' in <link>
│   │   ├── list_plugins.js                 # → Collect plugins from node_modules/
│   │   ├── list_scripts.js                 # → Collect files from js/modules/
│   │   ├── plugins.js                      # → Autogenerated from list_plugins.js
│   │   └── scripts.js                      # → Autogenerated from list_scripts.js
│   ├── scss/                               # → Styles
│   │   ├── theme/                          # → All scss custom files
│   │   │   ├── components/                 # → Components
│   │   │   |   ├── _carousel.scss          # → Carousels
│   │   │   |   ├── _components.scss        # → Collect all component files
│   │   │   |   ├── _footer.scss            # → Footer
│   │   │   |   ├── _header.scss            # → Header
│   │   │   |   ├── _modal.scss             # → Modal
│   │   │   |   └── _wishlist.scss          # → TI wishlist plugin styles
│   │   │   ├── mixins/                     # → Mixins
│   │   │   |   ├── _ellipsis.scss          # → Ellipsis mixin (i.e. 3 dots at end ...)
│   │   │   |   ├── _flex_align.scss        # → Flex align mixin - widely used
│   │   │   |   ├── _img_item.scss          # → Make image centered and limited inside box
│   │   │   |   └── _mixins.scss            # → Collect all mixin files
│   │   │   ├── pages/                      # → Pages
│   │   │   |   ├── _faq.scss               # → FAQ page styles
│   │   │   |   ├── _home.scss              # → Custom homepage tpl styles
│   │   │   |   └── _pages.scss             # → Collect all page files
│   │   │   ├── snippets/                   # → Snippets
│   │   │   |   ├── _forms.scss             # → Form styles
│   │   │   |   ├── _images.scss            # → Image box classes for limit image size and object-fit
│   │   │   |   ├── _list.scss              # → Flex lists (for menus, social lists etc)
│   │   │   |   ├── _menus.scss             # → Menu prototyping styles
│   │   │   |   ├── _pagination.scss        # → WooCommerce pagination
│   │   │   |   ├── _scrollup.scss          # → Scrollup button
│   │   │   |   ├── _select2.scss           # → Select2: default woo component - used on checkout, account
│   │   │   |   ├── _snippets.scss          # → Collect all snippet files
│   │   │   |   └── _wp_accessibility.scss  # → Fork of twentyseventeen/style.css (2.0 Accessibility)
│   │   │   ├── woo/                        # → Woo
│   │   │   |   ├── _account.scss           # → Account pages
│   │   │   |   ├── _filters.scss           # → Filter - archive page
│   │   │   |   ├── _product_item.scss      # → Product item
│   │   │   |   ├── _rating.scss            # → Rating
│   │   │   |   ├── _single_product.scss    # → Single product styles
│   │   │   |   └── _woo.scss               # → Collect all woo files
│   │   │   ├── _common.scss                # → Common styles
│   │   │   └── _variables.scss             # → Bootstrap customization
│   │   ├── plugins.scss                    # → Bootstrap modules
│   │   ├── styles.scss                     # → Custom modules
│   │   └── wp_admin.scss                   # → Styles for wordpress admin
│   └── svg-icons.svg                       # → Svg icons - used for decor graphics in theme (i.e. not content)
├── inc/                                    # → PHP logic
│   ├── acf-json/                           # → Autogenerated ACF
│   ├── woocommerce/                        # → WooCommerce logic
│   │   ├── comment/                        # → Comment
│   │   │   ├── comment-backend.php         # → comment logic
│   │   │   ├── comment-customizer.php      # → customizer settings
│   │   │   └── comment.php                 # → comment functions
│   │   ├── filter/                         # → Filter
│   │   │   ├── class-wc-widget-layered-nav.php # → fork of default Widget filter
│   │   │   └── filter.php                  # → filter functions
│   │   └── woocommerce.php                 # → woo functions
│   ├── customizer.php                      # → WordPress customizer
│   ├── icon-functions.php                  # → Svg icon functions (fork of twentyseventeen/inc/icon-functions.php)
│   ├── image.php                           # → Image functions
│   ├── menu.php                            # → Menu functions
│   ├── recaptchalib.php                    # → Google recaptcha lib
│   ├── remove-wp-assets.php                # → Remove unnecessary WordPress assets
│   └── tiny-mce-advanced.php               # → WYSIWYG settings, improvements like font-family
├── node_modules/                           # → Autogenerated packages
├── templates/                              # → Page templates
│   ├── page-faq.php                        # → FAQ page template
│   └── page-home.php                       # → Home page template
├── woocommerce/                            # → WooCommerce ovveride templates
│   ├── single-product/                     # → Single product template parts
│   │   │   ├── add-to-cart/                # → 
│   │   │   |   └── variation-add-to-cart-button.php  # → 
│   │   │   ├── related.php                 # → 
│   │   │   └── up-sells.php                # → 
│   ├── archive-product.php                 # → Archive template
│   ├── content-widget-price-filter.php     # → Price filter template
│   ├── product-searchform.php              # → Search form template
│   ├── single-product.php                  # → Single product template
│   └── ti-wishlist-product-counter.php     # → TI wishlist counter template
├── woocommerce-custom/                     # → Custom additional templates
│   ├── comment/                            # → Comment files
│   │   ├── comment-form.php                # → 
│   │   ├── comment-image-modal.php         # → 
│   │   ├── comment-item.php                # → 
│   │   └── comment-section.php             # → 
│   ├── global/                             # → Different global template parts
│   │   ├── add-to-cart.php                 # → 
│   │   ├── product-item.php                # → 
│   │   └── rating.php                      # → 
│   └── single-image-modal.php              # → Single image modal template
├── 404.php                                 # → 404 page template
├── config.js                               # → Configs for gulpfile.js
├── footer.php                              # → Footer template
├── functions.php                           # → Theme functions
├── gulpfile.js                             # → Gulp tasks
├── header.php                              # → Header template
├── index.php                               # → Theme default index file
├── package.json                            # → Node.js dependencies and scripts
├── page.php                               # → Default page template
├── README.md                              # → Readme (this current file)
├── screenshot.jpg                         # → Theme screenshot for WP admin
└── style.css                              # → Theme meta information
```
***
<br>



# 🤝 Contributing
Please open an issue first to discuss what you would like to change.
***
<br>



# 📘 License
[MIT](https://choosealicense.com/licenses/mit/)
