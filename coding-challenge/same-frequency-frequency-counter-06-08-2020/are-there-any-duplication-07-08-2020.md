---
description: 07/08/2020
---

# Are there any Duplication? - 07/08/2020

## Question:

```text
anyDuplication(1,2,2);                //true
anyDuplication(1,2);                 //false
anyDuplication("a", "b", "a");       //true
anyDuplication("a", "b", "c", "d");                //false
```

{% hint style="info" %}
Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

## Solutions:

Solution1 \(using frequency counter\):

```javascript
function areThereDuplicates(...args) {
    var counter = {};
    //console.log("args length is: " + args);
    for(var i = 0; i < args.length; i++)
    {
        //console.log("loop: " + i);
        if(counter[args[i]] !== undefined)
        {
            return true;
        }else
        {
        //  console.log("trigger");
          counter[args[i]] = true;  
        }
    }


  return false;
  // good luck. (supply any arguments you deem necessary.)
}

console.log(areThereDuplicates(1,2,2));
console.log(areThereDuplicates('a','b','c','d'));
```

Solution2 \(using multi-pointers\)

```javascript
function areThereDuplicates(...args) {
    var counter = {};
    var j = args.length;
    //console.log("args length is: " + args);
    for(var i = 0; i < args.length; i++)
    {
        if(args[i] !== args[j])
        {
            j -= 1;
        }else{
            return true;
        }
    }


  return false;
  // good luck. (supply any arguments you deem necessary.)
}

console.log(areThereDuplicates(1,2,2));
console.log(areThereDuplicates('a','b','c','d'));
```

Bonus:

```javascript
function areThereDuplicates() {
  return new Set(arguments).size !== arguments.length;
}
```

