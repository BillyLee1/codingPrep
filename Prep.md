Question #1: Turning Strings to URLs
URLs cannot have spaces. Instead, all spaces in a string are replaced with %20. Write an algorithm that replaces all spaces in a string with %20.

You may not use the replace() method or regular expressions to solve this problem. Solve the problem with and without recursion.

Example
Input: "Jasmine Ann Jones"

Output: "Jasmine%20Ann%20Jones"

Steps:
  1. Loop through string.
  2. If loop encounters a space, replace space with %20.
  3. If it is not a space, nothing will happen to it.

*Without recursion*

function spaceFinder(string) {
  let final = "";
  for(let i = 0; i < string.length; i++) {
    if (string[i] === " ") {
      final += "%20";
    } else {
      final += string[i]
    }
  }

  return final;
}

*With recursion*

function spaceFinderRecursion(string, index = 0) {
  //checks if index is at string length, if it is, stop recursion.
  if (index === string.length) { 
    return string;
  }

  if (string[index] === " ") {
    string = string.slice(0, index) + "%20" + string(index + 1)
    index += 2;
  }

  return spaceFinderRecursion(string, index + 1);

}

Question #2: Array Deduping
Write an algorithm that removes duplicates from an array. Do not use a function like filter() to solve this. Once you have solved the problem, demonstrate how it can be solved with filter(). Solve the problem with and without recursion.

Steps:
1. Go through list of items in array.
2. Add unique items into a new array.
3. If item already exists in the new array, skip to next item

function arrayDeDupe(arr) {
  let uniqueArr = [];

  for (let i = 0; i < arr.length; i++) {
    if (!uniqueArr.includes(arr[i])) {
      uniqueArr.push(arr[i]);
    }
  }
  return uniqueArr;
}

Using filter()

function arrayDeDupeFilter(arr) {
  return arr.filter((item, index) => arr.indexOf(item) === index);
}

Question #3: Compressing Strings
Write an algorithm that takes a string with repeated characters and compresses them, using a number to show how many times the repeated character has been compressed. For instance, aaa would be written as 3a. Solve the problem with and without recursion.

Steps:
1. Go through each item in string and see if the next item is the same.
2. If it is the same, add a count.
3. Keep adding count until it the next item is not the same.
4. Add the count number and unique item to a new string.

function compressString(string) {
  let count = 1;
  let uniqueItem = "";
  let compressed = "";
  for (let i = 0; i < string.length; i++) {
    uniqueItem = string[i];
    if (string[i] === string[i + 1]) {
      count++;
      uniqueItem = string[i];
    } else {
      compressed += count + uniqueItem;
      count = 1;
    }
  }

  return compressed;
}

function compressStringRecursion(string) {
  if (string === "") {
    return "";
  }
  let count = 1;
  while (string[count] === string[0]) {
    count++;
  }
  return count + string[0] + compressStringRecursion(string.slice(count));
}

Question #4: Checking for Uniqueness
Write an algorithm that determines whether all the elements in a string are unique. You may not convert the string into an array or use array methods to solve this problem. The algorithm should return a boolean.

function uniqueChars(string) {
  for (let i = 0; i < string.length; i ++) {
    for (let j = i + 1; j < string.length; j++) {
      if (string[i] === string[j]) {
        return false;
      }
    }
  }
  return true;
}
