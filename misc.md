Trend Micro
===

# 2
Alexander and Thomas share a common passion for movies, but unfortunately they do not really like each other. A movie festival is taking place in another town, and both of them want to participate in it. The problem is that neither of them is willing to meet the other during the event.
After some not very pleasant negotiations, they agree that the fairest way to fulfill both goals is to pick two intervals of time so as to maximise the total number of movies that they can both see on their own. Keeping in mind that Alexander and Thomas each want to spend several days in a row at the festival (as the town in which the event is taking place is not close by, so they do not want to travel there more than once), help them count the maximal number of movies that can be seen by both of them independently.
Write a function:
int solution(int movies[], int N, int K, int L);
that, given an array movies consisting of N integers that specifies the number of movies on each day of the festival, and integers K and L that specify the number of days that Alexander and Thomas, respectively, want to spend at the festival, returns the maximal number of movies that can be seen by both of them, or −1 if a solution is not possible.
For example, given movies = [6, 1, 4, 6, 3, 2, 7, 4], K = 3, L = 2, your function should return 24, because Alexander can participate in the festival from the third day and see 4 + 6 + 3 = 13 movies, and Thomas can participate from the seventh day and see 7 + 4 = 11 movies. Thus, they will see a combined total of 13 + 11 = 24 movies, and that is the maximal number that can be achieved.
Given movies = [10, 19, 15], K = 2, L = 2, your function should return −1, because it is not possible for Alexander and Thomas to participate in the event in such a way as to avoid meeting each other.
Assume that:

	* N is an integer within the range [2..600];
	* K and L are integers within the range [1..N − 1];
	* each element of array movies is an integer within the range [1..500].

In your solution, focus on correctness. The performance of your solution will not be the focus of the assessment.




# 3
A network consisting of M cities and M − 1 roads connecting them is given. Cities are labeled with distinct integers within the range [0..(M − 1)].
Roads connect cities in such a way that each pair of distinct cities is connected either by a direct road or along a path consisting of direct roads. There is exactly one way to reach any city from any other city. In other words, cities and direct roads form a tree. The number of direct roads that must be traversed is called the distance between these two cities.
For example, consider the following network consisting of ten cities and nine roads:
![](https://i.imgur.com/aRf8VA5.png)


Cities 2 and 4 are connected directly, so the distance between them is 1. Cities 4 and 7 are connected by a path consisting of the direct roads 4−0, 0−9 and 9−7; hence the distance between them is 3.
One of the cities is the capital, and the goal is to count the number of cities positioned away from it at each of the distances 1, 2, 3, ..., M − 1.
If city number 1 is the capital, then the cities positioned at the various distances from the capital would be as follows:

	* 9 is at a distance of 1;
	* 0, 3, 7 are at a distance of 2;
	* 8, 4 are at a distance of 3;
	* 2, 5, 6 are at a distance of 4.

Assume that the following declarations are given:
struct Results { int * A; int N;};
Write a function:
struct Results solution(int T[], int M);
that, given a non-empty zero-indexed array T consisting of M integers describing a network of M cities and M − 1 roads, returns an array consisting of M − 1 integers, specifying the number of cities positioned at each distance 1, 2, ..., M − 1.
Array T describes a network of cities as follows:

	* if T[P] = Q and P = Q, then P is the capital;
	* if T[P] = Q and P ≠ Q, then there is a direct road between cities P and Q.

For example, given the following array T consisting of ten elements:
T[0] = 9 T[1] = 1 T[2] = 4 T[3] = 9 T[4] = 0 T[5] = 4 T[6] = 8 T[7] = 9 T[8] = 0 T[9] = 1
the function should return [1, 3, 2, 3, 0, 0, 0, 0, 0], as explained above.
Assume that:

	* M is an integer within the range [1..100,000];
	* each element of array T is an integer within the range [0..M−1];
	* there is exactly one (possibly indirect) connection between any two distinct cities.

Complexity:

	* expected worst-case time complexity is O(M);
	* expected worst-case space complexity is O(M), beyond input storage (not counting the storage required for input arguments).


https://stackoverflow.com/questions/21812340/codility-country-network-how-to-solve-it

https://www.quora.com/Algorithms/How-do-I-determine-the-order-of-visiting-all-leaves-of-a-rooted-tree-so-that-in-each-step-I-visit-a-leaf-whose-path-from-root-contains-the-most-unvisited-nodes#

https://github.com/ivanpgs/traveling-graph-greedy-algorithm/tree/master/src

https://codereview.stackexchange.com/questions/183514/find-the-path-connecting-two-points-in-array


http://alrightchiu.github.io/SecondRound/graph-breadth-first-searchbfsguang-du-you-xian-sou-xun.html#code

目標  O(n)


這題用BFS or DFS皆可

1.DFS的話
``` c=
void DFS(struct node *root, int level){
    if(root!=NULL){
        printf(level=%d\n,level);
    }
    DFS(root->right, level+1);
    DFS(root->left,level+1);
}
```

這樣基本上會輸出 


2.BFS 的話
    1.queue
    2.adjacent matrix
    3.visited array 
    4.predecessor
    
```c
    while (!isEmpty(*headptr))
    {
        int u = dequeue(headptr);                  // u 為新的搜尋起點
        for ( iter=0;  iter< citynum; iter++)
        {
            idx=u*citynum+iter;
            printf("idx=%d iter=%d\n",idx,iter);
            if ( adjacentMap[idx]==1  && color[iter] == 0)           
            {
                color[iter] = 1;  // 塗成灰色, 表示已經被「找到」
                distance[iter] = distance[u] + 1; // 距離是predecessor之距離加一
                predecessor[iter] = u;  // renew predecessor
                enqueue(headptr,iter);  // 
            }
        }
    }
```

###### tags: `interview` `Codility`