---
description: 15/08/2020
---

# Sorting - Quick Sort - it's hard

## Quick Sort

![source: https://www.techiedelight.com/quicksort/](../.gitbook/assets/quicksort.png)

```javascript
function quickSort(arr, left = 0, right = arr.length - 1){
    
    var pivotIndex = pivot(arr, left, right);
    var distance = pivotIndex - left;
    var hasRight = right - pivotIndex;
    
    console.log("hasRight: " + hasRight);
    console.log("distance: " + hasRight);
    
//     if(distance > 0){
//         quickSort(arr, 0, pivotIndex);
//     }


//     if(hasRight > 0){
//         quickSort(arr, pivotIndex + 1, arr.length - 1);
//     }
    
    //better
    if(distance > 0){
        quickSort(arr, left, pivotIndex - 1);
    }


    if(hasRight > 0){
        quickSort(arr, pivotIndex + 1, arr.length - 1);
    }




//     if(distance > 0){
//         console.log("right side: " + pivotIndex);
//         return quickSort(arr, pivotIndex, arr.length - 1);    
//     }
    

// //     if(base == 0){
// //         pivotIndex = pivot(arr, base);
// //     }


// //    var base = pivotIndex + 1;
    

//     var distance = right - left;

//     console.log("left - right: ", distance);
    
// //     if(pivotIndex != 0){
// //         quickSort(arr, left, right);
// //     }

// //     if(pivotIndex != 0){
// // //         pivotIndex = pivot(arr, left, right);
// //         return quickSort(arr, 0, pivotIndex);
// //     }

//     if(distance > 0){
//         return quickSort(arr, 0, pivotIndex);
//     }




// //     if(base < arr.length){
// //         pivotIndex = pivot(arr, base);

// //         quickSort(arr, base);
// //     }
   
    console.log("basePoint: " + left);

    return arr;
}



function pivot(arr, start = 0, end = arr.length - 1){
    var pivotPoint = start;

//    console.log("arr start is equal to: " + arr);

//     console.log("end: " + end);
//     console.log("start: " + start);
    
    for(var i = start + 1; i <= end; i++){
        if(arr[start] > arr[i]){
            pivotPoint++;
            var temp = arr[pivotPoint];
            arr[pivotPoint] = arr[i];
            arr[i] = temp;
        }

        if(i === end){
            var temp = arr[pivotPoint];
            arr[pivotPoint] = arr[start];
            arr[start] = temp;
        }
    }
//    console.log("arr is equal to: " + arr);
    return pivotPoint;
}


// let arr = [5,2,1,8,4,7,6,3, 9 , 11, 33, 55, 23];
// let arr = [5,2,1,8,4,7,6,3, 9 , 11, 33, 55, 23];

// let arr = [5,2,1,8,4,7,6,3, 9];
 let arr = [5,2,1,8,4,7,6,3, 9 , 5,2,1,8,4,7,6,3, 9];
//let arr = [6,10,11,50,43,40,30,42,20,40,19,32,20,41,23,27];
quickSort(arr, 0);     //4


```



