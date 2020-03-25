---
layout: topic
title: Файловый ввод - вывод
permalink: topics/file_inoutput/
---

В программировании нередко приходится иметь дело с файлами. В данной статье мы рассмотрим основный принципы и методы файлового ввода - вывода.

Прежде, чем использовать файловый ввод - вывод, подключаем заголовочный файл fstream.
  
## Начинаем работать

Для начала объявим потоки:

{% highlight cpp %}
ifstream fin; // открываем входной поток - fin
ofstream fout; // открываем выходной поток - fout
{% endhighlight %}

ifstream и ofstream - это классы. Значит созданные нами fin и fout - это экземпляры класса, или объекты. Это означает, что для них определены методы. 

Воспользуемся методом открытия файла - open(). В скобках нам необходимо указать имя требуемого файла в кавычках.
{% highlight cpp %}
fin.open("input.txt");
{% endhighlight %}

Также одним из методов является is_open(). Данный метод проверяет, удалось ли открыть файл. Возвращает логическое значение.

{% highlight cpp %}
if (!fin.is_open())
		cout << "Error! File not found.";
 {% endhighlight %}
 
 Иначе, нам удалось открыть файл. Предположим, что в нашем файле лежали некоторые числа, и мы хотим узнать их сумму и вывести её на экран. Стоит отметить, что файл должен лежать в одной папке с вашем проектом (в противном случае, можно указать путь к файлу).
 
 {% highlight cpp %}
 else
	{
		int n,sum = 0;
		while (fin >> n)
		{
			sum += n;
		}
		cout << "Sum: " << sum;
	}
  fin.close();
 {% endhighlight %}

Всегда, после использования потока, закрываем его методом close().

Теперь рассмотрим вывод в файл. На самом деле, он не сильно отличается от ввода. Открываем файл для вывода:

{% highlight cpp %}
fout.open("output.txt");
{% endhighlight %}

И теперь просто выводим при помощи fout:
{% highlight cpp %}
fout << "Sum: " << sum;
{% endhighlight %}

Финальный код:

{% highlight cpp %}
#include <iostream>
#include <fstream>

using namespace std;

int main()
{
	ifstream fin; // открываем входной поток - fin
	ofstream fout; // открываем выходной поток - fout

	fin.open("input.txt");
	fout.open("output.txt");

	if (!fin.is_open())
		cout << "Error! File not found.";
	else
	{
		cout << "Success!";
		int n,sum = 0;
		while (fin >> n)
		{
			sum += n;
		}
		fout << "Sum: " << sum;
	}
	fin.close();
	fout.close();
	return 0;
}
{% endhighlight %}
