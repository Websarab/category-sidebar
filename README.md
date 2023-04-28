# category-sidebar


<div class="acnav">
  <h2 class="category_title_Sel"> {{ section.settings.cat }} </h2>
<ul class="acnav__list acnav__list--level1">
{% for link in section.settings.menu.links %}
{% if link.links == blank %}
<li class="has-children">
  <a class="toggles new-sub"  href="{{ link.url }}">{{ link.title }}</a>
  
{% if link.links != blank %}
  <ul class="acnav__list acnav__list--level2">
    {% for child_link in link.links %}  
    <li class="">      
<a class="acnav__link acnav__link--level2" href="{{ child_link.url }}">{{ child_link.title }}</a>
    {% if child_link.links != blank %}
     <ul class="acnav__list acnav__list--level3">
      {% for grandchild_link in child_link.links %}  
        <li><a class="acnav__link acnav__link--level3" href= "{{ grandchild_link.url }}">{{ grandchild_link.title }}</a></li>
      {% endfor %}
      </ul>
    {% endif %}   
       
    </li>
    {% endfor %}
  </ul> 
{% endif %} 
</li>
  {% else %}
  <li class="has-children">
  <a class="toggles new-sub"  href="{{ link.url }}">{{ link.title }}</a>
  <span class="acnav__label">+</span>
{% if link.links != blank %}
  <ul class="acnav__list acnav__list--level2">
    {% for child_link in link.links %}  
    <li>
      
 <a class="acnav__link acnav__link--level2"href="{{ child_link.url }}">{{ child_link.title }}</a>
  </li>
    {% endfor %}
  </ul> 
{% endif %} 
</li>
  {% endif %}
{% endfor %}
</ul>
  
  </div>

<style>  
    .acnav__list--level2 {
    display: none;
  
    .is-open   {
      display: block;
    }
  }
  </style>

  <script>
    $( document ).ready(function() {
  $('.acnav__label').click(function () {
	var label = $(this);
	var parent = label.parent('.has-children');
	var list = label.siblings('.acnav__list');

	if ( parent.hasClass('is-open') ) {
    label.removeClass("icon-new");
		list.slideUp('200');
		parent.removeClass('is-open');
	}
	else {
     label.addClass("icon-new");
		list.slideDown('200');
		parent.addClass('is-open');
	}
});
      });
   </script>
