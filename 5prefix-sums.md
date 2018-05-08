## Lesson 5 Prefix Sums

### CountDiv

[https://app.codility.com/demo/results/trainingSU2YMH-P3Z/](https://app.codility.com/demo/results/trainingSU2YMH-P3Z/)

the background knowledge is

A/K=C that means there are C numbers can be divided by K.

ex.  6/2=3  so, 1,2,6 are the 3 numbers can be divided by 2.

similarly, if we want to count the numbers can be divided by K between range A and B  
it can be expressed as B/K - A/K  
test cases:  
A = 6, B = 11, K = 2  
A = 10, B = 10, K in {5,7,20}

```c
int solution(int A, int B, int K) {
   int countB = B/K;    //numbers can be divided by K  
    int countA = (A > 0 ? (A - 1)/K: 0); //why A-1, because A might be the factor of K we need to -1.
    if(A == 0){
        countB++;   //an bundary condition, 0 can be divided by an number
    }
    return countB - countA;
}
```

### PassingCars



https://app.codility.com/demo/results/trainingWUYKQ7-7SU/





### MinAvgTwoSlice

### GenomicRangeQuery



