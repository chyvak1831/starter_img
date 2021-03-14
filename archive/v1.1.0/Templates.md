1. The main difference in development in Starter is **custom templates**: instead of hell with hooks just use **raw data** from woo!  
   For example: instead of getting thumbnails with 💩-markup - just get ids array and use with any your own markup:
   ```php
   $starter_thumbnails = $product->get_gallery_image_ids() //get thumbnail ids on single page
   ```
   and use it with any markup
   ```php
   <?php foreach ( $starter_thumbnails as $starter_thumbnail_img ) : ?>
     <picture>
         <?php
           echo starter_img_func([
             'img_src'   => 'w200',
             'img_sizes' => '70px',
             'img_id'    => $starter_thumbnail_img
           ]);
         ?>
     </picture>
   <?php endforeach; ?>
   ```
2. Theme contain custom tempaltes for **home, archive, single**.  
3. **Account/cart/checkout** are not ovverrided, they are styled using css (and a bit js to add css classes) because usually these pages very similar and *it's not easy* to get raw data and *to maintain*  (due so much logic present on checkout for example).
<br>



### Code
   * **folder `templates`** contains page templates, except is `page.php` (default page template) & `index.php` (used by default for frontpage) - both are default templates and must be at root
   * **folder `woocommerce`** contain woocommerce overrides: some templates slightly changed like `woocommerce\product-searchform.php`, but some is in fact 100% custom template like `woocommerce\single-product.php`
   * **folder `woocommerce-custom`** contain custom template's files for woocommerce
   * **root of theme** contain `footer.php`, `header.php`, `index.php`, `page.php`