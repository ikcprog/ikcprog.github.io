---
layout: topic
title: Циклы и отладка
permalink: topics/cycle/
---
Многие вещи в нашей жизни цикличны. Например, вы каждый день ходите в школу, университет, на работу... В языках программирования также существует конструкция, позволяющая описывать циклические явления.

Из уроков информатики вы наверняка знаете, что существует три вида циклов:
* Цикл ПОКА с предусловием (while) - выполняет действия пока условие верно. Условие проверяется **перед** выполнением цикла.
* Цикл ПОКА с постусловиеи (do .. while) - выполняет действия пока условие верно. Условие проверяется **после** выполнения цикла. Значит, что тело цикла гарантировано выполняется 1 раз.
* Цикл ДЛЯ (for) - выполняет операции **заданное** число раз.

Единичное выполнение тела цикла называется итерацией.

Аналогично условиям, для записи одной операции внутри цикла можно не выделять фигурными скобками. В противном случае данное действие является обязательным.

Цикл for распологает тремя параметрами: начальным значением, условием звершения, и увеличением счетчика.

{% highlight cpp %}
for(int i = 0; i < 10; i++)
  cout << i << " ";
{% endhighlight %}

Данный код пробегается по i от 0 до 10 и выводит каждое i.

{% highlight cpp %}
#include <iostream>
#include <Windows.h>

using namespace std;

int main()
{
	int i = 0;
	while (true)
	{
		cout << i;
		Sleep(100);
		i++;
	}
	return 0;
}
{% endhighlight %}

## Отладка
Во время написания кода часто встречаются непредвиденные ошибки. Посмотрим на следующий код:
{% highlight cpp %}
for (int i = 5; i >= 0; i--)
	{
    		int d = 5 / i;
		cout << d << endl;
	}
{% endhighlight %}

Здесь происходит деление на ноль. А сама программа написана вроде бы правильно. Как же отлавливать подобные ошибки - баги?
Для этого люди придумали отладку (Debug). Для того, чтобы начать отладку нужно поставить **точку останова** (breakpoint). Чтобы поставить точку останова, нужно щелкнуть в левую серую панель рядом со строкой, где она требуется. Отладчик приостановит выполнение в заданной точке останова.

![1](2019-11-28 (1).png)

Далее можем пошагово отслеживать значение переменных, задействованных в коде.

![1](2019-11-28 (3).png)
