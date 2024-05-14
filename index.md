---
---
# Leiðbeiningar

{% for category in site.data.nav_is %}
## {{ category.name  }}

{% for guide in category.guides %}
* [{{ guide.title }}]({{guide.path || relative_url }})
{% endfor %}

{% endfor %}
