### Overall
Starter uses recaptcha v2.  
Google recaptcha keys are required and available to setup in `Customizer->WooCommerce->Recaptcha`.
<details><summary>Show screenshot</summary>
 <img src="https://raw.githubusercontent.com/wiki/chyvak1831/starter/archive/v1.1.0/screenshots/recaptcha.jpg" alt="Recaptcha">
</details>

Please notice: **recaptcha loads lazyload** when user starts to interact with form (for avoid influence on pagespeed).
<br><br><br>



### How to add recaptcha  
**Frontend of recaptcha** is universal for all forms, just add these **3 lines of markup to each of your form** where you need recaptcha:
```php
<input type="hidden" class="js_recaptcha_input">
<div class="g-recaptcha" data-callback="recaptchaCallback" data-recaptchapublickey="<?php echo esc_attr( get_theme_mod( 'public_recaptcha_key' ) ); ?>"></div>
<div class="invalid-feedback"><?php esc_html_e( 'This field is required.', 'starter' ); ?></div>
```
Also you can to **add markup via wordpress actions** (like it done for login/register/lostpassword in Starter).  
**Backend validation of recaptcha** is different for each form, below listed files of backend validation (logic files) for **comment, login/register/lostpassword pages** in Starter.
<br><br><br>



### Code
 * logic: `inc\recaptcha.php` - recaptcha function, customizer, **login/register/lostpassword markup and backend validation**
 * js: `assets\js\modules\recaptcha.js` - load recaptcha on click, render, front validation

#### Comment
 * logic: `inc\woocommerce\comment\comment-backend.php` - backend validation of recaptcha
 * tpl: `woocommerce-custom\comment\comment-form.php` - recaptcha markup
 * js: `assets\js\modules\comment.js` - add class is-invalid when recaptcha invalid (when came from backend) and reset recaptcha