---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
Добро пожаловать! Школа олимпиадного перограммирования ИКЦ
{% assign pinned = site.posts | where_exp:"item", "item.pin == true" %}

