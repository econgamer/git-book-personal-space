---
description: 04/09/2020
---

# Singly Linked Lists

### Singly Linked Lists:

![https://codeburst.io/js-data-structures-linked-list-3ed4d63e6571](../.gitbook/assets/image%20%2834%29.png)

```javascript
class Node{
    constructor(val){
        this.val = val;
        this.next = null;
    }
}

class SinglyLinkedList{
    constructor(){
        this.head = null;
        this.tail = null;
        this.length = 0;
    }

    push(val){
        let newNode = new Node(val);

        if(this.length === 0){
            this.head = newNode;
            this.tail = newNode;
        }else{
            this.tail.next = newNode;
            this.tail = newNode;
        }
        this.length ++;
        return this;
    }


    pop(){

        if(!this.head) return undefined;

        if(this.tail === this.head){
            var popNode = this.tail;
            this.head = null;
            this.tail = null;
            this.length --;

            return popNode;
        }

        let currentNode = this.head;
        let nextNode = this.head.next;
        
        while(nextNode && nextNode.next){
            currentNode = currentNode.next;
            nextNode = currentNode.next;
        }
        
        this.tail = currentNode;
        this.tail.next = null;
        this.length --;

        return nextNode;
    }


    shift(){
        if(!this.head) return undefined;

        var shiftNode = this.head;
        this.head = this.head.next;
        this.length --;

        if(this.length === 0){
            this.tail = null;
        }

        return shiftNode;
    }


    unshift(val){
        let newNode = new Node(val);
        newNode.next = this.head;
        
        if(!this.head){
            this.tail = newNode;
        }

        this.head = newNode;
        this.length ++;

        return this;
    }


    get(i){
        if(i < 0 || i >= this.length) { return null; }

        var getTarget = this.head;
        for(var count = 0; count < i; count++){
            getTarget = getTarget.next;
        }

        return getTarget;
    }

    set(val, index){
        var nodeToChange = this.get(index);
        
        if(nodeToChange){
            nodeToChange.val = val;
            return true;
        }

        return false;
        
    }

    
    insert(val, index){
        

        if(index <= 0 || index > this.length){
            return false;
        }

        if(index === this.length){
            this.push(val);
            return true;
        }

        if(index === 0){
            this.unshift(val);
            return true;
        }
        
        let newNode = new Node(val);

        var prev = this.get(index - 1);
        newNode.next = prev.next;
        prev.next = newNode;
        this.length ++;
        return true;       
    }


    remove(index){
        if(index < 0 || index >= this.length) return undefined;
        if(index === this.length - 1) return this.pop();
        if(index === 0) return this.shift();
        
        let prev = this.get(index - 1);
        let temp = prev.next;
        prev.next = temp.next;
        this.length --;

        return temp;
    }

    reverse(){
        var headTemp = this.head;
        this.head = this.tail;
        this.tail = headTemp;

        var currentNode = this.tail;
        var nextNode = currentNode.next;
        currentNode.next = null;

        while(nextNode){
            var nextTemp = nextNode.next;
            var currentTemp = nextNode;
            nextNode.next = currentNode;
            nextNode = nextTemp;
            currentNode = currentTemp;
        }

        nextNode
        
        return this;

    }

    print(){
        var arr = [];
        var current = this.head;
        while(current){
            arr.push(current.val);
            current = current.next;
        }

        console.log(arr);
    }


}



var list = new SinglyLinkedList()
list.push("HELLO")
list.push("GOODBYE")
list.push("!!!!")
list.push("1")
list.push("2")
list.push("3")
list.push("4")
list.push("5")
list.push("6")
// list.get(2);
// list.set("dabb", 1);
//console.log("list: " + list);

```





