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
 
## Методы string
 
Для начала следует сказать, что для строки определены итераторы **begin()** и **end()**. Указывающее соответственно на первый и на последний символы.

* **s.size() / s.lenght()**
 Возвращает длину строки s. В следующем коде мы циклом идем по строке и выводим каждый символ.
{% highlight cpp %}
#include <iostream>
#include <string>

using namespace std;

int main()
{
	string s;
	cin >> s;
	for (int i = 0; i < s.size(); i++)
	{
		cout << s[i];
	}
	return 0;
}
{% endhighlight %}

* **s.append(s1)**
Данная функция добавляет строку s1 в конец строки s.
{% highlight cpp %}
#include <iostream>
#include <string>

using namespace std;

int main()
{
	string s = "a";
	string s1 = "b";
	s.append(s1); // идентично s += s1
	cout << s << endl; 
	cout << s + s1 << endl;
	return 0;
}
{% endhighlight %}

* **s.erase()**
Данная функция имеет несколько перегрузок:

 **s.erase(pos,n)** удаляет n символов начиная с позиции pos
 
 **s.erase(iterator)** iterator - это итератор, указывающий на символ. В результате применения функции этот символ будет удален.
 
 **s.erase(it begin, it end)** it begin, it end - итераторы, указывающие на начало и конец удаляемой последовательности. 
  
{% highlight cpp %}
#include <iostream>
#include <string>

using namespace std;

int main()
{
	string s = "abcdef";
	s.erase(1,2); // adef
	string str = "abcdef";
	str.erase(str.begin()); // bcdef
	string sp = "abcdef";
	sp.erase(sp.begin() + 1, sp.end()); // a
}
{% endhighlight %}

В данном коде показаны преобразования строки, сделанные erase().
