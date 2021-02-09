# Ancho dinamico JavaScript

```javascript
function fullWidthRow() {
        var $elements = jQuery('[data-vc-full-width="true"]');
        jQuery.each($elements, function(key, item) {
            var $el = jQuery(this);
            $el.addClass("vc_hidden");
            var $el_full = $el.next(".vc_row-full-width");
            if ($el_full.length || ($el_full = $el.parent().next(".vc_row-full-width")), $el_full.length) {
                var padding, paddingRight, el_margin_left = parseInt($el.css("margin-left"), 10),
                    el_margin_right = parseInt($el.css("margin-right"), 10),
                    offset = 0 - $el_full.offset().left - el_margin_left,
                    width = jQuery(window).width();
                if ("rtl" === $el.css("direction") && (offset -= $el_full.width(), offset += width, offset += el_margin_left, offset += el_margin_right), $el.css({
                        position: "relative",
                        left: offset,
                        "box-sizing": "border-box",
                        width: width
                    }), !$el.data("vcStretchContent")) "rtl" === $el.css("direction") ? ((padding = offset) < 0 && (padding = 0), (paddingRight = offset) < 0 && (paddingRight = 0)) : ((padding = -1 * offset) < 0 && (padding = 0), (paddingRight = width - padding - $el_full.width() + el_margin_left + el_margin_right) < 0 && (paddingRight = 0)), $el.css({
                    "padding-left": padding + "px",
                    "padding-right": paddingRight + "px"
                });
                $el.attr("data-vc-full-width-init", "true"), $el.removeClass("vc_hidden"), jQuery(document).trigger("vc-full-width-row-single", {
                    el: $el,
                    offset: offset,
                    marginLeft: el_margin_left,
                    marginRight: el_margin_right,
                    elFull: $el_full,
                    width: width
                })
            }
        }), jQuery(document).trigger("vc-full-width-row", $elements)
    }

    jQuery(document).ready(function(){
        fullWidthRow();
    });

    jQuery(window).resize(function(){
        fullWidthRow();
    });
```
    
```html
  <div class="container">
    <div class="cari-main-banner" data-vc-full-width="true" data-vc-full-width-init="true">
      <div class="cari-main-control">
        <p class="cari-main-txt"><?=get_field('home_find_your_title')?></p>
        <p class="cari-main-txt last-child"><?=get_field('home_find_your_subtitle')?></p>
        <a href="<?=get_field('home_find_your_link_url')?>" class="cari-main-link-white"><?=get_field('home_find_your_link_text')?></a>
      </div>
    </div>
    <div class="vc_row-full-width vc_clearfix"></div>
  </div>
 ```
