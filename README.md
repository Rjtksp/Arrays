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

## How to resize an Array in Java ?
```js
public class MyClass {
    public static void main(String args[]) {
      int[] arr = {2,5,7,0,4,6};
      System.out.println("Oirginal array length: " + arr.length);
      
      arr = resizeArray(arr, arr.length*2);
      System.out.println("Modified array length: " + arr.length);
    }
    public static int[] resizeArray(int[] arr, int newSize){
        int[] temp = new int[newSize];
        for(int i=0; i<arr.length; i++){
            temp[i] = arr[i];
        }
        return temp;
    }
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

## How to Reverse an Array in Java ?
```js
public class MyClass {
    public static void main(String args[]) {
      int[] arr = {1,2,3,4,5};
      reverse(arr,0,arr.length-1);
      printArray(arr);
    }
    public static int[] reverse(int[] arr, int start, int end){
        while(start < end){
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
        return arr;
    }
    public static void printArray(int[] arr){
        int n = arr.length;
        for(int i=0; i<n; i++){
            System.out.print(arr[i]+" ");
        }
    }
}
```

## How to check if a given String is a Palindrome ?
```js
public class MyClass {
    public static void main(String args[]) {
      String str = "madam";
      if(isPlaindrome(str)){
          System.out.print("Given string is Palindrome!!");
      }else{
          System.out.print("Given string is not Palindrome!!");
      }
    }
    public static boolean isPlaindrome(String str){
        char[] arr = str.toCharArray();
        int start = 0;
        int end = arr.length - 1;
        while(start < end){
            if(arr[start] != arr[end]){
                return false;
            }
            start++;
            end--;
        }
        return true;
    }
}
```

## Two Sum problem ?
import java.util.*;
public class MyClass {
    public static void main(String args[]) {
      int[] arr = {2,11,5,10,7,8};
      int target = 9;
      int[] res = new int[2];
      HashMap<Integer,Integer> map = new HashMap<>();
      for(int i=0; i<arr.length; i++){
          if(map.containsKey(target - arr[i])){
              res[0] = map.get(target - arr[i]);
              res[1] = i;
          }else{
              map.put(arr[i], i);
          }
      }
      for(int i=0; i<res.length; i++){
          System.out.print(res[i]+" ");
      }
    }
}
