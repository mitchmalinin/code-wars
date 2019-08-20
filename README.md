# code-wars

This is where I post my code wars challanges.

# Challange 1
Name: Format a string of names like 'Bart, Lisa & Maggie'
- kyu: 6
- Given: an array containing hashes of names
- Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.

My Solution:
```
function list(names) {
  let newArr = []
  let finalString;
  //your code here
  names.forEach((name) => {
    newArr.push(name.name);
  })
  let slicedArr = newArr.slice(newArr.length - 2);
  let otherSliced = newArr.slice(0, newArr.length - 2)
  otherSliced = otherSliced.join(', ');
  slicedArr = slicedArr.join(' & ');

  if (newArr.length <= 2) {
    finalString = slicedArr
  }
  else {
    finalString = otherSliced + ', ' + slicedArr
  }
  return finalString
}
```
# Challange 2
Name: Detect Pangram 
- kyu: 6
- A pangram is a sentence that contains every single letter of the alphabet at least once. For example, the sentence "The quick brown fox jumps over the lazy dog" is a pangram, because it uses the letters A-Z at least once (case is irrelevant).
- Given a string, detect whether or not it is a pangram. Return True if it is, False if not. Ignore numbers and punctuation.

My Solution:
```
function isPangram(string){
 let arr = [];
string = string.replace(/[^A-Za-z']/g, "").toLowerCase();
  cleanedString = string.split('').sort();
  cleanedString.forEach((letter)=>{
    if(arr.includes(letter) === false){
        arr.push(letter)
      } 
  })
  if(arr.length === 26){
    return true
  }
  else{
    return false
  }
}
```
# Challange 3 

Name: List Filtering
- kyu: 7
- In this kata you will create a function that takes a list of non-negative integers and strings and returns a new list with the strings filtered out.

My Solution:
```
function filter_list(l) {
let newArr = l.filter((elm)=>{
  return typeof elm === 'number';
})
  return newArr
}
```
# Challange 4 
Name: Find the missing letter
- kyu: 6
- Write a method that takes an array of consecutive (increasing) letters as input and that returns the missing letter in the array.
- You will always get an valid array. And it will be always exactly one letter be missing. The length of the array will always be at least 2.
- The array will always contain letters in only one case.

My Solution:
```
function findMissingLetter(array)

{
  let missingValue;
  let finalLetter;
  let newArr = [];
 let stringArr = array.toString().split(',')
 stringArr.forEach((letter)=>{
   newArr.push(letter.charCodeAt(0))
 })
 
  for(i = 0; i < newArr.length-1; i++){
    if(newArr[i] + 1 == newArr[i+1]){
      console.log("true")
    }
    else{
      console.log(newArr[i])
      missingValue = newArr[i]+1
    }
  }
finalLetter = String.fromCharCode(missingValue) 
return finalLetter
}
```

# Challange 5
Name: Fake Binary
- kyu: 7
- Given a string of digits, you should replace any digit below 5 with '0' and any digit 5 and above with '1'. Return the resulting string.

My Solution:
```
function fakeBin(x){
let newArr = x.split('')
newArr.forEach((num,i)=>{
  if(num < 5){
   newArr[i] = 0
  }
  else{
    newArr[i] = 1
  }
})
return newArr.join('')
}
```

# Challange 6

Name: Two fighters, one winner.
- kyu: 7
- Create a function that returns the name of the winner in a fight between two fighters.
- Each fighter takes turns attacking the other and whoever kills the other first is victorious. Death is defined as having health <= 0.
- Each fighter will be a Fighter object/instance. See the Fighter class below in your chos- en language.
- Both health and damagePerAttack (damage_per_attack for python) will be integers larger than 0. You can mutate the Fighter objects.

My Solution:
```
function declareWinner(fighter1, fighter2,firstAttacker) {
  let winner = ""
  
  if (firstAttacker === fighter1.name){
   while(fighter1.health > 0 &&  fighter2.health > 0){
      fighter2.health = fighter2.health - fighter1.damagePerAttack;
      if(fighter2.health <= 0){
        winner = fighter1.name
      }
      else{
         fighter1.health = fighter1.health - fighter2.damagePerAttack;
         if(fighter1.health <= 0){
           winner = fighter2.name
         }
      }
    } 
  }
  else{
     while(fighter1.health > 0 &&  fighter2.health > 0){
      fighter1.health = fighter1.health - fighter2.damagePerAttack;
      if(fighter1.health <= 0){
        winner = fighter2.name
      }
      else{
         fighter2.health = fighter2.health - fighter1.damagePerAttack;
         if(fighter2.health <= 0){
           winner = fighter1.name
         }
      }
    }
  }
return winner;
}
```

# Challange 7

Name: Make a function that does arithmetic!
- kyu: 7
- Given two numbers and an arithmetic operator (the name of it, as a string), return the result of the two numbers having that operator used on them.
- a and b will both be positive integers, and a will always be the first number in the operation, and b always the second.
- The four operators are "add", "subtract", "divide", "multiply".

My Solution:
```
function arithmetic(a, b, operator){
  switch (operator){
  case "add":
  return a + b;
  break;
  case "subtract":
  return a - b;
  break;
  case "multiply":
  return a * b;
  break;
  case "divide":
  return a / b;
  break;
  }
} 
```

# Challange 8

Name: Sum of odd numbers
- kyu: 7
- Given the triangle of consecutive odd numbers:
- example: 
```                   
                      1
                   3     5
                 7     9    11
             13    15    17    19
          21    23    25    27    29
```
- Calculate the row sums of this triangle from the row index (starting at index 1) e.g.:

My Solution:
```
function rowSumOddNumbers(n) {
  let oddNum = 1
  let obj = {}
    for(let i = 1; i <= n; i++){
        let test = Array(i)
        for(let j = 0;j < test.length; j++){
          test[j] = oddNum
          oddNum = oddNum + 2
        }
        obj[i] = test
      }
 return obj[n].reduce((a,b)=>{
    return a + b
 })
}
```
# Challange 9

Name: Break camelCase
- kyu: 6
- Complete the solution so that the function will break up camel casing, using a space between words.

My Solution:
```
function solution(string) {
  string = string.split("")
  for(let i = 0;i< string.length;i++){
    if(string[i] == string[i].toUpperCase()){
        string[i] = " " + string[i]
    }
  }
  return string.join("")
}
```
# Challange 10

Name: The highest profit wins!
- kyu: 7
- Write a function that returns both the minimum and maximum number of the given list/array.

My Solution:
```
function minMax(arr){ 
  return [Math.min(...arr),Math.max(...arr)];
}

```

# Challange 11
** CODE WARS WAS DOWN THIS DAY, SO I DID AN ALGODAILY PROBLEM. **
Name: Reverse Only Alphabetical

- You are given a string that contains alphabetical characters (a - z, A - Z) and some other characters ($, !, etc.). For example, one input may be:
- 'sea!$hells3'
- Can you reverse only the alphabetical ones?

My Solution:
```
 function reverseOnlyAlphabetical(str) {
  let count = 0;
  str = str.split("");
  let filteredArr = str.filter((char)=>{
      return char.match(/[a-zA-Z]+/g);
  });
  filteredArr.reverse();
  str.forEach((char,i)=>{
    if(char.match(/[a-zA-Z]+/g)){
      console.log(count);
      str[i] = filteredArr[count];
      count++;
           console.log(count);
    }
  });
  return str.join("");
}

```
# Challange 12
** CODE WARS WAS STILL DOWN THIS DAY, SO I DID AN ALGODAILY PROBLEM. **
Name: Is An Anagram

- We are given two strings like "cinema" and "iceman" as inputs. Can you write a method isAnagram(str1, str2) that will return  true or false depending on whether the strings are anagrams of each other?

My Solution:
```
function isAnagram(str1, str2) {
  str1 = str1.toLowerCase().split("").sort().join("");
  str2 = str2.toLowerCase().split("").sort().join("");
  return str1 === str2;
}

```
# Challange 13
** BACK TO CODE WARS **
Name: Categorize New Member Kyu: 7

- The Western Suburbs Croquet Club has two categories of membership, Senior and Open. They would like your help with an application form that will tell prospective members which category they will be placed.
- To be a senior, a member must be at least 55 years old and have a handicap greater than 7. In this croquet club, handicaps range from -2 to +26; the better the player the lower the handicap.
- Input will consist of a list of lists containing two items each. Each list contains information for a single potential member. Information consists of an integer for the person's age and an integer for the person's handicap.
- Output will consist of a list of string values (in Haskell: Open or Senior) stating whether the respective member is to be placed in the senior or open category.

My Solution:
```
function openOrSenior(data){
  let openOrSeniorArr = [];
   data.map((elm)=>{
    if(elm[0] >= 55 && elm[1] > 7)
    {
      openOrSeniorArr.push("Senior")
    }
    else{
      openOrSeniorArr.push("Open")
    }
  })
  return openOrSeniorArr
}

```
# Challange 14
Name: Sort the odd
Kyu: 6

- You have an array of numbers.
- Your task is to sort ascending odd numbers but even numbers must be on their places.
- Zero isn't an odd number and you don't need to move it. If you have an empty array, you need to return it.

My Solution:

```
function sortArray(array) {
  let count = 0;
  let oddArray = array.filter((num)=>{
    if(num != 0 && num % 2 != 0){
      return num
    }
  })
oddArray.sort((a,b)=>{
  return  a - b
});
  array.forEach((num, i)=>{
    if(num % 2 != 0){
      array[i] = oddArray[count]
      count++
    }    
  })
  return array
}

```



