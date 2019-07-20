# code-wars

This is where I do my daily code wars challanges.

# Challange 1
Name: Format a string of names like 'Bart, Lisa & Maggie'.
- Given: an array containing hashes of names
- Return: a string formatted as a list of names separated by commas except for the last two names, which should be separated by an ampersand.

My Solution:

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

# Challange 2
