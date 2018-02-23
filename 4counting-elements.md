## Lesson 4 Counting Elements 

### Perm Check
https://app.codility.com/demo/results/trainingBJ8AXR-HEC/

### FrogRiverOne

### Missing integer
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

### MaxCounters