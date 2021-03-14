# Navitaion

- [Default WordPress Discussion feature](#default-wordpress-discussion-feature)
  - [Default post settings](#default-post-settings)
  - [Email me whenever, Before a comment appears, Comment Moderation, Disallowed Comment Keys](#email-me-whenever-before-a-comment-appears-comment-moderation-disallowed-comment-keys)
  - [Avatars](#avatars)
- [Default WooCommerce Reviews feature](#default-woocommerce-reviews-feature)
  - [Enable reviews](#enable-reviews)
  - [Product ratings](#product-ratings)
  - [Single product page](#single-product-page)
- [Custom features](#custom-features)
  - [Extended rating](#extended-rating)
  - [Low-rating popup](#low-rating-popup)
  - ["Privacy Policy" checkbox](#privacy-policy-checkbox)
  - [Fileuploader](#fileuploader)
  - [Ajax load comments](#ajax-load-comments)
  - [Ajax load comment image modal](#ajax-load-comment-image-modal)
  - [Ajax send comment](#ajax-send-comment)
  - [Validation](#validation)
- [Code](#code)
***
<br>




Starter uses **default WordPress comment** & **default Woo reviews** features extended by custom *cool* features: extended rating, low-rating popup, privacy checkbox, recaptcha, fileuploader, ajax for submit comment and load to front.  

# Default WordPress Discussion feature
Default WP "discussion" setting located at `/wp-admin/options-discussion.php`.  
**Aren't all** default features supports by Starter.

### Default post settings
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/01.jpg" alt="Comment - Default post settings">

* **"Attempt to notify any blogs linked to from the post"** and **"Allow link notifications from other blogs (pingbacks and trackbacks) on new posts"** - is recommended to keep disabled (why - read [here](https://themeisle.com/blog/wordpress-pingbacks/)).  
* **"Allow people to submit comments on new posts"** - only changing default state of Woo **"Advanced->Enable reviews"** setting when new product is been creating ([see](#single-product-page))
<br>


### Other comment settings
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/03.jpg" alt="Comment - Other comment setting">

* **Comment author must fill out name and email** - it require name&email for submit comment.
<br>Files:
    * `woocommerce-custom\comment\comment-form.php`.
* **Users must be registered and logged in to comment (Signup has been disabled. Only members of this site can comment.)** - when enabled for unlogged users form does not available and displays related message.
<br>Files:
    * `woocommerce-custom\comment\comment-section.php`.
* **Automatically close comments on posts older than**, **Show comments cookies opt-in checkbox, allowing comment author cookies to be set**, **Enable threaded (nested) comments** - does not supports.
* **Break comments into pages with {#} top level comments per page** - in Starter sets how many comments load by default and by click "Show more".
<br>Files:
    * `woocommerce-custom\comment\comment-section.php`
    * `inc\woocommerce\comment\comment.php`.
* **and the {last|first} page displayed by default** - does not supports (due no pagination for comments).
* **Comments should be displayed with the {newer|older} comments at the top of each page** - comment order: display older/newer comments on single page.
<br>Files:
    * `woocommerce-custom\comment\comment-section.php`
    * `inc\woocommerce\comment\comment.php`.
<br>


### Email me whenever, Before a comment appears, Comment Moderation, Disallowed Comment Keys
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/04.jpg" alt="Comment - Moderation">

All these settings pure backend - so works as expected.
<br><br>


### Avatars
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/05.jpg" alt="Comment - Avatar">

Does not supports
<br><br><br><br><br>




# Default WooCommerce Reviews feature
Default woo "reviews" setting located at `/wp-admin/admin.php?page=wc-settings&tab=products` and on each single product in "Advanced" tab.  
**All** default woo features supports by Starter.

### Enable reviews
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/06.jpg" alt="Woo reviews">

* **Enable product reviews** - enable/disable all reviews for all products: when disabled in loops and on single page displays nothing.
<br>Files:
    * `woocommerce-custom\global\product-item.php`
    * `woocommerce\single-product.php`.
* **Show "verified owner" label on customer reviews** - display verified owners badge in review.
<br>Files:
    * `woocommerce-custom\comment\comment-item.php`.
* **Reviews can only be left by "verified owners"** - allow reviews for verified owners only.
<br>Files:
    * `woocommerce-custom\comment\comment-item.php`
    * `inc\woocommerce\comment\comment-backend.php` (due [woo bug](https://github.com/woocommerce/woocommerce/issues/28352) )
<br>


### Product ratings
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/07.jpg" alt="Woo rating">

* **Enable star rating on reviews** - enable/disable rating.
<br>Files:
    * `inc\woocommerce\comment\comment-backend.php`
    * `woocommerce-custom\comment\comment-form.php`
    * `woocommerce-custom\comment\comment-item.php`
    * `woocommerce-custom\global\product-item.php`
    * `woocommerce\single-product.php`.
* **Star ratings should be required, not optional** - require rating when enabled.
<br>Files:
    * `inc\woocommerce\comment\comment-backend.php`
    * `woocommerce-custom\comment\comment-form.php`.
<br>


### Single product page
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/02.jpg" alt="Comment - Single Product">

Works **only when [reviews enabled for all products](#enable-reviews)** - allow to disable reviews only for some certain products.  
Files:
 * `woocommerce-custom\global\product-item.php`
 * `woocommerce\single-product.php`.
<br><br><br><br><br>




# Custom features
Comments extended by a few _cool_ features, each can be enabled/disabled in customizer `/wp-admin/customize.php` -> WooCommerce -> Comments.

### Extended rating
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/08.jpg" alt="Comment - Extended rating">

Extend default rating up to 3 separate ratings.  
**Default rating**: available to change by changing value in inputs `.js_rating_input`.  
**Star item width**: because rating calculates by js - _it's require to know the width of each star_, by default it's 22px. If you need to change star item width - it's require to update attribute** `data-elem-width="22"` for correct rating functional.  
Files:
 * `woocommerce-custom\global\rating.php`
 * `inc\woocommerce\comment\comment-backend.php`
 * `inc\woocommerce\comment\comment-customizer.php`
 * `woocommerce-custom\comment\comment-form.php`
 * `woocommerce-custom\comment\comment-item.php`
 * ACF `Comment additional fields`
 * `assets\js\modules\comment.js`
 * `assets\scss\theme\woo\_rating.scss`
 * `assets\scss\theme\woo\_comment.scss`.
<br><br>


### Low-rating popup
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/09.jpg" alt="Comment - Low-rating popup">

Display popup when low rating comment - low rating is < 4 by default (can be changed in attribute `data-minimum-rating="4"`).  
Files:
 * `inc\woocommerce\comment\comment-customizer.php`
 * `woocommerce-custom\comment\comment-form.php`
 * `assets\js\modules\comment.js`
 * `assets\scss\theme\components\_modal.scss`.
<br><br>


### "Privacy Policy" checkbox
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/10.jpg" alt="Comment - 'Privacy Policy' checkbox">

Block sending comment without privacy agreeing.  
Files:
 * `inc\woocommerce\comment\comment-backend.php`
 * `inc\woocommerce\comment\comment-customizer.php`
 * `woocommerce-custom\comment\comment-form.php`
 * `assets\js\modules\comment.js`.
<br><br>


### Fileuploader
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/12.jpg" alt="Comment - File">

Files:
 * `inc\woocommerce\comment\comment-backend.php`
 * `inc\woocommerce\comment\comment-customizer.php`
 * `woocommerce-custom\comment\comment-form.php`
 * `assets\js\modules\comment.js`
 * ACF `Comment additional fields`
 * `assets\scss\theme\snippets\_forms.scss`
 * `assets\js\blueimp`- due [ios](https://stackoverflow.com/a/52079109/7569674) it's still require to use jquery lib, fileuploader uses jquery lib
<br><br>


### Ajax load comments
<img src="https://raw.githubusercontent.com/chyvak1831/starter_img/master/archive/v1.1.0/screenshots/comment/13.jpg" alt="Comment - Break comments">

If to setup default WordPress setting 'Break comments into pages with' (and when amount of comments > then setup number) - on single page in comments section appears button 'Show more', by click on this button comments loads via ajax.
Files:
 * `woocommerce-custom\comment\comment-section.php`
 * `woocommerce-custom\comment\comment-item.php`
 * `inc\woocommerce\comment\comment.php`
 * `assets\js\modules\comment.js`
<br><br>


### Ajax load comment image modal
Images in comments are clickable, by click loads image modal via ajax.
Files:
 * `woocommerce-custom\comment\comment-item.php`
 * `woocommerce-custom\comment\comment-image-modal.php`
 * `inc\woocommerce\comment\comment.php`
 * `assets\js\modules\comment.js`.
<br><br>


### Ajax send comment
Comments sends by ajax.
Files:
 * `woocommerce-custom\comment\comment-form.php`
 * `inc\woocommerce\comment\comment-backend.php`
 * `assets\js\modules\comment.js`
<br><br>


### Validation
**Frontend validation** processed by html5 `checkValidity()` (file `assets\js\modules\comment.js`) in cooperation with bootstrap validation for validate require fields, and for another validations (like email - has two different validations - required and must be valid) bootstrap extended by `.not_required_feedback` html class (file `assets\scss\theme\snippets\_forms.scss`).  
**Backend validation** processed by default `$comment->get_error_message()` and in file `inc\woocommerce\comment\comment-backend.php` for catch custom errors (privacy, recaptcha, images, extended rating).
Files:
 * `inc\woocommerce\comment\comment-backend.php`
 * `assets\scss\theme\snippets\_forms.scss`
 * `assets\js\modules\comment.js`
<br><br><br><br><br>




# Code
* ACF: `Comment additional fields`
* css:
    * `assets\scss\theme\woo\_rating.scss` - rating
    * `assets\scss\theme\woo\_comment.scss` - comment
    * `assets\scss\theme\components\_modal.scss` - low-rating popup
    * `assets\scss\theme\snippets\_forms.scss` - extended bootstrap validation and fileuploader
* js: `assets\js\modules\comment.js`.
* tpl:
    * `woocommerce-custom\global\rating.php` - rating template
    * `woocommerce-custom\global\product-item.php` - rating/count comment in loops
    * `woocommerce\single-product.php` - rating/comment on single, comments, comment form include
    * `woocommerce-custom\comment\comment-section.php` - wrapper for comments and comment form
    * `woocommerce-custom\comment\comment-item.php` - comment item
    * `woocommerce-custom\comment\comment-image-modal.php` - comment image modal
    * `woocommerce-custom\comment\comment-form.php` - comment form
* logic:
    * `inc\woocommerce\comment\comment.php` - ajax load comment and image comment modal
    * `inc\woocommerce\comment\comment-backend.php` - custom validations, save custom rating and images
    * `inc\woocommerce\comment\comment-customizer.php` - customizer settings.
* dependence - recaptcha:
    * `inc\recaptcha.php` - recaptcha customizer and function
    * `assets\js\modules\recaptcha.js` - recaptcha js