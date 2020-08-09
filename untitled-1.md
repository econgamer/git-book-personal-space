---
description: 2020/08/08
---

# Find Longest Substring

## Question

```javascript
console.log("result1: " + findLongestSubstring(''));  //0
console.log("result2: " + findLongestSubstring('rithmschool')); //7
console.log("result3: " + findLongestSubstring('thisisawesome')); //6
console.log("result4: " + findLongestSubstring('thecatinthehat'));  //7
console.log("result5: " + findLongestSubstring('bbbbbbbb'));  //1
console.log("result6: " + findLongestSubstring('longestsubstring'));  //8
console.log("result7: " + findLongestSubstring('thisisshowwedoit'));  //6
```

## Solution

```javascript
function findLongestSubstring(str1){
  // add whatever parameters you deem necessary - good luck!

  let counter = {};
  let initialStr = '';
  let longestLength = 0;
  let startIndex = 0;

  for(var i = 0; i < str1.length ; i++){
    if(counter[str1[i]] !== undefined)
    {
        let length = i - startIndex;  //1 is not required, as i is the next index already
        longestLength = Math.max(length, longestLength);
        i = counter[str1[i]] + 1;
        startIndex = i;

        //console.log("startIndex is: " + startIndex);
        counter = {};
    }

    counter[str1[i]] = i;
    initialStr += str1[i];

    if(i == (str1.length - 1))
    {
//       console.log("i= " + i);
//       console.log("startIndex= " + startIndex);
      let length = i - startIndex + 1;    //1 is the inclusion of the startIndex
      longestLength = Math.max(length, longestLength);
    }


  }

    return longestLength;
}
```

