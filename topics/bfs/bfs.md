---
layout: topic
title: Поиск в ширину (BFS)
permalink: topics/bfs/
---
**Поиск в ширину** (англ. breadth-first search, BFS) - метод обхода и поиска пути в графе.
Когда мы говорим слово "обход" мы подразумеваем, что мы посещаем вершины графа в определенном порядке. Одним из часто используемых методов обхода графа является обход в ширину (BFS). Суть BFS достаточно проста. Обход начинается с посещения определённой вершины (для обхода всего графа часто выбирается произвольная вершина). Затем алгоритм посещает соседей этой вершины. За ними - соседей соседей, и так далее.

Ниже представлена визуализация алгоритма BFS. Серым помечены вершины в очереди на посещение, чёрным - уже посещённые.

<img style="display: block; margin: auto; width: 400px" src="./Animated_BFS.gif" />

## Реализация
Для реализации алгоритма нам потребуется очередь из вершин для посещения. При посещении очередной вершины в очередь добавляются все её соседи, которые ещё не были посещены и ещё не находятся в очереди. Для проверки, была ли вершина уже посещена, используется массив меток. Изначально $$visited[i] = false$$ для всех $$i$$, кроме начальной вершины. При добавлении вершины $$i$$ в очередь $$visited[i]$$ присваивается $$true$$.

{% highlight cpp %}
//INPUT
	cout << "Enter a number of edges: ";
	int n;
	cin >> n;
	for (int i = 1; i <= n; i++)
	{
		int u, v;
		cin >> u >> v;

		graph[u].push_back(v);
		graph[v].push_back(u);
	}

	//BFS
	queue <int> q;
	q.push(1); // 1 - начальная вершина
	used[1] = true;
	while (!q.empty())
	{
		int current = q.front();
		q.pop();
		cout << current << endl;
		for (auto neighbor : graph[current])
		{
			if (!used[neighbor])
			{
				q.push(neighbor);
				used[neighbor] = true;
			}
		}
	}
 {% endhighlight %}

Теперь усложним задачу - нам нужно определить расстояние от заданной вершины до всех остальных. Для этого создадим массив $$distance$$, и обозначим расстояние от начальной вершины до вершины $$i$$ как $$dst[i]$$.
{% highlight cpp %}
 int distance[100];
	for (int i = 0; i <= 99; i++)
		distance[i] = -1;
	distance[1] = 0;
	//INPUT
	cout << "Enter a number of edges: ";
	int n;
	cin >> n;
	for (int i = 0; i < n; i++)
	{
		int u, v;
		cin >> u >> v;
		graph[u].push_back(v);
		graph[v].push_back(u);
	}

	//BFS
	queue <int> q;
	q.push(1); // 1 - начальная вершина
	used[1] = true;
	while (!q.empty())
	{
		int current = q.front();
		q.pop();
		for (auto neighbor : graph[current])
		{
			if (!used[neighbor])
			{
				q.push(neighbor);
				used[neighbor] = true;
				distance[neighbor] = distance[current] + 1;
			}
		}
	}
	// OUTPUT
	for (int i = 2; i <= n+1; i++)
	{
		if(distance[i] != -1)
			cout << "Distance between vertices 1 and " << i << " is " << distance[i] << endl;
		else
			cout << "Vertex " << i << " cannot be reached from vertex 1." << endl;
	}
{% endhighlight %}
Таким образом мы обошли граф и посчитали расстояния между 1 и всеми остальными вершинами.
