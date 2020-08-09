---
description: 2020/08/08
---

# Max Sub Array Sum - 08/08/2020

## Question:

```javascript
console.log("result 1 : " + maxSubarraySum([100,200,300,400], 2));  //700
console.log("result 2 : " + maxSubarraySum([1,4,2,10,23,3,1,0,20], 4)); //39
console.log("result 3 : " + maxSubarraySum([-3,4,0,-2,6,-1], 2));   //5
console.log("result 4 : " + maxSubarraySum([3,-2,7,-4,1,-1,4,-2,1],2)); //5
console.log("result 5 : " + maxSubarraySum([2,3], 3));  //null
```

## My Solution:

```javascript
function maxSubarraySum(arr1, num){
    let tempSum = 0;
    let currentSum;
    let maximumSum = 0;

    if(num > arr1.length){
        return null;
    }

    for(var i = 0; i < num; i++){
        tempSum += arr1[i]
    }
    //console.log("tempSum" + tempSum);
    maximumSum = tempSum;
    for(var i = num; i < arr1.length; i++){
//        console.log("tempSum : " + tempSum);
        currentSum = tempSum - arr1[i-num] + arr1[i];
//         console.log("currentSum : " + i);
//         console.log("arr1[i-num] : " + arr1[i-num]);
//         console.log("arr1[num] : " + arr1[num]);
        maximumSum = Math.max(currentSum, maximumSum);
        tempSum = currentSum;
    }

    return maximumSum;

}
```

