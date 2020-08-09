---
description: 2020/08/08
---

# Is Subsequence

## Question:

```javascript
console.log("result1: " + isSubsequence('hello', 'hello world'));    //true
console.log("result2: " + isSubsequence('sing', 'sting'));   //true
console.log("result3: " + isSubsequence('abc', 'abracadabra'));  //true
console.log("result4: " + isSubsequence('abc', 'acb'));  //false (order matters)
console.log("result5: " + isSubsequence('cddbe', 'acfgdbdbe'));   //true
console.log("result6a: " + isSubsequence('adg', 'daaaaaahg'));   //false
console.log("result6b: " + isSubsequence('adg', 'daaaaaadg'));   //true
```

## Solution:

```javascript
function isSubsequence(str1, str2){

    let firstIndex = 0;
    //let secondIndex = 0;

    for(var secondIndex = 0; secondIndex < str2.length; secondIndex ++)
    {
        if(str1[firstIndex] == str2[secondIndex])
        {
            firstIndex ++;
            if(firstIndex > str1.length - 1)
            {
                return true;
            }
        }
    }
    return false;
}
```

