# code-wars

This is where I post my code wars challanges.

# Challange 1
Name: Format a string of names like 'Bart, Lisa & Maggie'.
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
