# Introduction

Here are some notes regarding [Codility](https://app.codility.com/programmers/lessons/1-iterations/) questions.

## Lesson 1 Iterations

BinaryGap

## Lesson 2 Arrays

OddOccurrencesInArray  
PAINLESS

## Lesson 3 Time Complexity

### FrogJmp

### PermMissingElem

## Lesson 4 Counting Elements

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

```c=
int solution(int A, int B, int K) {
   int countB = B/K;    //numbers can be divided by K  
    int countA = (A > 0 ? (A - 1)/K: 0); //why A-1, because A might be the factor of K we need to -1.
    if(A == 0){
        countB++;   //an bundary condition, 0 can be divided by an number
    }
    return countB - countA;
}
```

## Lesson 6 Sorting

### Triangle

[Triangle](https://app.codility.com/demo/results/trainingHA6RY3-X7F/#)  
[https://app.codility.com/demo/results/trainingHA6RY3-X7F/](https://app.codility.com/demo/results/trainingHA6RY3-X7F/)

這題遇到幾個問題

1.前處理要先檢查 至少元素都要是正的   而且至少三個  
2.自己寫了insertion sort 不會過  因為 time complexity n^2 太糟  最後只好呼叫stdlib內建的quick sort  
3.triangular check那邊有陷阱

參考資料  
[【题解】【数组】【Leader】【Codility】Dominator&Equi-leader](http://www.cnblogs.com/wei-li/p/Dominator.html)

## Lesson 8 Leaders

### Dominator

#### 思路

就是一個dominator 和另一個non dominator 互相抵銷  
最後  若某數  數量有 大於N/2個   會成為最後保留下來的 ，就會是dominator

所以利用這個方法  先掃過array   得出dominator

#### 這題遇到幾個問題

1.我的做法是 計算某數出現的次數\(count\)

```
若下一個element 仍為某數(variable A),
    則count +1.

if next element is not variable A,
    substract 1 from the variable A   

When counter is zero, the dominator needs to be replaced
    counter要回設為1, because the new dominator has appear one time.
```

2.count　\(dominator 最後的次數\)　 一定不為零，因為最後至少會有一個存活

3.最後要檢查 dominator 出現的次數有沒有超過n/2

[https://app.codility.com/demo/results/trainingJ5MW8U-V29/](https://app.codility.com/demo/results/trainingJ5MW8U-V29/)

## Lesson 9 Maximum slice problem

### MaxProfit

[https://app.codility.com/demo/results/trainingQUVSAJ-JHV/](https://app.codility.com/demo/results/trainingQUVSAJ-JHV/)

這題主要是找 陣列內兩元素相減 差為最大

所以基本上要考慮是 找出  目前該元素 減去 該元素之前的其他元素中最小的

```c=
#define MAX(a,b) ((a)>(b))?(a):(b)
#define MIN(a,b) ((a)<(b))?(a):(b)
int solution(int A[], int N) {

int i;

int min=A[0];
int profit=0;
for (i=1;i<N;i++){
    min=MIN(min,A[i]);  //record who is the smallest element prior to A[i]
    profit=MAX(profit, A[i]-min);  //renew profit
    //printf("i=%d, min=%d profit=%d\n",i,min,profit);

}
    //printf("profit=%d\n",profit);
    return profit;
}
```

## Lesson 16 Greedy algorithms

### Tie rope

[https://app.codility.com/demo/results/trainingDYMRUK-HM4/](https://app.codility.com/demo/results/trainingDYMRUK-HM4/)

基本上就是 加到 超過threshold K 表示找到一條

## Codility 面試 3 題

[http://www.hjwu.me/2017-10-31-codility-tasks/](http://www.hjwu.me/2017-10-31-codility-tasks/)

###### tags: `interview` `Codility`



