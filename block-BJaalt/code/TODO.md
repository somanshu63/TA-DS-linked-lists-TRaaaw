## Solve the list of given problems:

For the given problems below write a function to solve the problem and write two test/example testing your solution.

1. Write Algorithms to Check if Two String are Anagram. An anagram is something where length and character matches but not the order like `listen` and `silent`, both have the same number of characters.

```js
function anagram(wordOne, wordTwo) {
  var isAnagram = false;
  if (wordOne.split("").length === wordTwo.split("").length) {
    wordOne
      .split("")
      .sort()
      .every(function (one, two) {
        one === wordTwo.split("").sort()[two]
          ? (isAnagram = true)
          : (isAnagram = false);
      });
  }
  return isAnagram;
}
```

2. Given two non-empty array of numbers, write a function to find whether the second array is a subsequence of the first array or not.

```js
function isValidSubsequence(array, sequence) {
  let counter = 0;
  for (let i = 0; i < array.length; i++) {
    let curNum = array[i];
    if (sequence[counter] === curNum) {
      counter++;
    }
    if (counter === sequence.length) {
      return true;
    }
  }
  return false;
}
isValidSubsequence([1, 5, 23, 32, -42, 100], [23, 32, -42]); // true
isValidSubsequence([1, 5, 23, 32, -42, 100], [200, 23, 32, -42]); // false
```

A subsequence is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements. For example, [3,6,2,7] is a subsequence of the array [0,3,1,6,2,2,7].

Example 1:

First array is `[1, 5, 23, 32, -42, 100]` and second array is `[23, 32, -42]`. In this example the second array is a subsequence of the first array.

Example 2:

First array is `[1, 5, 23, 32, -42, 100]` and second array is `[200, 23, 32, -42]`. In this example the second array is not a subsequence of the first array.

3. Hamming Distance

the Hamming distance between two strings of equal length is the number of positions at which the corresponding symbols are different. In other words, it measures the minimum number of substitutions required to change one string into the other, or the minimum number of errors that could have transformed one string into the other. In a more general context, the Hamming distance is one of several string metrics for measuring the edit distance between two sequences.

```js
function hammingDistance(a, b) {
  if (a.length !== b.length) {
    throw new Error("Strings must be of the same length");
  }

  let distance = 0;

  for (let i = 0; i < a.length; i += 1) {
    if (a[i] !== b[i]) {
      distance += 1;
    }
  }

  return distance;
}
```

Examples:

Input: `karolin` and `kathrin`
Output: 3

Input: `karolin` and `kerstin`
Output: 3

Input: `1011101` and `1001001`
Output: 3

4. For a given number, find all the prime numbers in an array from zero to that number.

```js
function isPrime(n) {
  if (n <= 1) return false;
  for (let i = 2; i < n; i++) {
    if (n % i == 0) {
      return false;
    }
  }
  return true;
}
function getAllPrimeNumbers(number) {
  const numbers = new Array(number + 1).fill(undefined);

  return numbers
    .map((_val, index) => (isPrime(index) ? index : false))
    .filter(Boolean);
}
// Test
let primeNumbers = getAllPrimeNumbers(100); // [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]
```

5. Given a phrase, reverse the order of the characters of each word.

Example:

"I love JavaScript!" will become "I evol !tpircSavaJ"

```js
function reverseWord(string) {
  return string
    .split(" ")
    .map((word) => word.split("").reverse().join(""))
    .join(" ");
}
function reverseWords(string) {
  return string
    .split(" ")
    .map((word) => reverseWord(word))
    .join(" ");
}
// Test
reverseWords("I love JavaScript!"); // "I evol !tpircSavaJ"
```
