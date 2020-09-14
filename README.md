# Starter

Starter theme for WooCommerce.  
Open source, free to use - [MIT](https://choosealicense.com/licenses/mit/) license.



## Table of content

- [Why you should to use theme](#why)
- [Installation](#installation)
  - [Requirements](#requirements)
  - [Highly recommended/integrated to theme plugins](#recommended_plugins)
- [Contributing](#contributing)
- [License](#license)



## Why you should to use theme?
This theme keeps your time: it provides main ecommerce pages ready to easy and fast customize (home, catalog, single page) and a few great features which usually used or must have.

#### Pros
* easy to customize layout
* load speed ready
* retina ready
* extended by a few cool features

#### Cons
* frontend plugins are require code integration (shortcodes or functions usually) - due theme does not used hooks (i.e. just "install plugin and activate" - does not works)



## Installation

#### Requirements
Probably theme will works with other plugin versions - but with versions below it's tested.
* [WordPress](https://wordpress.org/) >= 5.5
* [ACF](https://wordpress.org/plugins/advanced-custom-fields/) >= 5.9.0
  <details><summary>Show details</summary>
  You can to install: "ACF Pro" - all features available or Basic ACF - is not available Home Page features and you'll not see comment images in admin due gallery and repeater features are not available in free version.<br>
  After installation go to ACF and sync fields.
  ![ACF sync settings](https://github.com/chyvak1831/starter_img/blob/master/acf_sync.jpg?raw=true)</details>
* [Classic Editor](https://wordpress.org/plugins/classic-editor/) >= 1.6
* [EWWW Image Optimizer](https://wordpress.org/plugins/ewww-image-optimizer/) >= 5.7.0
  <details><summary>Show details</summary>
  After installation go to EWWW setting and enable 'WebP Conversion' & 'Force WebP'.![EWWW settings](https://github.com/chyvak1831/starter_img/blob/master/ewww.jpg?raw=true)</details>
*  [TinyMCE Advanced](https://wordpress.org/plugins/tinymce-advanced/) >= 5.5.0
    <details><summary>Show details</summary>
    After installation go to settings
    ![TinyMCE settings 1](https://github.com/chyvak1831/starter_img/blob/master/wysiwyg_01.jpg?raw=true)
    ![TinyMCE settings 2](https://github.com/chyvak1831/starter_img/blob/master/wysiwyg_02.jpg?raw=true)
    ![TinyMCE settings 3](https://github.com/chyvak1831/starter_img/blob/master/wysiwyg_03.jpg?raw=true)
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


#### Setup
1. Install  [Requirements](#requirements)
2. Install gulp globally (if is not installed yet) - do it once
```bash
npm i --global gulp-cli
```
3. Go to theme folder and run cmd/terminal and install packages
```bash
npm i
```

#### Build commands
* Default task (for development):
```bash
gulp
```
* Production task:
```bash
gulp production
```

## Contributing
Please open an issue first to discuss what you would like to change.

## License
[MIT](https://choosealicense.com/licenses/mit/)