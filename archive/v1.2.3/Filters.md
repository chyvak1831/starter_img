**Default woo filters** extended by custom cool features.  
Widget area for add filters to archive is **'Archive product'**.  
How to work with default woo filter widgets - there are a lot info in internet, for example official docs https://docs.woocommerce.com/document/woocommerce-widgets/.
<br><br>



### Ajax 💭
Starter allows to enable **ajax for sort/filter and pagination without plugins**!  
By default this feature disabled, can be enabled into customizer.
<details><summary><strong>Where to enable ajax for sort/filter & pagination</strong></summary>
	<img width="600" src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/screenshots/filter/since1.2.0/filter_ajax.jpg" alt="Filter: Ajax">
</details>

#### How it works?
Everything handled via js `assets\js\modules\archive.js`: by click requests related page (html) and injects into page.
<br><br><br>



### Display types 📄〽️〰️
Fitlers has two custom selects for setup display type on front.

#### How to use
1. Open widgets
2. Add fitler (or expand existing) and **setup display types** for dekstop and mobile (by default used 'list' type)
<details id="filter_display_type_example"><summary><strong>Filter display types example</strong></summary>
	<a href="https://raw.githubusercontent.com/chyvak1831/starter_img/master/screenshots/filter/filter_display_type.mp4">Download this video example</a><br>
	<img width="600" src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/screenshots/filter/filter_display_type.gif" alt="Filter: display type">
</details>

#### How it works?
Filter markup is customized in file `inc\filter.php`: added ACF `Filter widget` for dekstop/mobile display types and added required minimum markup for dropdown and collapse. Filter diplay type settings handled via css `assets\scss\theme\woo\_filters.scss`.
<br><br><br>



### Color filter 🔴⚫🔵

#### How to use
1. Open any attribute
2. Add color
<details><summary><strong>Color filter example</strong></summary>
	<a href="https://raw.githubusercontent.com/chyvak1831/starter_img/master/screenshots/filter/filter_color.mp4">Download this video example</a><br>
	<img width="600" src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/screenshots/filter/filter_color.gif" alt="Filter: color">
</details>

#### How it works?
Filter markup is customized in file `inc\filter.php`: added ACF `Color taxonomy` and required minimum markup. Styled in file `assets\scss\theme\woo\_filters.scss`.
<br><br><br>



### Code
* ACF: `Filter widget` and `Color taxonomy`
* css: `assets\scss\theme\woo\_filters.scss`
* js: `assets\js\modules\archive.js`
* tpl:
    * `woocommerce\archive-product.php`:
      * `starter_archive_url` - get archive canonical URL
      * `<!-- filters --`> - filters markup
    * `woocommerce\content-widget-price-filter.php` - ovverride default woo price filter tpl
* logic:
    * `inc\woocommerce\filter\filter.php` - customize filter layout; Change Price Filter Widget Increment; customize text in Sort select; Register Archive page widget area