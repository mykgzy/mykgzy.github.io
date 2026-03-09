---
publish: true
---
  
# 欢迎来到我的技术自留地
   
   > 持续学习，记录点滴。本站点的目录与文章均由 Obsidian 自动发布，并通过云端动态渲染生成。
   
---
   
{% assign grouped_pages = site.pages | group_by_exp: "p", "p.dir" %}
   
{% for group in grouped_pages %}
  {% comment %} 清理目录两侧的斜杠，提取纯净的文件夹名称 {% endcomment %}
  {% assign dir_name = group.name | replace: "/", "" | url_decode %}
     
  {% comment %} 排除根目录(主页所在位置)以及存放图片的 assets 文件夹 {% endcomment %}
  {% if dir_name != "" and dir_name != "assets" and dir_name != "images"  and dir_name != "## assetscss" %}
       
## 🗂️ {{ dir_name }}
       
{% for page in group.items %}
-  [{{ page.title | default: page.name | replace: ".md", "" }}]({{ site.baseurl }}{{ page.url }})
{% endfor %}
       
{% endif %}
{% endfor %}
   
---
**[关于我](关于)** | **[归档](归档)**