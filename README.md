### Arrays
An array is a collection of items of same data type stored at contiguous memory locations.

### Declaration and Initialization of a One-Dimensional Array
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

### Adding or Updating elements in a One-Dimensional Array
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

### How to print elements of an Array in Java?
```js
public void printArray(int[] arr){
  int n = arr.length;
  for(int i=0; i<n; i++){
    System.out.print(arr[i] + " ");
  }
  System.out.println();
}
```

### How to resize an Array in Java ?
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

### How to find Minimum value in an Array ?
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

### How to move Zeroes to end of an Array?
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

### How to Reverse an Array in Java ?
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

### How to check if a given String is a Palindrome ?
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

### Two Sum problem ?
```js
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
```

### How to merge two sorted arrays in Java?
```js
import java.util.*;
public class MyClass {
    public static void main(String args[]) {
      int[] arr1 = {2,4,5,8};
      int[] arr2 = {3,6,7,9};
      int n = arr1.length;
      int m = arr2.length;
      
      int[] result = merge(arr1,arr2,n,m);
      for(int i=0; i<result.length; i++){
        System.out.print(result[i]+" ");
      }
    }
    public static int[] merge(int[] arr1, int[] arr2, int n, int m){
        int[] result = new int[n+m];
        int i=0;
        int j=0;
        int k=0;
        while(i<n && j<m){
            if(arr1[i] < arr2[j]){
                result[k] = arr1[i];
                i++;
            }else{
                result[k] = arr2[j];
                j++;
            }
            k++;
        }
        while(i<n){
            result[k] = arr1[i];
            i++;
            k++;
        }
        while(j<m){
            result[k] = arr2[j];
            j++;
            k++;
        }
        return result;
    }
}
```

### Maximum Sum Subarray - Kadane's Algorithm
```js
import java.util.*;
public class MyClass {
    public static void main(String args[]) {
      int[] arr = {2,4,-2,5,-12,8,5};
      System.out.print(maxSum(arr));
    }
    public static int maxSum(int[] arr){
        int currentMax = arr[0];
        int maxSoFar = arr[0];
        for(int i=1; i<arr.length; i++){
            currentMax = currentMax + arr[i]; //element become part of given subarray.
            if(currentMax < arr[i]){ 
                currentMax = arr[i]; //element decides to starts its own array.
            }
            if(maxSoFar < currentMax){
                maxSoFar = currentMax;
            }
        }
        return maxSoFar;
    }
}
```

### Find Missing Number in array ?
```js
public class MyClass {
    public static void main(String args[]) {
      int[] arr = {1,2,3,5,6};
      System.out.print(findMissing(arr));
    }
    public static int findMissing(int[] arr){
        int n = arr.length + 1;
        int sum = n*(n+1)/2;
        for(int i=0; i<arr.length; i++){
            sum = sum - arr[i];
        }
        return sum;
    }
}
```

### Squares of a Sorted Array?
```js
import java.util.*;
public class MyClass {
    public static void main(String args[]) {
      int[] arr = {-4,-1,0,3,10};
      int[] res = sortedSquare(arr);
      for(int i=0; i<res.length; i++){
          System.out.print(res[i]+" ");
      }
    }
    public static int[] sortedSquare(int[] arr){
        int n = arr.length;
        int[] result = new int[n];
        int i=0;
        int j=n-1;
        for(int k=n-1; k>=0; k--){
            if(Math.abs(arr[i]) > Math.abs(arr[j])){
                result[k] = arr[i] * arr[i];
                i++;
            }else{
                result[k] = arr[j] * arr[j];
                j--;
            }
        }
        return result;
    }
}
```

### First Non-Repeating Character in a String?
```js
import java.util.*;
public class MyClass {
    public static void main(String args[]) {
      String str = "racecars";
      System.out.print(firstNonRep(str));
    }
    public static int firstNonRep(String str){
        HashMap<Character,Integer> map = new HashMap<>();
        char[] chars = str.toCharArray();
        for(char ch : chars){
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }
        for(int i=0; i<chars.length; i++){
            char ch = chars[i];
            if(map.get(ch) == 1){
                return i;
            }
        }
        return -1;
    }
}
```

### Remove Vowels from a String?
```js
import java.util.*;
public class MyClass {
    public static void main(String args[]) {
      String str = "ice cream";
      System.out.print(removeVowels(str));
    }
    public static String removeVowels(String str){
        Set<Character> vowels = Set.of('a','e','i','o','u');
        StringBuilder sb = new StringBuilder();
        
        char[] charArray = str.toCharArray();
        for(Character ch : charArray){
            if(!vowels.contains(ch)){
                sb.append(ch);
            }
        }
        return sb.toString();
    }
}
```

### Three Sum problem? (Triplets)
```js
import java.util.*;
public class MyClass {
    public static void main(String args[]) {
      int[] arr = {1,2,0,4,3,7};
      int target = 6;
      threeSum(arr, target);
    }
    public static void threeSum(int[] arr, int target){
        Arrays.sort(arr); // nlogn
        for(int i=0; i<arr.length-2; i++){ // O(n)
            int j=i+1;
            int k=arr.length-1;
            while(j<k){ // O(n)
                int sum = arr[i] + arr[j] + arr[k];
                if(sum == target){
                    System.out.println(arr[i] + "," + arr[j] + "," + arr[k]);
                    j++;
                    k--;
                }else if(sum > target){
                    k--;
                }else{
                    j++;
                }
            }
        }
    }
}
```

### Find Triplets (Hashing) ?
```js
import java.util.*;
public class MyClass {
	static boolean find3Numbers(int A[], int arr_size, int sum){
		for (int i = 0; i < arr_size - 2; i++) {
			HashSet<Integer> s = new HashSet<Integer>();
			int curr_sum = sum - A[i];
			for (int j = i + 1; j < arr_size; j++)
			{
				if (s.contains(curr_sum - A[j]))
				{
					System.out.printf("Triplet is %d, %d, %d", A[i],
									A[j], curr_sum - A[j]);
					return true;
				}
				s.add(A[j]);
			}
		}
		return false;
	}

	public static void main(String[] args) {
		int A[] = {-3, 1, 4, -5, -4, 2, 3};
		int sum = 0;
		int arr_size = A.length;

		find3Numbers(A, arr_size, sum);
	}
}

```

### Merge two sorted arrays with O(1) extra space?
```js
import java.io.*;
import java.util.Arrays;
import java.util.Collections;

public class MyClass {
    public static void merge(int[] arr1, int[] arr2, int n, int m){
    	int i = 0;
    	// While loop till last element of array 1 is greater than first element of array 2
    	while (arr1[n - 1] > arr2[0]) {
    		if (arr1[i] > arr2[0]) {
    			int temp = arr1[i];
    			arr1[i] = arr2[0];
    			arr2[0] = temp;
    			Arrays.sort(arr2);
    		}
    		i++;
    	}
    }
    public static void main(String[] args){
        int arr1[] = { 1, 5, 9, 10, 15, 20 };
        int arr2[] = { 2, 3, 8, 13 };
    	merge(arr1,arr2,arr1.length, arr2.length);
    	System.out.println(Arrays.toString(arr1));
    	System.out.println(Arrays.toString(arr2));
    }
}
```

### Sort an array according to the order defined by another array?
```js
import java.io.*;
import java.util.Arrays;
import java.util.HashMap;

public class MyClass {
    static void sortA1ByA2(int arr1[], int n, int arr2[], int m) {
    	HashMap<Integer, Integer> mp = new HashMap<>();
    	int[] ans = new int[n];
    	int ind = 0;
    	for (int i = 0; i < n; i++) {
    		if (!mp.containsKey(arr1[i])) {
    		    mp.put(arr1[i],1);
    		}else {
    		    mp.put(arr1[i],mp.get(arr1[i])+1);
    		}
    	}
    	for (int i = 0; i < m; i++) {    		
    		if (mp.containsKey(arr2[i])) {
    			for (int j = 1; j <= mp.get(arr2[i]); j++)
    				ans[ind++] = arr2[i];
    		}
    		mp.remove(arr2[i]);
    	}
    
    	// store the remaining elements of A1 in ans array
    	for (HashMap.Entry<Integer,Integer> it : mp.entrySet()) {
    		// it.second = frequency of remaining elements
    		for (int j = 1; j <= it.getValue(); j++) {
    			ans[ind++] = it.getKey();
    		}
    	}
    	
    	System.out.println("Sorted array is ");
	for (int i = 0; i < n; i++) {
    		System.out.print(ans[i] + " ");
	}
    }
	public static void main(String[] args) {
		int A1[] = { 2, 1, 2, 5, 7, 1, 9, 3, 6, 8, 8 };
		int A2[] = { 2, 1, 8, 3 };
		int n = A1.length;
		int m = A2.length;
	
		sortA1ByA2(A1, n, A2, m);
    }
}
```

### Sort an array of 0’s, 1’s, and 2’s (Dutch National Flag Problem)?
```js
import java.util.*;
public class MyClass {
	public static void main(String[] args) {
		int arr[] = {1,2,0,1,1,2,2,0,0};
		int i=0;
		int j=0;
		int k=arr.length-1;
		while(i<=k){
		  if(arr[i] == 0){
		      swap(arr,i,j);
		      i++;
		      j++;
		  }else if(arr[i] == 1){
		      i++;
		  }else if(arr[i] == 2){
		      swap(arr,i,k);
		      k--;
		  }
		}
		for(int m=0; m<arr.length; m++){
		    System.out.print(arr[m]+" ");
		}
	}
	public static void swap(int[] arr, int i, int j){
	    int temp = arr[i];
	    arr[i] = arr[j];
	    arr[j] = temp;
	}
}

```

### Remove Even Integers from an Array?
```js
import java.util.*;
public class MyClass {
	public static void main(String[] args) {
		int arr[] = {3, 2, 4, 7, 10, 6, 5};
		int[] result = removeEven(arr);
		for(int i=0; i<result.length; i++){
		    System.out.print(result[i]+" ");
		}
		
	}
	public static int[] removeEven(int[] arr){
	    int odd = 0;
	    for(int i=0; i<arr.length; i++){
	        if(arr[i] % 2 != 0){
	            odd++;
	        }
	    }
	    int[] res = new int[odd];
	    int index = 0;
	    for(int i=0; i<arr.length; i++){
	        if(arr[i] % 2 != 0){
	            res[index] = arr[i];
	            index++;
	        }
	    }
	    return res;
	}
}
```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```

### 
```js

```
