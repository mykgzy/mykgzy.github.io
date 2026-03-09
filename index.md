---
publish: true
---
   
# 欢迎来到我的技术自留地
   
> 持续学习，记录点滴。本站点的目录与文章均由 Obsidian 自动发布，并通过云端动态渲染生成。
   
---
   
{% assign grouped_pages = site.pages | group_by_exp: "p", "p.dir" %}
   
{% for group in grouped_pages %}
  {% comment %} 1. 先进行 URL 解码，恢复中文 {% endcomment %}
  {% assign raw_dir = group.name | url_decode %}
     
  {% comment %} 2. 去掉开头的第一个斜杠 {% endcomment %}
  {% assign dir_path = raw_dir | remove_first: "/" %}

  {% comment %} 3. 使用 split 按照斜杠切分成数组，然后再用漂亮的箭头 join 起来 {% endcomment %}
  {% assign parts = dir_path | split: "/" %}
  {% assign display_name = parts | join: " ➔ " %}

  {% comment %} 过滤掉根目录和系统文件夹 {% endcomment %}
  {% if display_name != "" and display_name != "assets" and display_name != "images" and display_name !="assetscss" %}
       
## 🗂️ {{ display_name }}
       
{% for page in group.items %}
* [{{ page.title | default: page.name | replace: ".md", "" }}]({{ site.baseurl }}{{ page.url }})
{% endfor %}
       
{% endif %}
{% endfor %}
   
---
**[关于我](关于)** | **[归档](归档)**