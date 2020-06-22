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

# Challange 15
Name: Extract the domain name from a URL
Kyu: 5

- Write a function that when given a URL as a string, parses out just the domain 
My Solution:

```

function domainName(url){
return url.replace(/^(?:https?:\/\/)?(?:www\.)?(?:http\.)?/i, "").split(".")[0];
}

```


# Challange 16
Name: Two Sum
Kyu: 6

- Write a function that takes an array of numbers (integers for the tests) and a target number. It should find two different items in the array that, when added together, give the target value. The indices of these items should then be returned in an array.

My Solution:

```
function twoSum(numbers, target) {
  let completedArr;
  for(let i = 0; i< numbers.length;i++){
    for(let j = 1; j < numbers.length;j++){
      if(numbers[i] + numbers[j] == target){
        return completedArr = [i,j]
      }
    }
  }
}

```

# Challange 17
Name: Array Helpers
Kyu: 6

- This kata is designed to test your ability to extend the functionality of built-in classes. In this case, we want you to extend the built-in Array class with the following methods: square(), cube(), average(), sum(), even() and odd().

- Explanation:
- square() must return a copy of the array, containing all values squared
- cube() must return a copy of the array, containing all values cubed
- average() must return the average of all array values; on an empty array must return NaN (note: the empty array is not tested in Ruby!)
- sum() must return the sum of all array values
- even() must return an array of all even numbers
- odd() must return an array of all odd numbers

My Solution:

```
Array.prototype.square = function(){
  return this.map((num)=>{
    return Math.pow(num,2)
  })
}
Array.prototype.cube = function(){
  return this.map((num)=>{
    return Math.pow(num,3)
  })
}
Array.prototype.average = function(){
if(this.length == 0){
  return NaN  
}
else{
   let sum = this.reduce((a,b)=>{
    return a + b
  })
  return sum/this.length;
  }
}

Array.prototype.sum = function(){
   return this.reduce((a,b)=>{
    return a + b
  })
}

Array.prototype.even = function(){
   return this.filter((num)=>{
    return num % 2 == 0
  })
}

Array.prototype.odd = function(){
   return this.filter((num)=>{
    return num % 2 != 0
  })
}

```
# Challange 16
Name: Prefill an Array
Kyu: 6

- Create the function prefill that returns an array of n elements that all have the same value v. See if you can do this without using a loop.
- You have to validate input:
- v can be anything (primitive or otherwise)
- if v is ommited, fill the array with undefined
- if n is 0, return an empty array
- if n is anything other than an integer or integer-formatted string (e.g. '123') that is >=0, throw a TypeError
- When throwing a TypeError, the message should be n is invalid, where you replace n for the actual value passed to the function.

My Solution:

```
function prefill(n, v) {
  if(isNaN(parseInt(n)) || !isNaN(n) && Math.round(n) != n || n < 0){
    throw new TypeError([`${n} is invalid`])
  }
  else {
  n = parseInt(n)
  let preFilledArr = new Array(n);
  preFilledArr.fill(v)
  return preFilledArr;
  }
}


```

# Challange 17
Name: Exclamation marks series #17: Put the exclamation marks and question marks to the balance, Are they balanced?
Kyu: 6

- Each exclamation mark weight is 2; Each question mark weight is 3. Put two string left and right to the balance, Are they balanced?
- If the left side is more heavy, return "Left"; If the right side is more heavy, return "Right"; If they are balanced, return "Balance".

My Solution:

```
function balance(left,right){
  let leftTotal = 0;
  let rightTotal = 0;
 for(let i = 0;i< left.length;i++){
   if(left.charAt(i) == "!"){
     leftTotal += 2
   }
   else{
     leftTotal += 3
   }
 }
 for(let i = 0;i< right.length;i++){
   if(right.charAt(i) == "!"){
     rightTotal += 2
   }
   else if(right.charAt(i)=="?"){
     rightTotal += 3
   }
 }
if(leftTotal > rightTotal){
  return "Left"
}
else if(rightTotal >leftTotal  ){
  return "Right"
}
else{
return "Balance"
  }
}


```

# Challange 17
*ALGODAILY CHALLANGE* 
- Given a string str, can you write a method that will return True if is a palindrome and False if it is not? If you'll     recall, a palindrome is defined as "a word, phrase, or sequence that reads the same backward as forward". For now, assume that we will not have input strings that contain special characters or spaces.
- For an extra challenge, try to ignore non-alphanumerical characters. The final solution that we present will handle all edge cases.

My Solution: 

```
function isPalindrome(str) {
  if(str.indexOf(" ") > 0){
    str = str.toLowerCase().split(" ").join('').split('').join('')
    stringToCheck = str.toLowerCase().split(" ").join('').split('').reverse().join('')
    
  }
  
  else{
  stringToCheck = str.toLowerCase().split("").reverse().join('');
  console.log("niz")
  }
  
  if(str == stringToCheck){
    return true
  }
  else{
    return false;
  }
}
```
# Challange 18
- Mothers arranged a dance party for the children in school. At that party, there are only mothers and their children. All are having great fun on the dance floor when suddenly all the lights went out. It's a dark night and no one can see each other. But you were flying nearby and you can see in the dark and have ability to teleport people anywhere you want.
- Uppercase letters stands for mothers, lowercase stand for their children, i.e. "A" mother's children are "aaaa".
- Function input: String contains only letters, uppercase letters are unique.
- Place all people in alphabetical order where Mothers are followed by their children, i.e. "aAbaBb" => "AaaBbb".

My Solution: 

```
function findChildren(dancingBrigade){
let arr = dancingBrigade.toLowerCase().split("").sort();
arr[0] = arr[0].toUpperCase()
let  tempChar = arr[0];
arr.forEach((elm,i)=>{
if(elm.toUpperCase() != tempChar){
  arr[i] = arr[i].toUpperCase();
  tempChar = arr[i];
  }
})
  return arr
};
```
# Challange 19
- Bob is preparing to pass IQ test. The most frequent task in this test is to find out which one of the given numbers differs from the others. Bob observed that one number usually differs from the others in evenness. Help Bob — to check his answers, he needs a program that among the given numbers finds one that is different in evenness, and return a position of this number.
- ! Keep in mind that your task is to help Bob solve a real IQ test, which means indexes of the elements start from 1 (not 0)

My Solution: 

```
function iqTest(numbers){
numbers =  numbers.split(" ");
let evenArr = [];
let oddArr = [];
numbers.forEach((elm)=>{
  (elm % 2 == 0) ? evenArr.push(elm) : oddArr.push(elm)
 })
 if(evenArr.length > oddArr.length){
   oddNum = oddArr.join("");
   return numbers.indexOf(oddNum) + 1
 }
 else{
   evenNum = evenArr.join("");
   return numbers.indexOf(evenNum) + 1
 }
}
```

# Challange 20
- Implement the function unique_in_order which takes as argument a sequence and returns a list of items without any elements with the same value next to each other and preserving the original order of elements.

My Solution: 

```
var uniqueInOrder=function(iterable){
 if(Array.isArray(iterable) === false){
   iterable = iterable.split("")
 }
 if(iterable.length == 0){
 return []
 }
  tempElm = iterable[0];
  let uniqueArr = [];
  uniqueArr.push(tempElm)
  iterable.forEach((elm)=>{
    if(elm != tempElm){
      tempElm = elm;
      uniqueArr.push(tempElm)
    }
  })
  return uniqueArr
}
```
# Challange 21
- Given a number, return a string with dash'-'marks before and after each odd integer, but do not begin or end the string with a dash mark.

My Solution: 

```
function dashatize(num) {
let newThing = num.toString().split("")
let endOfArray = newThing.length
newThing.forEach((elm,i)=>{
  if(elm == "-"){
    newThing.splice(i,1)
  }
})

if(newThing.length == 1){
  return newThing.join("")
}
newThing.map((elm,i)=>{
if(elm/1 && elm % 2 != 0 && i != 0 && i != newThing.length-1){
  newThing[i] = "-" + newThing[i] + "-"
}
else if(elm/1 && elm % 2 != 0 && i == 0){
newThing[i] = newThing[i] + "-"
}
else if(elm/1 && elm % 2 != 0 && i == newThing.length-1){
newThing[i] =  "-"  + newThing[i] 
}
  });
newThing = newThing.join("").split("")
newThing.forEach((elm,i)=>{
  console.log(newThing)
  if(elm == newThing[i+1] && newThing[i+1] == "-" || elm == newThing[i-1] && newThing[i-1] == "-" ){
    console.log(newThing[i])
    newThing.splice(i,1)
  }
})
return newThing.join("")
}
```
# Challange 22
- The depth of an integer n is defined to be how many multiples of n it is necessary to compute before all 10 digits have appeared at least once in some multiple.

My Solution: 

```
function computeDepth(num){
let multiplier = 0
let numSet = new Set();
  while(numSet.size != 10){
    multiplier++
    value = num * multiplier+""
    value = value.split("").forEach((elm)=>{
    numSet.add(elm)
    })
  }
return multiplier
}
```
# Challange 23
- In this kata you are required to, given a string, replace every letter with its position in the alphabet.
- If anything in the text isn't a letter, ignore it and don't return it.

My Solution: 

```
function alphabetPosition(text) {
text = text.toLowerCase().replace(/[^a-z]/g, '').split("") 
let lettersToNumbers = {
  "a":1,"b":2,"c":3,"d":4,"e":5,"f":6,"g":7,"h":8,"i":9,"j":10,"k":11,"l":12,"m":13,"n":14,"o":15,"p":16,"q":17,"r":18,"s":19,"t":20,"u":21,"v":22,"w":23,"x":24,"y":25,"z":26
  }
text.map((elm,i)=>{
for(key in lettersToNumbers){
  if(elm == key){
    text[i] = lettersToNumbers[key]
    } 
  }
})  

return text.join(" ")
}

```

# Challange 24

- Build Tower by the following given argument:
- number of floors (integer and always greater than 0).
- Tower block is represented as *

My Solution: 

```
function towerBuilder(nFloors) {
let arr = new Array(nFloors).fill('');
let addStar = '*'
const baseStar = '*'
let space = " "
  arr.forEach((elm,i)=>{
  arr[i] = space.repeat(nFloors - 1) + addStar + space.repeat(nFloors - 1)
  nFloors--
  addStar =  addStar + baseStar.repeat(2)
  })
return arr
}

```
# Challange 24

- Your message is a string containing space separated words.
- You need to encrypt each word in the message using the following rules:
- The first letter needs to be converted to its ASCII code.
- The second letter needs to be switched with the last letter

My Solution: 

```
var encryptThis = function(text) {
  let wordArr = text.split(" ");
  let newArr = wordArr.map((elm)=>{
    elm = elm.split("");
    let secondLetter = elm[1];
    let lastLetter = elm[elm.length-1];
    elm[0] = elm[0].charCodeAt(0)
    elm[1] = lastLetter
    elm[elm.length-1] = secondLetter
    return elm.join("")
  })
  return newArr
}

```

# Challange 25

- Your goal in this kata is to implement a difference function, which subtracts one list from another and returns the result.
- It should remove all values from list a, which are present in list b.

My Solution: 

```
function arrayDiff(a, b) {
 b.forEach((elm)=>{
  for(let i = a.length; i >= 0; i--){
    if(elm === a[i]){
      a.splice(i,1)
    }
  }
 })
 return a
}
```
# Challange 26

- Given an array, find the integer that appears an odd number of times.
- There will always be only one integer that appears an odd number of times.

My Solution: 

```
function findOdd(A) {
  let nums = {}
  A.forEach((num)=>{
    nums[num] === undefined ? nums[num] = 1 : nums[num] = nums[num]+ 1
  })
  for (const value in nums){
    if(nums[value] % 2 != 0){
      return Number(value)
    }
  }
}
```
# Challange 27

- In this kata, you must create a digital root function.
- A digital root is the recursive sum of all the digits in a number. Given n, take the sum of the digits of n. If that value has more than one digit, continue reducing in this way until a single-digit number is produced. This is only applicable to the natural numbers.

My Solution: 

```
function digital_root(n) {
 n = n.toString().split('').reduce((a,b)=>{
    return Number(a) + Number(b)
  });
  if(n <  10){
    return n
  }
 return digital_root(n)
}

//TEST
digital_root(456)

```
# Challange 28

- You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this "outlier" N.

My Solution: 

```
function findOutlier(integers){
  let oddArr = [];
  let evenArr = []
  integers.forEach((elm)=>{
    elm % 2 == 0 ? evenArr.push(elm) : oddArr.push(elm)
  })
  return oddArr.length == 1 ?  oddArr[0] :  evenArr[0]
}

//TEST
findOutlier([0, 1, 2])

```
# Challange 29

- Write a function that will return the count of distinct case-insensitive alphabetic characters and numeric digits that occur more than once in the input string. The input string can be assumed to contain only alphabets (both uppercase and lowercase) and numeric digits.

My Solution: 

```
function duplicateCount(text){
  const numSet = {}
  let totalNumOfDups = 0;
  text.toLowerCase().split('').forEach((elm)=>{
    if(numSet[elm] == undefined){
      numSet[elm] = 1
    }
    else{
      numSet[elm] = numSet[elm] + 1
    }
  })
  for(key in numSet){
    if(numSet[key] > 1){
      totalNumOfDups++
    }
  }
return totalNumOfDups
}

//TEST
duplicateCount("aabBcde111")

```
