---
layout: topic
title: Строка
permalink: topics/string/
---
**Строка** в C++ представляет собой особый класс. Класс, в терминах программирования, это элемент, описывающий абстрактный тип данных. Это означает, что для строки определены особые функции - методы. В дальнейшем такие понятия как функции, методы и классы будут рассмотренны подробнее.

Чтобы пользоваться строками, необходимо подключить заголовочный файл <string>:
{% highlight cpp %}
  #include <string>
{% endhighlight %}

Объявление строк схоже с объявлением переменной.
{% highlight cpp %}
  #include <string>
  
  using namespace std;
  
  int main()
  {
   string s;
   s = "Hello!";
   cout << s << endl;
   return 0;
  }
{% endhighlight %}

Строка также представляет собой массив символов. Значит, чтобы получить конкретный символ, можно использовать следующее:
{% highlight cpp %}
  #include <string>
  
  using namespace std;
  
  int main()
  {
   string s;
   s = "Hello!";
   cout << s[2] << endl;
   return 0;
  }
{% endhighlight %}
 
 Этот код выведет третий символ строки s.
 
 ## Методы
 
 **s.size() / s.lenght()**
 Возвращает длину строки s.
