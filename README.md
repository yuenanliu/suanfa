递归算法的时间复杂度=递归的次数*每次递归操作的次数, 并不总是O(logn)

举例：求x的n次方

***写法1***
```
int func(int x, int n){
  if(n==0) return 1;
  if(n==1) return x;
  return func(x, n-1) * x;
}
```
时间复杂度是O（n)

***写法2***
```
int func(int x, int n){
  if(n==0) return 1;
  if(n==1) return x;
  if(n % 2 == 1){
    return func(x, n/2) * func(x, n/2) * x;
  }
}
```
时间复杂度是O(N)
分析：从下图看，相乘操作的次数是1+2+4+8=15次，即非叶子节点的个数
假设树的深度是m，那么节点个数为2^0+2^1+...+2^m = 2^(m+1)-1 = N-1, 而m=log[2]N
所以时间复杂度是o(N)
```
                    16
          8                       8
    4           4           4           4
 2     2     2     2     2     2     2     2 
1 1   1 1   1 1   1 1   1 1   1 1   1 1   1 1 
```

***写法3***
```
int func(int x, int n){
  if(n==0) return 1;
  if(n==1) return x;
  int temp = func(x, n/2);
  if(n % 2 == 1){
    return temp * temp * x;
  }else{
    return temp * temp;
  }
}
```
递归次数log[2]N, 每次递归相乘操作的次数2，时间复杂度是O(logN)

