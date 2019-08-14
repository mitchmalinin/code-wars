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


