---
description: 2020/08/08
---

# Min Sub Array Length - 08/08/2020

## Question:

```javascript
console.log("Result1: " + minSubArrayLen([2,3,1,2,4,3], 7));
console.log("Result2: " + minSubArrayLen([2,1,6,5,4], 9));
console.log("Result3: " + minSubArrayLen([3,1,7,11,2,9,8,21,62,33,19], 52));
console.log("Result4: " + minSubArrayLen([1,4,16,22,5,7,8,9,10], 39));
console.log("Result5: " + minSubArrayLen([1,4,16,22,5,7,8,9,10],55));
console.log("Result6: " + minSubArrayLen([4,3,3,8,1,2,3],11));
console.log("Result7: " + minSubArrayLen([1,4,16,22,5,7,8,9,10],95));
```

## My Solution:

```javascript
function minSubArrayLen(arr1, num){

   let initSum = 0;
   let initIndex = 0;
   let minIndex = 0;
   let startingIndex = 0;
   let resultLength = 0;

   for(var i = 0; i < arr1.length; i++)
   {
       if(initSum < num)
       {
           initSum += arr1[i];
           initIndex = i + 1;
       }else{
           break;
       }

   }

   minIndex = initIndex;

    for(var i = initIndex; i <= arr1.length; i++)
    {

        //console.log(initSum);

        while(initSum >= num){
            initSum -= arr1[startingIndex];
            startingIndex++;
            minIndex--;

            //console.log("minIndex --: " + minIndex);
            if(initSum >= num)
            {
                resultLength = minIndex;
            }
        }

        if(initSum < num){
            initSum += arr1[i];
            minIndex++;

            //console.log("minIndex ++: " + minIndex);

        }

    }


   //console.log("initindex:" + minIndex);
    return resultLength;
}
```

