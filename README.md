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

## How to print elements of an Array in Java?
```js
public void printArray(int[] arr){
  int n = arr.length;
  for(int i=0; i<n; i++){
    System.out.print(arr[i] + " ");
  }
  System.out.println();
}
```

## How to find Minimum value in an Array ?
```js
import java.util.Scanner;
public class MyClass {
    public static void main(String args[]) {
    Scanner sc = new Scanner(System.in);
    int size = sc.nextInt();
    int[] arr = new int[size];
    for (int i=0; i<size; i++){
      arr[i] = sc.nextInt();
    }
    // int[] arr = {2,5,9,7,10,1,6};
    System.out.print(findMinimum(arr));
    }
    public static int findMinimum(int[] arr){
        int min = arr[0];
        for(int i=1; i<arr.length; i++){
            if(arr[i] < min){
                min = arr[i];
            }
        }
        return min;
    }
}
```

## How to move Zeroes to end of an Array?
```js
public class MyClass {
    public static void main(String args[]) {
      int[] arr = {2,0,9,7,0,1};
      moveZero(arr);
      printArray(arr);
    }
    public static int[] moveZero(int[] arr){
        int j = 0; // j is responsible for zero's value
        for(int i=0; i<arr.length; i++){ // i is responsible for non zero's value
            if(arr[i] != 0 && arr[j] == 0){
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
            if(arr[j] != 0){ // if j value is not zero then j stay at same index otherwise increment by 1.
                j++;
            }
        }
        return arr;
    }
    public static void printArray(int[] arr){
        int n = arr.length;
        for(int i=0; i<n; i++){
            System.out.print(arr[i] + " ");
        }
        System.out.println();
    }
}
```
