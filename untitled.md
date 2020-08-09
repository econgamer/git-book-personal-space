---
description: 2020/08/08
---

# Average Pair

## Question

```javascript
console.log("result1: " + averagePair([1,2,3],2.5)); //true
console.log("result2: " + averagePair([1,3,3,5,6,7,10,12,19],8)); //true
console.log("result3: " + averagePair([-1,0,3,4,5,6], 4.1));   //false
console.log("result4: " + averagePair([], 4)); //false
```

## My Solution:

```javascript
function averagePair(arr1, avg){
  let j = 0;
  let i = 1;

  while(i > j && i < arr1.length)
  {
    if((arr1[i] + arr1[j])/2 == avg){
        return true;
    }

    if(i == arr1.length - 1)
    {
        j += 1;
        i = j + 1;
        continue;
    }
    i++;
  }

  return false;


}
```

