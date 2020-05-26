# Dijkstra Algorithm
<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-1-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->
Dijkstra Algorithm for finding the shortest path between nodes and a graph.


```csharp
/*
www.amiedd.com
1/11/2019
Dijkstra Algorithm for finding the shortest path between nodes and graph.

More reading on the Algorithm can be found here: https://en.wikipedia.org/wiki/Dijkstra's_algorithm
*/
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Diagnostics;

namespace DijkstraAlgorithm
{
    class Dijkstra
    {
        private static int MinimumDistance(int[] distance, bool[] shortestPath, int verticesCount)
        {
            int min = int.MaxValue;
            int minIndex = 0;
 
            for (int v = 0; v < verticesCount; ++v)
            {
                if (shortestPath[v] == false && distance[v] <= min)
                {
                    min = distance[v];
                    minIndex = v;
                }
            }
            return minIndex;
        }
 
        private static void Print(int[] distance, int verticesCount)
        {
            Console.WriteLine("Vertex    distance from source");
 
            for (int i = 0; i < verticesCount; ++i)
                Console.WriteLine("{0}\t  {1}", i, distance[i]);
        }
 
        public static void DijkstraAlgorithm(int[,] graph, int source, int verticesCount)
        {
            int[] distance = new int[verticesCount];
            bool[] shortestPath = new bool[verticesCount];
 
            for (int i = 0; i < verticesCount; ++i)
            {
                distance[i] = int.MaxValue;
                shortestPath[i] = false;
            }
 
            distance[source] = 0;
 
            for (int count = 0; count < verticesCount - 1; ++count)
            {
                int u = MinimumDistance(distance, shortestPath, verticesCount);
                shortestPath[u] = true;
 
                for (int v = 0; v < verticesCount; ++v)
                    if (!shortestPath[v] && Convert.ToBoolean(graph[u, v]) && distance[u] != int.MaxValue && distance[u] + graph[u, v] < distance[v])
                        distance[v] = distance[u] + graph[u, v];
            }
 
            Print(distance, verticesCount);
        }
 
        static void Main(string[] args)
        {
            int[,] graph =  {
                         { 0, 6, 0, 0, 0, 0, 0, 9, 0 },
                         { 6, 0, 9, 0, 0, 0, 0, 11, 0 },
                         { 0, 9, 0, 5, 0, 6, 0, 0, 2 },
                         { 0, 0, 5, 0, 9, 16, 0, 0, 0 },
                         { 0, 0, 0, 9, 0, 10, 0, 0, 0 },
                         { 0, 0, 6, 0, 10, 0, 2, 0, 0 },
                         { 0, 0, 0, 16, 0, 2, 0, 1, 6 },
                         { 9, 11, 0, 0, 0, 0, 1, 0, 5 },
                         { 0, 0, 2, 0, 0, 0, 6, 5, 0 }
                            };
 
            DijkstraAlgorithm(graph, 0, 9);
        }
    }
}
```

[![Run on Repl.it](https://repl.it/badge/github/AmieDD/Dijkstra-Algorithm)](https://repl.it/github/AmieDD/Dijkstra-Algorithm)

## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="http://www.amiedd.com"><img src="https://avatars3.githubusercontent.com/u/7669428?v=4" width="100px;" alt=""/><br /><sub><b>Amie DD</b></sub></a><br /><a href="https://github.com/AmieDD/Dijkstra-Algorithm/commits?author=AmieDD" title="Code">💻</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!