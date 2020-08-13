---
description: 13/08/2020
---

# Sorting - bubbleSort,

## Bubble Sort

```javascript
function bubbleSort(arr){
    var  noSwaps;
    for(var i = arr.length - 1; i >= 0; i--){
//        console.log("i = " + i);
        noSwaps = true;
        for(var j = 0; j < i; j++){
            console.log("arr: " + arr);
            if(arr[j] > arr[j + 1]){
                swap(arr, j , j + 1);
                noSwaps = false;
//                  var temp = arr[j];
//                  arr[j] = arr[j+1];
//                  arr[j+1] = temp;
                
            } 
        }
        console.log("one pass complete");

        if(noSwaps) break;
    }
    return arr;
}


function swap(arr, index1, index2){
    var temp = arr[index1];
    arr[index1] = arr[index2];
    arr[index2] = temp;
//     return arr;
}


bubbleSort([5,3,4,1,2,14,-1]);
```

## Selection Sort



```javascript
function selectionSort(arr){
    for(var i = 0; i < arr.length; i++){
        var mini = arr[i];
        var miniIndex = i;
        for(var j = i + 1; j < arr.length; j++){

            if(mini > arr[j]){
                mini = arr[j];
                miniIndex = j;
            }
            if(j === (arr.length - 1) && miniIndex !== i){
                swap(arr, i, miniIndex);
            }

        }
    }

    return arr;
}




function swap(arr, index1, index2){
    var temp = arr[index1];
    arr[index1] = arr[index2];
    arr[index2] = temp;
//     return arr;
}


selectionSort([5,3,4,1,2,14,-1]);
```

## Insertion Sort

```javascript
function insertionSort(arr){
    for(var currentIndex = 1; currentIndex < arr.length; currentIndex++){
        
        var currentValue = arr[currentIndex];
        for(var j = (currentIndex - 1); j >= 0; j--){
            

            
            if(currentValue < arr[j]){
                swap(arr, j, j + 1);
            }
        }

        console.log("array", arr);
    }

    return arr;
}


function swap(arr, index1, index2){
    var temp = arr[index1];
    arr[index1] = arr[index2];
    arr[index2] = temp;
//     return arr;
}




insertionSort([2,1,9,76,0])



```



