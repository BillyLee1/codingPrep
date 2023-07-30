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
