---
layout: topic
title: Сортировки
permalink: topics/sort/
---
Сортировка - алгоритм упорядочивания элементов в списке - достаточно распространенная задача программирования. Существуют многочисленные алгоритмы сортировки - простые и сложные - о них мы поговорим далее.

В данной статье мы рассмотрим следующие темы:
* Сортировка пузырьком
* Сортировка вставками
* Сортировка слиянием
* Быстрая сортировка
* Стандартный алгоритм сортировки
* Компараторы
* Стабильная сортировка


## Сортировка пузырьком
Сортировка пузырьком (Bubble sort) проста в реализации, однако сложность данного алгоритма оставляет желать лучшего - $$O(n^2)$$. Поэтому, на практике данный алгоритм применяется редко, лишь в качестве обучения.
{% highlight cpp %}
vector <int> arr;
int temp;
for (int i = 0; i < 10; i++)
{
	cin >> temp;
	arr.push_back(temp);
}
for (int i = 0; i < arr.size() - 1; i++)
{
	for(int j = 0;j<arr.size() - 1; j++)
		if (arr[j] > arr[j + 1])
		{
			temp = arr[j];
			arr[j] = arr[j + 1];
			arr[j + 1] = temp;
		}
}
for (int i = 0; i < arr.size(); i++)
	cout << arr[i] << " ";
{% endhighlight %}

Чтобы понять, как работает данный алгоритм, предлагаю ознакомиться со следующим видеороликом:
<iframe width="738" height="538" src="https://www.youtube.com/embed/lyZQPjUT5B4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



## Сортировка вставками
Сортировка вставками (Insertion sort), вычислительная сложность - $$O(n^2)$$.
{% highlight cpp %}
for (int i = 0; i < arr.size() - 1; i++) {
     for (int j = i + 1; j < arr.size(); j++) {
		if (arr[i] > arr[j]) {
			temp = arr[j];
			arr[j] = arr[i];
			arr[i] = temp;
		}
	}
}
{% endhighlight %}
<iframe width="738" height="538" src="https://www.youtube.com/embed/ROalU379l3U" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



## Сортировка слиянием
Сортировка слиянием (Merge sort). Вычислительная сложность - $$O(n\log(n))$$. Реализуем рекурсивный способ данной сортировки.
С этой целью, спроектируем две процедуры - sort и merge.
Процедура merge будет отвечать за объединение массивов в единный массив
{% highlight cpp %}
int middle, start, final, j;
int mas[100];
middle = (first + last) / 2; //вычисление среднего элемента
start = first; //начало левой части
final = middle + 1; //начало правой части
for (j = first; j <= last; j++) //выполнять от начала до конца
	if ((start <= middle) && ((final > last) || (A[start] < A[final])))
	{
		mas[j] = A[start];
		start++;
	}
	else
	{
		mas[j] = A[final];
		final++;
	}
//возвращение результата в список
for (j = first; j <= last; j++) 
	A[j] = mas[j];
};
{% endhighlight %}

Процедура sort отвечает непосредственно рекурсивную сортировку.
{% highlight cpp %}
void sort(int A[], int first, int last)
{
        int mid = (first + last) / 2;
	{
	        if (first < last)
		{
		sort(A, first, (first + last) / 2); //сортировка левой части
		sort(A, (first + last) / 2 + 1, last); //сортировка правой части
		merge(A, first, last); //слияние двух частей
		}
	}
};
{% endhighlight %}

Осталось лишь в главной функции вызвать процедуру sort:
{% highlight cpp %}
sort(A, 1, n);
{% endhighlight %}

Важное замечание: в функции main() мы нумеровали массив А начиная с 1.

<iframe width="738" height="538" src="https://www.youtube.com/embed/XaqR3G_NVoo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



## Быстрая сортировка
Быстрая сортировка (quick sort), известная также как **сортировка Хоара**, - один из самых быстрых универальных алгоритмов сортировки, вычислительная сложность -  $$O(n\log(n))$$. Стоит заметить, что это средняя сложность. В худшем случае сложность будет  $$On^2$$

{% highlight cpp %}
void quicksort(int* arr, int first, int last)
{
 int mid, count;
 int f = first; int l = last;
 mid = arr[(f + l) / 2];//опорный элемент
 do
 {
	while (arr[f] < mid) f++;
	while (arr[l] > mid) l--;
	if (f <= l)
	    {
		count = arr[f];
		arr[f] = arr[l];
		arr[l] = count;
		f++;
		l--;
	    }
} while (f < l);
if (first < l)
{
	quicksort(arr, first, l);
}
if (f < last) 
{ 
        quicksort(arr, f, last); 
}
}
{% endhighlight %}

<iframe width="738" height="538" src="https://www.youtube.com/embed/ywWBy6J5gz8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## Стандартный алгоритм сортировки

Чтобы каждый раз не реализовывать в своем проекте алгоритм сортировки, разработчики добавили в язык встроенный алгоритм сортировки. Для того, чтобы его использовать, нужно подключить библиотеку **algorithm**.
Итак, в общем виде стандартный алгоритм сортировки выглядит так:
{% highlight cpp %}
sort(arr, arr + n);
{% endhighlight %}
Где arr(имя массива) является первым аргументом (началом диапазона сортировки), a n - количество элементов в массиве (то есть arr + n - это конец диапазона сортировки). Также при необходимости мы можем использовать третий аргумент - **компаратор** - о нем мы поговорим далее.
Если мы захотим отсортировать vector, мы будем использовать такие аргументы:
{% highlight cpp %}
sort(arr.begin(), arr.end());
{% endhighlight %}

## Компараторы
Иногда в задаче требуется отсортировать не числа, а некоторые сложные объекты, состоящие из нескольких элементов. Для сортировки таких объектов чаще всего нужно вручную указывать параметр, который будет сравниваться при сортировке. Для этого и предназначены компараторы.

Компаратор в C++ - логическая функция, которая принимает два объекта одинакового типа, и возвращает true, если первый из них “меньше” второго и false в противном случае. В этом контексте “меньше” значит, что в отсортированном массиве этот элемент обязательно должен стоять раньше.

Рассмотрим постой пример: нам нужно купить автомобиль. Введем в рассмотрение такую величину как оценку комфорта по десятибалльной шкале. Первое, на что мы должны ориентироваться, это комфорт, а далее уже цена.

Для этого нам понадобится разработать структуру car:
{% highlight cpp %}
struct car
{
        string name;
	int comfort;
	int price;
};
{% endhighlight %}

Далее напишем сам комраратор:
{% highlight cpp %}
bool comp(car a, car b)
{
	return a.comfort > b.comfort 
		|| ((a.comfort == b.comfort) && a.price <  b.price);
}
{% endhighlight %}

Теперь мы можем использовать компаратор как третий аргумент функции sort. Полный код решения:
{% highlight cpp %}
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

struct car
{
	string name;
	int comfort;
	int price;
};

bool comp(car a, car b)
{
	return a.comfort > b.comfort 
		|| ((a.comfort == b.comfort) && a.price <  b.price);
}

int main()
{
	vector <car> cars{
		{"Mersedes", 6,1000},
		{"Toyota", 5,1500},
		{"Hyundai", 4,1500},
		{"Ford", 6,2000},
		{"Volvo", 5,1000},
	};

	sort(cars.begin(), cars.end(), comp);
	for (car a : cars) {
		cout << a.name << endl;
	}

	return 0;
}
{% endhighlight %}

## Стабильная сортировка
Рассмотрим следующий массив структур:
{% highlight cpp %}
vector <car> cars{
		{"Mersedes", 6,1000},
		{"Toyota", 7,1500},
		{"Hyundai", 6,1000},
};
{% endhighlight %}
Как должен быть отсортирован данный массив? Возможны два варианта:

{% highlight cpp %}
Toyota
Mersedes
Hyundai
{% endhighlight %}
или
{% highlight cpp %}
Toyota
Hyundai
Mersedes
{% endhighlight %}
При стандартной сортировке возможны оба этих случая, тогда как при стабильной сортировке возможен только первый, так как относительное положение "Mersedes" и "Hyundai" сохраняется.
Стандартная библиотека C++ включает в себя оптимальную реализацию алгоритма стабильной сортировки со сложностью $$O(n\log n)$$. Как и в std::sort, определены две перегрузки:
{% highlight cpp %}
void stable_sort(iterator begin, iterator end);
void stable_sort(iterator begin, iterator end, comparator comp);
{% endhighlight %}
Разумеется, за стабильность приходится платить другими характеристиками. Стабильная сортировка работает медленнее, чем нестабильная, хотя их сложность одинаковая: $$O(n\log n)$$.
