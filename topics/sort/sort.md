---
layout: topic
title: Сортировки
permalink: topics/sort/
---
Сортировка - алгоритм упорядочивания элементов в списке - достаточно распространенная задача программирования. Существуют многочисленные алгоритмы сортировки - простые и сложные - о них мы поговорим далее.


## Сортировка пузырьком
Сортировка пузырьком (Bubble sort) проста в реализации, однако сложность данного алгоритма ставляет желать лучшего - $$O(n^2)$$. Поэтому, на практике данный алгоритм применяется редко, в качестве обучения.
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
Быстрая сортировка (quick sort), известная также как **сортировка Хоара**, - один из самых быстрых универальных алгоритмов сортировки, вычислительная сложность -  $$O(n\log(n))$$.

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

<iframe width="956" height="538" src="https://www.youtube.com/embed/ywWBy6J5gz8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
