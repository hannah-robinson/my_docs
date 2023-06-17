---
date created: 2023-05-21
last updated: 2023-06-17
programming language: liquid
library or framework:
programme:
platform: shopify
tags: site speed, web performance, image optimisation, lazy loading, shopify
---

⬆ [[_Shopify_]]

You can use liquid to add lazy loading to all but the first image in a slider/carousel.
```html
 {% assign count = 0 %}

 {%- for block in section.blocks -%}

   {% assign count = count | plus: 1 %}
   
   {%- comment -%} Slide goes here. Inside <img/> tag add: 
   {% if count > 1 %} loading="lazy" {% endif %}
   {%- endcomment -%}
 {%- endfor -%}
```

```html
<div class="
	 slideshow__media 
	 {% if block.settings.image == blank %} placeholder{% endif %}"
	 >

  {%- if block.settings.image -%}

    <img
             srcset="{%- if block.settings.image.width >= 375 -%}{{ block.settings.image | image_url: width: 375 }} 375w,{%- endif -%}

             {%- if block.settings.image.width >= 550 -%}{{ block.settings.image | image_url: width: 550 }} 550w,{%- endif -%}

             {%- if block.settings.image.width >= 750 -%}{{ block.settings.image | image_url: width: 750 }} 750w,{%- endif -%}

             {%- if block.settings.image.width >= 1100 -%}{{ block.settings.image | image_url: width: 1100 }} 1100w,{%- endif -%}

             {%- if block.settings.image.width >= 1500 -%}{{ block.settings.image | image_url: width: 1500 }} 1500w,{%- endif -%}

             {%- if block.settings.image.width >= 1780 -%}{{ block.settings.image | image_url: width: 1780 }} 1780w,{%- endif -%}

             {%- if block.settings.image.width >= 2000 -%}{{ block.settings.image | image_url: width: 2000 }} 2000w,{%- endif -%}

             {%- if block.settings.image.width >= 3000 -%}{{ block.settings.image | image_url: width: 3000 }} 3000w,{%- endif -%}

             {%- if block.settings.image.width >= 3840 -%}{{ block.settings.image | image_url: width: 3840 }} 3840w,{%- endif -%}

             {{ block.settings.image | image_url }} {{ block.settings.image.width }}w"

  sizes="100vw"

  src="{{ block.settings.image | image_url: width: 1500 }}"
  {%- comment -%} Add lazylading to all but first slide image{%- endcomment -%}
  {% if count > 1 %} loading="lazy" {% endif %}

  class="{%- if block.settings.image_mob -%} hide--small{%- endif -%}"

  alt="{{ block.settings.image.alt | escape }}"

  width="{{ block.settings.image.width }}"

  height="{{ block.settings.image.width | divided_by: block.settings.image.aspect_ratio | round }}"

           >
%- else -%}
```

---

🏷 Tags: #🌱

🖇 Related links:
[[Lazy Loading]]
[[Images]]
[[Shopify]]
[[_Web Performance Optimisation_]]
[[Sliders - Carousels]]

