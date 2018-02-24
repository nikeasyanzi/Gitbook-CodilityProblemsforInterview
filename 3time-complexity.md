## Lesson 3 Time Complexity
https://app.codility.com/programmers/lessons/3-time_complexity/

### [TapeEquilibrium](https://app.codility.com/programmers/lessons/3-time_complexity/tape_equilibrium/)
A non-empty zero-indexed array A consisting of N integers is given. Array A represents numbers on a tape.

Any integer P, such that 0 < P < N, splits this tape into two non-empty parts: A[0], A[1], ..., A[P − 1] and A[P], A[P + 1], ..., A[N − 1].

The difference between the two parts is the value of: |(A[0] + A[1] + ... + A[P − 1]) − (A[P] + A[P + 1] + ... + A[N − 1])|

In other words, it is the absolute difference between the sum of the first part and the sum of the second part.


這題乍看很難  因為不能用常規解法

1.分別sum A[0] ~ A[P-1] 和 A[P] ~ A[N-1]  很明顯沒效率  也重覆計算很多次
2.用額外的2d陣列  計算出各種和  做出dynamic programming的效果
  但其實題目是要求difference   最後還是要依造各種可能去做減法
3.後來看到這個[\[codility\]TapeEquilibrium](http://www.malphi.net/codility/tapeequilibrium.html)  ,發現用A[0] 和SUM(A[1]~A[N-1]) 起始  逐一增加即可

    ex, 
    P=1
    diff=absolute(SUM(A[1]~A[N-1])- A[0] );
    
    P=2
    diff=absolute(SUM(A[2]~A[N-1])- A[0]-A[1]-A[1]);
    
    P=3
    diff=absolute(SUM(A[3]~A[N-1])- A[0]-A[1]-A[1]-A[2]-A[2]);
    以此類推

(待寫code驗證)


###  [FrogJmp](https://app.codility.com/programmers/lessons/3-time_complexity/frog_jmp/)
蠻簡單的這題  直接寫就好
注意一下
可以用迴圈一直減  但這樣很慢  用除法找商& 餘數比較快
https://app.codility.com/demo/results/training7V28GN-DZ3/


### [PermMissingElem](https://app.codility.com/programmers/lessons/3-time_complexity/perm_missing_elem/)
https://app.codility.com/demo/results/trainingUKVQ5N-YQ2/

這題只是要找 array中 消失的某個數
    
    A zero-indexed array A consisting of N different integers is given.
    The array contains integers in the range [1..(N + 1)],
    which means that exactly one element is missing.


所以  missing item 有可能是1 也有可能是N+1

1. 用總和減去各個element的方法 會有overflow的問題 也導致了tyep conversion 的問題
```c=
int solution(int A\[\], int N) {     
    unsigned long long sum= (1+(N+1) ) *(N+1) /2;
    int i=0;   for (i=0;i<N;i++){   
    sum-=A[i];  
    }   
    return sum;   
}

```
2. 用xor sum 是頗聰明的方法  直接用index 與 each element 做xor
3. 用bucket sort也可以


