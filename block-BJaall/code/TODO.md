## Implement Sorting Algorithms

We learned about different sorting algorithms in the previous block. Implement the sorting algorithms you learned in the videos as a function.

1. Write down the steps to perform for different sorting algorithms i.e bubble, insertion and selection. Write in your own words. After writing the algorithm take an example of an array and draw the diagram for each step for different algorithm.

Example:

#### Bubble Sort

step-1: We will compare the first item with the second. If the first item is bigger than the second item we will swap them so that the bigger one stays in the second position.

step-2: And then compare second with third item. If second item is bigger than the third, we swap them. otherwise, they stayed in their position. Hence, the biggest among first three is in the third position.

step-3: We keep doing it. Until we hit the last element of the array. In that way we bubble up the biggest item of the array to the right most position of the array.

step-4: Now we will repeat the step 1, 2 and 3 but we will keep in mind not to touch the last element.

![Bubble Sort Example](./bubble.png)

<!-- You answer -->

Insertion sort
step1:-In insertion sort we start from item at index 0 .as we move in future we will have two portions one on left is sorted array and 0one on right is unsorted array.

step 2:- now when we are on index 1 we compare it to items on left and if its not in position then we swap it to the correct position.

step3 :- now when we are on index 2 then we compare it with all 2 items on left and swap it if necessary.

step 4 :- in this way we can sort whole array.

selection sort
step 1:- in seelection sort we have two pointers one current item and one current minimum.

step2:- now we start by marking index 0 item as current minimum and current item.now we move current item to next item on right and if it is smaller than current minimum move pointer to it and repeat step until curretn item pointer is on last item .

step3:- now we have to swap item on left with current minimum.once swapped now we have two portions on left sorted and on right unsorted.

step4:- now we have to put both pointers on 2nd item and repeat all steps untill array is sorted.

2. Create a function named `bubbleSort` that accepts an array of numbers and returns the array with sorted values. The elements should be in ascending order. Use the bubble sorting algorithms. After writing the function test it with an array and check if you are getting the right output.

```js
function bubbleSort() {
  // your code
  for (let i = 1; i < arr.length; i++) {
    for (let j = 0; j < arr.length - 1; j++) {
      if (arr[i] < arr[j]) {
        let newVar = arr[j];
        arr[j] = arr[i];
        arr[i] = newVar;
      }
    }
  }
}
```

3. Create a function named `selectionSort` that accepts an array of numbers and returns the array with sorted values. The elements should be in ascending order. Use the selection sorting algorithms. After writing the function test it with an array and check if you are getting the right output.

```js
function selectionSort() {
  // your code
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < i; j++) {
      if (arr[i] < arr[j]) {
        let newVar = arr[i];
        arr[i] = arr[j];
        arr[j] = newVar;
      }
    }
  }

  return arr;
}
```

4. Create a function named `insertionSort` that accepts an array of numbers and returns the array with sorted values. The elements should be in ascending order. Use the insertion sorting algorithms. After writing the function test it with an array and check if you are getting the right output.

```js
function insertionSort() {
  // your code
  for (let i = 0; i < arr.length; i++) {
    let mini = i;
    for (let j = i + 1; j < arr.length + 1; j++) {
      if (arr[j] < arr[mini]) {
        mini = j;
      }
    }
    let newVar = arr[i];
    arr[i] = arr[mini];
    arr[mini] = newVar;
  }

  return arr;
}
```

5. After writing all the sorting algorithm check the output with the array given below and make sure you are getting the right output.

```js
let values = [76, 34, 12, 32, 4, 2, 123, 5667, 8, 1, 3];
```
