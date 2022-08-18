## Arrays
An array is a collection of items of same data type stored at contiguous memory locations.

## Declaration and Initialization of a One-Dimensional Array
Array can declared and initialized in same line via syntax :
```js
  dataType[] arrName = new dataType[size];
  dataType arrName[] = new dataType[size];
  dataType[] arrName = {};
  
  For Example:
  int[] arr = new int[5];
  int arr[] = new int[5];
  int[] arr = {1,2,3,4,5};
```

## Adding or Updating elements in a One-Dimensional Array
```js
public void arrayDemo(){
  int[] arr = new int[5];
  arr[0] = 1;
  arr[1] = 2;
  arr[2] = 3;
  arr[3] = 4;
  arr[2] = 6; // here we update the value of index 2.
  arr[4] = 5;
  arr[5] = 7; // here it will thrown an error index out of bound. Because size of array is 5 and trying to add 6th element. 
}
o/p :  1 2 6 4 5 and an error Array index out of bound.
```
