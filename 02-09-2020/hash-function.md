---
description: 02/09/2020
---

# Hash Function

![https://en.wikipedia.org/wiki/Hash\_table](../.gitbook/assets/image%20%2833%29.png)

```javascript
// function hash(key, arrayLen){
//     let total = 0;
//     let WEIRD_PRIME = 31;
//     for (let i = 0; i < Math.min(key.length, 100); i++){
//         let char = key[i];
//         let value = char.charCodeAt(0) - 96;
//         total = (total * WEIRD_PRIME + value) % arrayLen;
//     }
//     return total;
// }


class HashTable{
    constructor(size=5){
        this.keyMap = new Array(size);
    }

    _hash(key){
        let total = 0;
        let WEIRD_PRIME = 31;
        for(let i = 0; i < Math.min(key.length, 100); i++){
            let char = key[i];
            let value = char.charCodeAt(0) - 96;
            total = (total * WEIRD_PRIME + value) % this.keyMap.length;
        }
        return total;
    }

    set(key, value){
        var hashKey = this._hash(key);
        if(!this.keyMap[hashKey]){
            this.keyMap[hashKey] = [];
        }

        this.keyMap[hashKey].push([key, value]);

        return this;
    }

    get(key){
        var hashKey = this._hash(key);
        
        var arrayGet = this.keyMap[hashKey];
        var result;

        if(arrayGet){
//             console.log("arrayGet: ", arrayGet);
            arrayGet.forEach(element => 
                {
//                     console.log("element: ", element);
                    if(element[0] === key){
                        result = element;
                    }
                }
            );
        }

       return result;
    }


    
    keys(){
        var temp = [];
        var temp2 = [];
        var result = [];
        for(var i = 0; i < this.keyMap.length; i++){
            var temp = temp.concat(this.keyMap[i]);
        }
        for(var i = 0; i < temp.length; i++){
            if(temp[i]){
                temp2 = temp2.concat(temp[i]);
            }  
        }

        for(var i = 0; i < temp2.length; i+=2){
            if(!result.includes(temp2[i])){
                result.push(temp2[i]);
            }  
        }
        return result;
    }


    values(){
        var temp = [];
        var temp2 = [];
        var result = [];
        for(var i = 0; i < this.keyMap.length; i++){
            var temp = temp.concat(this.keyMap[i]);
        }
        for(var i = 0; i < temp.length; i++){
            if(temp[i]){
                temp2 = temp2.concat(temp[i]);
            }  
        }

        for(var i = 1; i < temp2.length; i+=2){
            result.push(temp2[i]);
        }
        return result;
    }



}



var hashTable = new HashTable();
hashTable.set("elise", "queen");
hashTable.set("pink", "#00123");
hashTable.set("table", "brown");
hashTable.set("monkey", "banana");
hashTable.set("tele", "baby");
hashTable.set("monkey", "banana2");



```



