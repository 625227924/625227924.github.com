{% comment %}<!--
The categories_list include is a listing helper for categories.
Usage:
  1) assign the 'categories_list' variable to a valid array of tags.
  2) include categories_list.md
  example:
    <ul>
  	  {% assign categories_list = site.categories %}  
  	  {% include categories_list.md %}
  	</ul>
  
  Notes: 
    Categories can be either a Hash of Category objects (hashes) or an Array of category-names (strings).
    The encapsulating 'if' statement checks whether categories_list is a Hash or Array.
    site.categories is a Hash while page.categories is an array.
    
-->{% endcomment %}

{% if categories_list.first[0] == null %}
    {% for category in categories_list %} 
        <li><a class="categories" data-name="{{ category }}" href="{{ site.url }}{{ site.categories_path }}#{{ category }}-category-ref">
            {{ category | join: "/" }} <span>{{ site.categories[category].size }}</span>
        </a></li>
    {% endfor %}
{% else %}
    {% for category in categories_list %} 
        <li><a class="categories" data-name="{{ category[0] }}" href="{{ site.url }}{{ site.categories_path }}#{{ category[0] }}-category-ref">
        {{ category[0] | join: "/" }} <span>{{ category[1].size }}</span>
        </a></li>
    {% endfor %}
{% endif %}
{% assign categories_list = nil %}









