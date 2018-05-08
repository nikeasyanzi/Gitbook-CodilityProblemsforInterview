### MaxSliceSum



https://app.codility.com/demo/results/trainingS5DSXH-HGW/



基本上你要想一件事

1. 就是加了某個element 

導致 current slice sum 變小



則要思考



目前這個element 是否比 current slice sum大



maxEndingHere =A\[i\] &gt; \(maxEndingHere + A\[i\]\)? A\[i\]:\(maxEndingHere + A\[i\]\);

  


比較

current slice sum  是否有機會變成max slice sum

## Kadane 's algorithm









### MaxProfit

[https://app.codility.com/demo/results/trainingQUVSAJ-JHV/](https://app.codility.com/demo/results/trainingQUVSAJ-JHV/)

這題主要是找 陣列內兩元素相減 差為最大

所以基本上要考慮是 找出  目前該元素 減去 該元素之前的其他元素中最小的

```c
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

### MaxDoubleSliceSum



