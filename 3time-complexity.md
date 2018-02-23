## Lesson 3 Time Complexity
###  [FrogJmp](https://app.codility.com/programmers/lessons/3-time_complexity/frog_jmp/)
蠻簡單的這題  直接寫就好
注意一下
可以用迴圈一直減  但這樣很慢  用除法找商& 餘數比較快
https://app.codility.com/demo/results/training7V28GN-DZ3/


### PermMissingElem
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


