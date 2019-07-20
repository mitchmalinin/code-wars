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
