Starter uses **default woo filter** feature (supported **price** and **attributes** filters) extended by custom cool features.  
Widget area for add filters to archive is **'Archive product'**.  
How to work with default woo filter widgets - there are a lot info in internet, for example official docs https://docs.woocommerce.com/document/woocommerce-widgets/.
<br><br>



### Display types 📄〽️〰️
Fitlers has two custom selects for setup display type on front.

#### How to use
1. Open widgets
2. Add fitler (or expand existing) and **setup display types** for dekstop and mobile (by default used 'list' type)
<details id="filter_display_type_example"><summary><strong>Filter display types example</strong></summary>
	<a href="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/filter/filter_display_type.mp4">Download this video example</a><br>
	<img width="600" src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/filter/filter_display_type.gif" alt="Filter: display type">
</details>

#### How it works?
To the filter class fork `inc\woocommerce\filter\class-wc-widget-layered-nav.php` added ACF `Filter widget` for dekstop/mobile display types and added required minimum markup for dropdown and collapse. Filter diplay type settings handled via css `assets\scss\theme\woo\_filters.scss`.
<br><br><br>



### Color filter 🔴⚫🔵

#### How to use
1. Open any attribute
2. Add color
<details><summary><strong>Color filter example</strong></summary>
	<a href="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/filter/filter_color.mp4">Download this video example</a><br>
	<img width="600" src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/filter/filter_color.gif" alt="Filter: color">
</details>

#### How it works?
To filter class fork `inc\woocommerce\filterclass-wc-widget-layered-nav.php` added ACF `Color taxonomy` and required minimum markup. Styled in file `assets\scss\theme\woo\_filters.scss`.
<br><br><br>



### Frontend filter logic 💭
Default woo uses for filter links: by each click page reloads with new query string in URL.  
Starter **uses fork of default woo filters** `inc\woocommerce\filterclass-wc-widget-layered-nav.php` where link logic replaced into checkboxes: by each click filter only getting select status (checkbox checked or unchecked) without page reloading, i.e. **in fact filters are collects via js** `assets\js\modules\filters.js`. When user selected filters - he can submit form and page reloads.
<details><summary><strong>Frontend filter logic example</strong></summary>
	<a href="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/filter/filter_demonstration.mp4">Download this video example</a><br>
	<img width="600" src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/filter/filter_demonstration.gif" alt="Filter: frontend logic">
</details>

In future for filters will be added ajax support so all will works without reloads. 
<br><br><br>



### Code
* ACF: `Filter widget` and `Color taxonomy`
* css: `assets\scss\theme\woo\_filters.scss`
* js: `assets\js\modules\filters.js`
* tpl:
    * `woocommerce\archive-product.php`:
      * `<!-- get active filters - used when 'No products found' so .js_form_filter form is empty -->` - get active filters
      * `<!-- filters --`> - filters markup
    * `woocommerce\content-widget-price-filter.php` - ovverride default woo price filter tpl
* logic:
    * `inc\woocommerce\filter\filter.php` - unregister default attr fitler and register fork; customize price filter layout - add data from ACF; Change Price Filter Widget Increment; customize text in Sort select; Register Archive page widget area
    * `inc\woocommerce\filter\class-wc-widget-layered-nav.php` - fork of default woo Widget filter