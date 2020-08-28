---
description: 28/08/2020
---

# Graph - undirected edges



![source: https://www.geeksforgeeks.org/count-number-edges-undirected-graph/](../.gitbook/assets/image%20%2832%29.png)



### Sorting:

```javascript
class Graph{
    constructor(){
        this.adjacencyList = {};
    }

    addVertex(val){
        if(!val) return undefined
        if(!this.adjacencyList[val]) this.adjacencyList[val] = [];
        return this;
    }

    addEdge(vertex1, vertex2){
        this.adjacencyList[vertex1].push(vertex2);
        this.adjacencyList[vertex2].push(vertex1);

        return this;
    }

    removeEdge(v1, v2){
//         for(var i = 0; i < this.adjacencyList[v1].length; i++){
//             if(this.adjacencyList[v1][i] === v2){
//                 this.adjacencyList[v1].splice(i,1);
//             }
//         }

        this.adjacencyList[v1] = this.adjacencyList[v1].filter(v => v !== v2);
        this.adjacencyList[v2] = this.adjacencyList[v2].filter(v => v !== v1);

//         for(var i = 0; i < this.adjacencyList[v2].length; i++){
//             if(this.adjacencyList[v2][i] === v1){
//                 this.adjacencyList[v2].splice(i,1);
//             }
//         }
 
        return this;
    }

    removeVertex(v1){
        for(var i = 0; i < this.adjacencyList[v1].length; i++){
            var tempKey = this.adjacencyList[v1][i];
             this.adjacencyList[tempKey] = this.adjacencyList[tempKey].filter(v => v != v1);
//            this.removeEdge(v1, this.adjacencyList[v1][i]);
        }
        delete this.adjacencyList[v1];
        return this;
    }

// Depth First Search
     dfsRecur(startingV1){
        var visited = {};
        var result = [];

        visitVertex.call(this, startingV1);

        function visitVertex(v1Key){

            if(!v1Key) return null;
            visited[v1Key] = true;
            result.push(v1Key);
            
            var keyNext;

            console.log("goody");

            for(var i = 0; i < this.adjacencyList[v1Key].length; i++){
                keyNext = this.adjacencyList[v1Key][i];
                if(!visited[keyNext]){
                    visitVertex.call(this, keyNext);;
                }
            }
        }

        return result;
    }



    dfsiterative(starting){
        var visited = {};
        var result = [];
        var stack = [];
        stack.push(starting);

        while(stack.length > 0){
            var currentVert = stack.pop();
            console.log("this.adjacencyList[currentVert]:" , this.adjacencyList[currentVert]);
            if(!visited[currentVert]){

                visited[currentVert] = true;
                result.push(currentVert);

                this.adjacencyList[currentVert].forEach(v1 => {

                stack.push(v1);

                })

            }
            
            

        }

        


        return result;
    }



//Breadth first Search
    bfsiterative(starting){
        var visited = {};
        var result = [];
        var stack = [];
        stack.push(starting);

        while(stack.length > 0){
            var currentVert = stack.shift();
            console.log("this.adjacencyList[currentVert]:" , this.adjacencyList[currentVert]);
            if(!visited[currentVert]){

                visited[currentVert] = true;
                result.push(currentVert);

                this.adjacencyList[currentVert].forEach(v1 => {

                stack.push(v1);

                })

            }
            
            

        }

        


        return result;
    }


}


var g = new Graph();
// g.addVertex("Michael");
// g.addVertex("Maria");
// g.addVertex("Elise");
// g.addEdge("Maria", "Michael");
// g.addEdge("Maria", "Elise");
// g.addEdge("Michael", "Elise");
g.addVertex("A")
g.addVertex("B")
g.addVertex("C")
g.addVertex("D")
g.addVertex("E")
g.addVertex("F")

g.addEdge("A", "B")
g.addEdge("A", "C")
g.addEdge("B", "D")
g.addEdge("C", "E")
g.addEdge("D", "E")
g.addEdge("D", "F")
g.addEdge("E", "F")
```



