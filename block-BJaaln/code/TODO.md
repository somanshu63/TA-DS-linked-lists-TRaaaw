## Implement Sorting Algorithms

1. Write down the steps to perform for different sorting algorithms i.e merge and quick sort. Write the steps in your own words. After writing the algorithm take an example of an array and draw the diagram for each step for different algorithm.

Example:

#### Bubble Sort

step-1: We will compare the first item with the second. If the first item is bigger than the second item we will swap them so that the bigger one stays in the second position.

step-2: And then compare second with third item. If second item is bigger than the third, we swap them. otherwise, they stayed in their position. Hence, the biggest among first three is in the third position.

step-3: We keep doing it. Until we hit the last element of the array. In that way we bubble up the biggest item of the array to the right most position of the array.

step-4: Now we will repeat the step 1, 2 and 3 but we will keep in mind not to touch the last element.

step-5: After repeating all the above steps you will get a sorted array

![Bubble Sort Example](./bubble.png)

<!-- You answer -->

merge sort
step1:- in this step first we have to divide array into half.once done then we have to divide each array into half again.

step2:- this we have to continue till we get each item in the different array.

step3:- now we have to start merging two element into single array but in arranged way.

step4:- we have to continue this step till we will get one sorted array.

2. Create a function named `mergeSort` that accepts an array of numbers and returns the array with sorted values. The elements should be in ascending order. Use the bubble sorting algorithms. After writing the function test it with an array and check if you are getting the right output.

```js
// your code
function merge(a, b) {
  const c = [];

  while (a.length && b.length) {
    c.push(a[0] > b[0] ? b.shift() : a.shift());
  }

  while (a.length) {
    c.push(a.shift());
  }
  while (b.length) {
    c.push(b.shift());
  }

  return c;
}

function mergeSort(a) {
  if (a.length < 2) return a;
  const middle = Math.floor(a.length / 2);
  const a_l = a.slice(0, middle);
  const a_r = a.slice(middle, a.length);
  const sorted_l = mergeSort(a_l);
  const sorted_r = mergeSort(a_r);
  return merge(sorted_l, sorted_r);
}
```

3. Create a function named `quickSort` that accepts an array of numbers and returns the array with sorted values. The elements should be in ascending order. Use the selection sorting algorithms. After writing the function test it with an array and check if you are getting the right output.

```js
function quickSort(originalList) {
  const list = [...originalList];

  if (list.length < 2) {
    return list;
  }

  const pivot = list[0];

  const smaller = list.filter((item) => item < pivot);
  const bigger = list.filter((item) => item > pivot);

  return [...quickSort(smaller), pivot, ...quickSort(bigger)];
}
```

4. After writing all the sorting algorithm check the output with the array given below and make sure you are getting the right output.

```js
let values = [76, 34, 12, 32, 4, 2, 123, 5667, 8, 1, 3];
```
