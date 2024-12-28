# Problem Solving Tools

## Using language sorting libraries

Sorting is a common operation. Many problems require sorting as part of solving it. Instead of writing a sort function themselves, while solving a problem, programmers usually use the sorting library functions provided by their language. In JavaScript, for example, the following function call sorts an integer array in increasing order.

```js
const arr = [10, 4, 8, 3, 9, 7, 1];
arr.sort();

console.log(arr);
```

### Using custom comparison functions

For integers, the sorting is obvious, but what about objects? How to sort an array of objects? Every sorting algorithm sorts elements by comparing them. For sorting objects, programmers have to pass the _comparison function_ to the sort library function.

```js
const arr = [{ marks: 10, name: "John"},
             { marks: 4, name: "Charles"},
             { marks: 8, name: "Mike"}, 
             { marks: 3, name: "Hans"}, 
             { marks: 9, name: "Adam"}, 
             { marks: 7, name: "Sam"},
             { marks: 1, name: "Ann"}];

arr.sort((a, b) => a.marks - b.marks);

console.log(arr);
```

In the preceding example, the array of a few students with their marks is sorted in increasing order. The custom comparison function passed to the `sort` function call specifies that two objects (`a` and `b`) shall be compared based on their `marks` property.

The comparison function can be used for integers too. The JavaScript sort function [documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) documents how to write the comparison function. Programmers have to check out the documentation of their own language sort function.
