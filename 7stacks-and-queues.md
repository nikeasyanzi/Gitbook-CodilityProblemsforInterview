### Brackets

檢查空字串可使用strlen 或者直接檢查是否為'\0'

```c
if(strlen(S)==0)
   return 1;

if(S[0]=='\0')
   return 1;
```

幾種illegal cases要考慮

1. The left bracket and right bracket are not compatible
2. We find a right bracket, but the stack is empty
3. Containing a character that is not a bracket {\[\( \)\]}
4. There are some other left brackets left in the stack

Solution:[https://app.codility.com/demo/results/trainingH9X3PD-3CY/](https://app.codility.com/demo/results/trainingH9X3PD-3CY/)



但這題上傳時,我沒多寫一個 function freeAll\(\)作為memory recollect之用,否則在illegal case產生時,程式立即返回,有memory leak的問題

```c
freeAll(){
   struct node *next;
   while(head!=NULL){
      head->next=next;
      free(head);
      head=next;
   }
}
```

### StoneWall

看起來很難  做起來更難的一

觀察一下幾個case

[1,2,1] -> 2
[1,2,3,2,1] -> 3
[1,1,1,1] -> 1

We find the only way to saving the retangle is the case that top(stack)==A[i]

其實是分這三種狀況

1. 遞增 -> push
   1. When the series is increasing, it means we need another retangle. 
2. 遞減 -> pop
   2. When the series is decreasing, it means we need to pop out the stack until the stack top value is less than or equal to the current value A[i]
3. 持平 -> ignore
   3. Whne the stack top value is euqal to the current value A[i], that means we can save a retangle by ignoring it.




### Fish

### Nesting

這題更簡單 只要檢查\(\)是否成對就好 是Bracket那題的簡化版

