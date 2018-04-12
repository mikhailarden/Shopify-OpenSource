# Shopify Blog Sidebar Filter
Version 1.0.0 
Originally created by: Suman K.C
Maintained and extended by MICA Interactive

## Use case

Used when merchant requires a sidebar that filters the blogs based on tags. Useful for merchants who want to extend SEO and content for their stores. Uses liquid and is created as a section. 


### 1.Blog Categories
Create a `blog-sidebar`  section and associate on blog page.

Navigate to section's folder and add a template named blog-sidebar.liquid. 
Note: You will need to include the sidebar in the blog.liquid file. 
```
<div class="page-width">
  <div class="blog-holder">
      <div class="blog-listing-left">
    {% section 'blog-template' %}
      </div>
      <div class="blog-sidebar-right">
    {% section 'blog-sidebar' %}
      </div>
	</div>
</div>

```

Within `blog-sidebar.liquid` add schema below which would add a textarea field to list tags that we are considering as a blog category.

```
{% schema %}
  {
    "name": "Sidebar",
    "settings": [
      {
        "type": "textarea",
        "id": "blog_category",
        "label": "Blog category",
	"info": "categories are selective tags. Mention those selective tags seperated with comma above."
      }
    ]
  }
{% endschema %}

```

The above schema on blog-sidebar section would create a field on blog section on `customize theme`. (Online store > customize theme > navigate to blog page on the preview section to view)

Now add tags that you are considering as blog categories separated with comma, in the above screenshot `summer` and `another` are tags. on the same blog-sidebar section add these codes

```
<div id="sidebar-categories">
	{% comment %}
      Blog categories
    {% endcomment %}
    {% if blog.all_tags.size > 0 %}
      <h3 class="h4">{{ 'blogs.sidebar.categories' | t }}</h3>
      <ul class="blog-listing">
        {% for tag in blog.all_tags %}
        	{% if section.settings.blog_category contains tag %}  
              {% if current_tags contains tag %}
              <li>{{ tag }}</li>
              {% else %}
              <li>{{ tag | link_to_tag: tag }}</li>
              {% endif %}
        	{% endif %}
        {% endfor %}
      </ul>
    {% endif %}
</div>

```

The code above would print tags that we have separated as categories.

### 2. Blog archives
For archives we are doing this trick of adding year and month as a tags on the blog post and listing them by grouping.

On a blog post add a `{{year}} { {month}}` as a tags. for. eg `2017 january` and add this code below on same blog-sidebar section that would group and shows archives.

```
{% capture dates %}2013 2014 2015 2016 2017 2018 2019 2020{% endcapture %}
<div id="sidebar-archives">
  {% capture tags %}{% for tag in blog.all_tags %}{{ tag }} {% endfor %}{% endcapture %}

  <div id="archives" class="widget">
    <h3 class="h4">Archives</h3>
    {% if tags contains '2017' %}
          <span>2017</span><ul>
          {% for tag in blog.all_tags reversed %}
              {% assign check = tag | downcase | split:' ' %}
              {% if dates contains check[0] and check[0] == '2017' %}
    			<li><a href="{{ blog.url }}/tagged/{{ tag | handle }}">{{ check[1] }}</a></li>
              {% endif %}
    	  {% endfor %}</ul>
      {% endif %}
      {% if tags contains '2016' %}
    	<span>2016</span><ul>
          {% for tag in blog.all_tags reversed %}
              {% assign check = tag | downcase | split:' ' %}
              {% if dates contains check[0] and check[0] == '2016' %}
    			<li><a href="{{ blog.url }}/tagged/{{ tag | handle }}">{{ check[1] }}</a></li>
              {% endif %}
  		  {% endfor %}</ul>
      {% endif %}
      {% if tags contains '2014' %}
          <span>2014</span><ul>
          {% for tag in blog.all_tags reversed %}
              {% assign check = tag | downcase | split:' ' %}
              {% if dates contains check[0] and check[0] == '2014' %}
    				<li><a href="{{ blog.url }}/tagged/{{ tag | handle }}">{{ check[1] }}</a></li>
              {% endif %}
    	  {% endfor %}</ul>
      {% endif %}
      {% if tags contains '2013' %}
          <span>2013</span><ul>
          {% for tag in blog.all_tags reversed %}
              {% assign check = tag | downcase | split:' ' %}
              {% if dates contains check[0] and check[0] == '2013' %}
  					<li><a href="{{ blog.url }}/tagged/{{ tag | handle }}">{{ check[1] }}</a></li>
              {% endif %}
		  {% endfor %}</ul>
      {% endif %}
  </div> <!-- end #archives -->
</div>
```

### 3. Tags
Tags are default by shopify but direct listing would list the categories and archives tags as well. so we will filter them out.

```
<div id="sidebar-tags">
	{% comment %}
      Blog tags
    {% endcomment %}
    {% if blog.all_tags.size > 0 %}
      <h3 class="h4">{{ 'blogs.sidebar.tags' | t }}</h3>
      <ul class="blog-listing">
        {% for tag in blog.all_tags %}
        	{% unless section.settings.blog_category contains tag %}
        	  		{% assign tag = tag |downcase %}
                  {% unless tag contains 'january' or tag contains 'february' or tag contains 'march' or tag contains 'april'  or tag contains 'may'  or tag contains 'june'  or tag contains 'july'  or tag contains 'august'  or tag contains 'september'  or tag contains 'october'  or tag contains 'november'  or tag contains 'december' %}
                    {% if current_tags contains tag %}
                    <li>{{ tag }}</li>
                    {% else %}
                    <li>{{ tag | link_to_tag: tag }}</li>
                    {% endif %}
                  {% endunless %}
        		
        	{% endunless %}
        {% endfor %}
      </ul>
    {% endif %}
</div>
 ```
