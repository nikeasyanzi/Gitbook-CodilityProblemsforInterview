

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
3. Containing a character that is not a bracket {[( )]}
4. There are some other left brackets left in the stack

Solution:https://app.codility.com/demo/results/trainingH9X3PD-3CY/


### StoneWall

### Fish

### Nesting



