---
description: 06/08/2020
---

# Same Frequency - Frequency Counter - 06/08/2020

## Question:

```javascript
sameFrequency(321,123);                //true
sameFrequency(59, 19);                 //false
sameFrequency(123456, 654123);       //true
sameFrequency(11, 111);                //false
```

## My Solution:

```javascript
function sameFrequency(num1, num2){
  var string1 = num1.toString();
  var string2 = num2.toString();
  Count = {};
  //console.log("string1.length is: " + string1.length);
  for(let i = 0; i < string1.length; i++){
      if(Count[string1[i]] !== undefined){
          Count[string1[i]] += 1;
      }else{
          //console.log("good");
          Count[string1[i]] = 1;
      }
  }

  for(let i = 0; i < string2.length; i++){
      if(Count[string2[i]] == undefined || !Count[string2[i]]){
          //console.log("false value is: " + Count[string2[i]]);
          return false;
      }else{
          Count[string2[i]] -= 1;
      }
  }

  console.log("Count is equal to: " + Count[8]);

  return true;
}

console.log(sameFrequency(321,123));
console.log(sameFrequency(59, 19));
console.log(sameFrequency(123456, 654123));
console.log(sameFrequency(11, 111));
```

{% hint style="info" %}
O\(n\)
{% endhint %}

