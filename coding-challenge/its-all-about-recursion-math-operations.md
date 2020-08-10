---
description: 10/08/2020
---

# It's all about recursion - math operations

## Power

```javascript
// power(2,0) // 1
// power(2,2) // 4
// power(2,4) // 16

function power(val, num){
    if(num === 0) return 1;
    
    return val * power(val, num - 1);
}
```

## Factorial

```javascript
//factorial(1) // 1
// factorial(2) // 2
// factorial(4) // 24
// factorial(7) // 5040

function factorial(val){
    if (val === 0) return 1;
    return val * factorial(val - 1);
}

```

## Product Of Array

```javascript
// productOfArray([1,2,3]) // 6
// productOfArray([1,2,3,10]) // 60

function productOfArray(arr){
    if(arr.length === 0) return 1;
    return arr[0] * productOfArray(arr.slice(1))
}
```

## Recursive Range

```javascript
// SAMPLE INPUT/OUTPUT
// recursiveRange(6) // 21
// recursiveRange(10) // 55 

function recursiveRange(val){
    if(val === 1) return 1;
    return val + recursiveRange(val - 1);
}
```

## Fib - the sum of two previous numbers

```javascript
// fib(4) // 3
// fib(10) // 55
// fib(28) // 317811
// fib(35) // 9227465

function fib(num){
    if(num === 1) return 1;
    if(num == 2) return 1;
    
    return fib(num - 1) + fib(num - 2)
}
```

