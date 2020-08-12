---
description: 12/08/2020
---

# It's all about recursion - challenges - part2 \(5 challenges\)

## Capitalize the First letter

```text
// capitalizeFirst(['car','taco','banana']); // ['Car','Taco','Banana']
```

```javascript
function capitalizeFirst (arr1) {
  // add whatever parameters you deem necessary - good luck!
  if(arr1.length === 0) return [];

  var newArray = [];
    

  var newChar = arr1[0].charAt(0).toUpperCase() + arr1[0].slice(1);
  arr1[0] = newChar;
  newArray.push(arr1[0]);
  console.log("arr1[0] is equal to: " + arr1[0]);
    
  console.log("newArray: " + newArray);
  return newArray.concat(capitalizeFirst(arr1.slice(1)));
}



capitalizeFirst(['car','taco','banana']);
```

## Sum of Nested Even

```text
var obj1 = {
  outer: 2,
  obj: {
    inner: 2,
    otherObj: {
      superInner: 2,
      notANumber: true,
      alsoNotANumber: "yup"
    }
  }
}

var obj2 = {
  a: 2,
  b: {b: 2, bb: {b: 3, bb: {b: 2}}},
  c: {c: {c: 2}, cc: 'ball', ccc: 5},
  d: 1,
  e: {e: {e: 2}, ee: 'car'}
};

//nestedEvenSum(obj1); // 6
nestedEvenSum(obj2); // 10
```

```javascript
function nestedEvenSum (obj1) {
  // add whatever parameters you deem necessary - good luck!
  var sumOfOdd = 0;

  Object.keys(obj1).forEach(key => {
     //console.log(key, obj1[key]);
     if(typeof(obj1[key]) === 'object')
     {
         sumOfOdd += nestedEvenSum(obj1[key]);
     }

     if(typeof(obj1[key]) === 'number')
     {
         if(obj1[key] % 2 === 0)
         {
            sumOfOdd += obj1[key];
         }
         
     }
     
  });

  return sumOfOdd;

}


var obj1 = {
  outer: 2,
  obj: {
    inner: 2,
    otherObj: {
      superInner: 2,
      notANumber: true,
      alsoNotANumber: "yup"
    }
  }
}

var obj2 = {
  a: 2,
  b: {b: 2, bb: {b: 3, bb: {b: 2}}},
  c: {c: {c: 2}, cc: 'ball', ccc: 5},
  d: 1,
  e: {e: {e: 2}, ee: 'car'}
};

//nestedEvenSum(obj1); // 6
nestedEvenSum(obj2); // 10
```

## Capitalize The Words

```text
// capitalizeWords(words); // ['I', 'AM', 'LEARNING', 'RECURSION']
```

```javascript
function capitalizeWords (arr) {
  // add whatever parameters you deem necessary - good luck!
  if(arr.length === 0) return [];

  var newArray = [];
  newArray[0] = arr[0].toUpperCase();
  

  return newArray.concat(capitalizeWords(arr.slice(1)));
}

let words = ['i', 'am', 'learning', 'recursion'];
// capitalizeWords(words); // ['I', 'AM', 'LEARNING', 'RECURSION']

console.log(capitalizeWords(words));
```

## Stringify the numbers

```text
/*
{
    num: "1",
    test: [],
    data: {
        val: "4",
        info: {
            isRight: true,
            random: "66"
        }
    }
}
*/
```

```javascript
function stringifyNumbers (obj1) {
  // add whatever parameters you deem necessary - good luck!

  var newObject = {};
  
  if(obj1.length === 0 )
  {
      return {};
  };
  //if(obj1 === undefined) return {};

  Object.keys(obj1).forEach(key => {
     //console.log(key, obj1[key]);
     //console.log("typeof(obj1[key]): " + typeof(obj1[key]));
     if(typeof(obj1[key]) === 'object')
     {
         newObject[key] = stringifyNumbers(obj1[key]);
     }else if(typeof(obj1[key]) === 'number')
     {
        console.log("key is: " + key);
        newObject[key] = obj1[key].toString();
        //console.log("typeOf is: " +  typeof(newObject[key]));
         
     }else{
         newObject[key] = obj1[key];
         //console.log("others");
     }
     

  });
  
  if(newObject["random"]){
      var n = newObject["random"].toString();

      //console.log("typeOf is: " +  typeof(newObject["random"]));

     // console.log("newObject is: " +  newObject["random"].toString() + typeof(n));
  }
  

  return newObject;

}

let obj = {
    num: 1,
//     test: [],
    data: {
        val: 4,
        info: {
            isRight: true,
            random: 66
        }
    }
}



stringifyNumbers(obj);
```

## Collect Strings from nested object 

```javascript
// const obj3 = {
//     stuff: "foo",
//     data: {
//         val: {
//             thing: {
//                 info: "bar",
//                 moreInfo: {
//                     evenMoreInfo: {
//                         weMadeIt: "baz"
//                     }
//                 }
//             }
//         }
//     }
// }

collectStrings(obj3) // ["foo", "bar", "baz"])
```

```javascript
function collectStrings (obj1) {
  // add whatever parameters you deem necessary - good luck!
  var newArray = [];

  Object.keys(obj1).forEach(key => {
     

//     console.log("typeOf: " + typeof(obj1[key]));
     if(typeof(obj1[key]) === 'object')
     {
         newArray = newArray.concat(collectStrings(obj1[key]));
     }

     if(typeof(obj1[key]) === 'string')
     {
         console.log("goody goody");
         newArray.push(obj1[key]);
     }
     
  });

  return newArray;

}
```



