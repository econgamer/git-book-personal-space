---
description: 22/08/2020
---

# Max Binary Heap





![src:https://www.geeksforgeeks.org/heap-data-structure/](https://media.geeksforgeeks.org/wp-content/cdn-uploads/MinHeapAndMaxHeap.png)

```javascript
class MaxBinaryHeap{
    constructor(){
        this.values = [];
    }

    insert(val){
        this.values.push(val);
        var index = this.values.length - 1;
        
        var parentIndex = Math.floor((index - 1) / 2);

        while(this.values[index] > this.values[parentIndex]){
  
            var temp = this.values[parentIndex];
            this.values[parentIndex] = this.values[index];
            this.values[index] = temp;
            index = parentIndex;
            parentIndex = Math.floor((index - 1) / 2);

        }

        return this.values;
    }


    remove(){
        var oldRoot = this.values[0];
        this.values[0] = this.values[this.values.length - 1];
        this.values.pop();
        
        var index = 0;
        var childrenLeftIndex = Math.floor(2 * index + 1);
        var childrenRightIndex = Math.floor(2 * index + 2);

        
        while(this.values[index] < this.values[childrenLeftIndex] || 
                this.values[index] < this.values[childrenRightIndex])
        {
            console.log("index: " + this.values[index]);
            console.log("left: " + this.values[childrenLeftIndex]);
            console.log("right: " + this.values[childrenRightIndex]);

            if(this.values[childrenLeftIndex] > this.values[childrenRightIndex] 
            || this.values[childrenRightIndex] === undefined){
                var temp = this.values[index];
                this.values[index] = this.values[childrenLeftIndex];
                this.values[childrenLeftIndex] = temp;
                index = childrenLeftIndex;
            }else{
                var temp = this.values[index];
                this.values[index] = this.values[childrenRightIndex];
                this.values[childrenRightIndex] = temp;
                index = childrenRightIndex;
            }

            childrenLeftIndex = Math.floor(2 * index + 1);
            childrenRightIndex = Math.floor(2 * index + 2);
             
        }
        console.log("updated value is " + this.values);
        return oldRoot;
    }


}



var heap = new MaxBinaryHeap();
// heap.insert(41);
// heap.insert(39);
// heap.insert(33);
// heap.insert(18);
// heap.insert(27);
// heap.insert(12);
heap.insert(70);
heap.insert(67);
heap.insert(65);
heap.insert(45);
heap.insert(58);
heap.insert(40);
heap.insert(53);
heap.insert(44);
heap.insert(15);
heap.insert(31);
```



