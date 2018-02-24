### EquiLeader



### Dominator

#### 思路

就是一個dominator 和另一個non dominator 互相抵銷  
最後  若某數  數量有 大於N/2個   會成為最後保留下來的 ，就會是dominator

所以利用這個方法  先掃過array   得出dominator

#### 這題遇到幾個問題

1.我的做法是 計算某數出現的次數\(count\)


若下一個element 仍為某數(variable A),
則count +1.

if next element is not variable A,
subtract 1 from the variable A   

When counter is zero, the dominator needs to be replaced 
counter要回設為1, because the new dominator has appeared one time 


2.count　\(dominator 最後的次數\)　 一定不為零，因為最後至少會有一個存活

3.最後要檢查 dominator 出現的次數有沒有超過n/2

[https://app.codility.com/demo/results/trainingJ5MW8U-V29/](https://app.codility.com/demo/results/trainingJ5MW8U-V29/)

