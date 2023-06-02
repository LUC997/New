function product_variation_price()
{
	?>
	<script>
		jQuery(document).ready(function () {
			jQuery(".woocommerce-page ul.products li").each(function () {
				if (jQuery(this).hasClass("product-type-variable")) {
					var pricehtml = jQuery(this).find('.price').first().removeClass('price').addClass('updated-price');
				var currentLi = jQuery(this);
				var variationsForm = currentLi.find('.variations_form');
				var newPrice = currentLi.find('.updated-price');
				pricehtml.html(newPrice);
				// when variation is found, do something
				variationsForm.on('found_variation', function (event, variation) {
					newPrice.html(variation.price_html);
				});
				}
			});
		});
	</script>
	<?php
}  
add_action('wp_footer', 'product_variation_price');
