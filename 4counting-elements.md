## Lesson 4 Counting Elements 

### 4-1.Perm Check

Description: 
A non-empty zero-indexed array A consisting of N integers is given.
A permutation is a sequence containing each element from 1 to N once, and only once.

https://app.codility.com/demo/results/trainingZQCD6P-WUF/

```c
int solution(int A[], int N)
{
int *hasharr=malloc(sizeof(int) *N );
int i;
memset(hasharr,0,sizeof(int)*N);
int isPerm=1;
for(i=0; i<N; i++)
{
    if(A[i]<=N && A[i]>=1) //check if the number excesses the range
    {
        if(hasharr[A[i]-1]==0){ //check if the number is repeteted
            hasharr[A[i]-1]=1;
        }
        else
        {
            isPerm= 0;
            break;
        }
    }
    else{    
        isPerm= 0;    
        break;
    }
}
free(hasharr);

return isPerm;
}
```
這題應該要把想法單純化

1.檢查數值是不是在1-N之間
2.檢查有沒有重複   這樣即可

不用去思考負數或零的問題
不用sum的方法，因為有overflow的風險

### 4-2.FrogRiverOne

### 4-3.Missing integer
##### 1. XOR sum
        
    Suppose you have numbers from 1 to N and you have to find their XOR sum 
    for N = 6, XOR sum will be 1^2^3^4^5^6 = 7.
[What is an XOR sum?](https://stackoverflow.com/questions/17284337/what-is-an-xor-sum)

In this case, xor sum is used to check the number appearing only once in a sequence where each numbers appear twice. XOR a number twice, then you get Zero.
2. using this idea, and we XOR the index with each element,
3. thus, we actually add up a sequence that all number appear twice except one

https://app.codility.com/demo/results/training8DWFUV-BGH/


##### 2.用hash 

1. 給定N個點，則答案必為1~N+1 中的某個數

2. 承1，hash array 只需要 N elements，其中index為 0~ N-1，分別代表1 ~ N的數

ex. 
[1,2,3]  則 最後掃描hassarr 會發現 hasharr[2]=3  所以 return 4;
[2,3,4]  則 最後掃描hassarr 會發現 hasharr[0]=0  所以 return 1;
https://app.codility.com/demo/results/training8R2VH7-P47/

### 4-4.MaxCounters