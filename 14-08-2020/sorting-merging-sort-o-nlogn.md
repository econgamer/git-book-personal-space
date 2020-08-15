---
description: 14/08/2020
---

# Sorting - Merging Sort - O\(nlogn\)

## Merging Sort

```javascript
function mergeSort(arr){

    if(arr.length <= 1) return arr;
    
    //var newArray = [];
    var middle = Math.floor(arr.length / 2);
    var left = arr.slice(0, middle);
    var right = arr.slice(middle, arr.length);

//     console.log("left: " + left);
//     console.log("right: " + right);
    
//     newArray.push(left);
//     newArray.push(right);
    
    //newArray = merge(left, right);
    //console.log("newArray" + newArray);
    console.log("destructure: " + left, right);
    
    return merge(mergeSort(left), mergeSort(right));
    //return mergeSort(left).concat(mergeSort(right));

}




function merge(left, right){
    var newArray = [];
    var i = 0;
    var j = 0;

    while(i < left.length || j < right.length){
        if(right[j] === undefined || left[i] < right[j]){
            newArray.push(left[i]);
            i++;
        }else{
            newArray.push(right[j]);
            j++
        }
    }

    console.log("newArray: " + newArray);

    return newArray;
}


//mergeSort([8,3,5,4,7,6,1,2]);
mergeSort([10,24,76,73,72,1,9]);

// mergeSort([2,14,99,100]);

// merge([1,10,50],[2,14,99,100]);
//merge([],[2,14,99,100]);
```





