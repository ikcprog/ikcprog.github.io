---
layout: page
title:  "Приветствие"
categories: jekyll

---
<div class="post {{ page.class }}">
  {% include item.html %}
  {{ page.content }}
  {% include comments.html %}
</div>


Привет! 
Сайт работает, с чем мы вас и поздравляем.

{% highlight cpp %}

#include <iostream>
using namespace std;
int main()
  {
  cout<<"Hello, world!";
  return 0;
  }

{% endhighlight %}
