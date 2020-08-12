---
description: 12/8/2020
---

# It's all about recursion - challenges - part1 \(4 challenges\)

## Reverse the strings

```javascript
// reverse('awesome') // 'emosewa'
// reverse('rithmschool') // 'loohcsmhtir'
```

```javascript
function reverse(str1){
  if(str1.length === 0) return "";
  var strLength = str1.length;
  return str1[str1.length - 1] + reverse(str1.slice(0,strLength - 1));
}

reverse('awesome');
reverse('rithmschool');

```

## Is the string Palindrome?

```javascript
// isPalindrome('awesome') // false
// isPalindrome('foobar') // false
// isPalindrome('tacocat') // true
// isPalindrome('amanaplanacanalpanama') // true
// isPalindrome('amanaplanacanalpandemonium') // false
```

```javascript
function isPalindrome(str1){
  // add whatever parameters you deem necessary - good luck!
  if(str1[str1.length - 1] !== str1[0]) return false;
  if(str1.length === 1) return true;

  var strLength = str1.length;

  return isPalindrome(str1.slice(1, strLength - 1));

}

console.log("result1: " + isPalindrome('awesome')); // false
console.log("result1: " + isPalindrome('foobar')); // false
console.log("result1: " + isPalindrome('tacocat')); // true
console.log("result1: " + isPalindrome('amanaplanacanalpanama')); // true
console.log("result1: " + isPalindrome('amanaplanacanalpandemonium')); // false
```

## Recursive - Callback function 

```javascript
// SAMPLE INPUT / OUTPUT
// const isOdd = val => val % 2 !== 0;

// someRecursive([1,2,3,4], isOdd) // true
// someRecursive([4,6,8,9], isOdd) // true
// someRecursive([4,6,8], isOdd) // false
// someRecursive([4,6,8], val => val > 10); // false

//const isOdd = val => val % 2 !== 0;

```

```javascript
function someRecursive(arr1, fun1){

  if(arr1.length === 0) return false;
  if(fun1(arr1[0])) return true;

  return someRecursive(arr1.slice(1), fun1);
//   if(!fun1(arr1)) return false

//   return someRecursive(arr1.slice(1), fun1);
  // add whatever parameters you deem necessary - good luck!
}

console.log("result 1: " + someRecursive([1,2,3,4], isOdd));
console.log("result 2: " + someRecursive([4,6,8,9], isOdd));
console.log("result 3: " + someRecursive([4,6,8], isOdd));
console.log("result 4: " + someRecursive([4,6,8], val => val < 10));
```

## Flatten the lists

```javascript
// flatten([1, [2, [3, 4], [[5]]]]) // [1, 2, 3, 4, 5]
// flatten([[1],[2],[3]]) // [1,2,3]
// flatten([[[[1], [[[2]]], [[[[[[[3]]]]]]]]]]) // [1,2,3]
```

```javascript
function flatten(arr1){
  // add whatever parameters you deem necessary - good luck!
  console.log("testing run");
  if(arr1.length === 0) return [];
  console.log("testing run2: " + arr1);
  
  var newArray1 = [];

  for(var i = 0; i < arr1.length; i++){
      if(arr1[i].length === undefined){
        newArray1 = newArray1.concat(arr1[i]);
        console.log("testing run3: " + arr1[i]);
        console.log("testing run4: " + newArray1);
      }else{
        newArray1 = newArray1.concat(flatten(arr1[i]));
      }

  }

  console.log("newArray1: " + newArray1);

  return newArray1;
  //return arr1[0].concat(flatten(arr1.slice(1)));
}

console.log("testing", [].concat(2));


 flatten([1, 2, 3, [4, 5] ]) // [1, 2, 3, 4, 5]
```





