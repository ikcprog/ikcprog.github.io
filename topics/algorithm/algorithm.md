---
layout: topic
title: Обзор библиотеки algorithm
permalink: topics/algorithm/
---
В данной статье мы познакомимся с некоторыми функциями из библиотеки **algorithm**. Само название данной библиотеки говорит нам о том, что в ней содержатся различные алгоритмы. Зачастую это такие, как поиск минимума/максимума, подсчет, разворот задом наперёд, то есть рутинные функции. Для того, чтобы не писать их каждый раз "руками", и была создана данная библиотека. Далее мы рассмотрим 10 самых важных функций:

Далее мы будем использовать:
* first - итератор начала
* last - итератор конца
* value - значение

## count
**count(first, last, value)**

Возвращает количество элементов, равных value. 
Например, у нас имеется вектор, и мы хотим узнать, сколько в нём нулей:

{% highlight cpp %}
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
	vector<int> vec = { 1,0,1,0,1,1,1 };
	cout << count(vec.begin(), vec.end(), 0);
	return 0;
}
{% endhighlight %}

## find
**find(first, last, value)**

Возвращает итератор на первый элемент, равный value.
Например, у нас имеется массив константоной длины, и мы хотим найти 4:

{% highlight cpp %}
#include <iostream>
#include <algorithm>

using namespace std;

const int SIZE = 10;

int main()
{
	int arr[SIZE] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
	int *find_4 = find(arr, arr + SIZE, 4);
	cout << *find_4;
	return 0;
}
{% endhighlight %}

А что вернет find, если элемента со значением value нет? Будет возвращен указатель на last. В этом легко убедиться, если проанализировать следующий код:
{% highlight cpp %}
int arr[SIZE] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
int* find_100 = find(arr, arr + SIZE, 100);
cout << arr + SIZE << endl;
cout << find_100;
{% endhighlight %}

## fill
**fill(first, last, value)**

Заполняет диапазон значениями value
Здесь всё просто: заполним вектор нулями:

{% highlight cpp %}
vector<int> vec(10);
fill(vec.begin(), vec.end(), 0);
{% endhighlight %}
	
## reverse
**reverse(first, last)**

Разворачивает диапазон задом наперед.
Допустим, у нас есть строка. И мы хотим проверить, является ли строка палиндромом:

{% highlight cpp %}
string s, reversed;
cin >> reversed;
s = reversed;
reverse(reversed.begin(), reversed.end());
if (s == reversed)
	cout << "Palindrome!";
else
	cout << "Not palindrome :(";
{% endhighlight %}

## swap
**swap(a,b)**

Обменивает a и b местами.

## max/min
**max(a,b)** - берет максимум из двух чисел
**min(a,b)** - берет минимум из двух чисел

Если нам нужно найти максимум/минимум из $$n$$ чисел, то мы можем использовать следующее:
{% highlight cpp %}
int a, b, c, d;
cin >> a >> b >> c >> d;
cout << "max: " << max(a, max(b, max(c, d))) << endl;
cout << "min: " << min(a, min(b, min(c, d)));
{% endhighlight %}

## next_permutation/prev_permutation
**next_permutation(first,last)** - позволяет выполнить перестановку в диапазоне
**prev_permutation(first,last)** - позволяет выполнить обратную перестановку в диапазоне

Пусть у нас имеется некоторая последовательность, для котрой мы хотим посмотреть все перестановки:
{% highlight cpp %}
vector<int>vec;

sort(vec.begin(), vec.end());

do {
	for (auto x : vec)
		cout << x << " ";
	cout << endl;
} while (next_permutation(vec.begin(), vec.end()));
{% endhighlight %}

## max_element/min_element
**max_element(first,last)** - возвращает итератор на максимальный элемент в массиве
**min_element(first,last)** - возвращает итератор на минимальный элемент в массиве

{% highlight cpp %}
vector<int>vec = { 1,2,3 };

cout << *max_element(vec.begin(), vec.end()) << endl;
cout << *min_element(vec.begin(), vec.end());
{% endhighlight %}

## remove
**remove(first, last, value)**

Удаляет все элементы со значением value

## rotate
**rotate(first, n_first, last)**

Зеркально отражает последовательность. В данном случае n_first - элемент будет первым в последовательности. Также можно рассматривать как сдвиг. Рассмотрим на примере строк:

{% highlight cpp %}
string s = "abcd";
rotate(s.begin(), s.begin() + 2, s.end());
cout << s; // cdab
{% endhighlight %}
