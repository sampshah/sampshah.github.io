---
layout: post
title: Competitive Programming Notes | Tech
comments: true
---

## Python general

- Useful for strings
```python
x = ord('A') # ASCII value from character
y = chr(x)   # Character from ASCII value
a = 'abc'.isalpha()   # returns boolean if it is only alphabet
b = 'abc12'.isalnum() # returns boolean if it is only alpha and nums
c = '123'.isdigit()   # returns boolean if it is only digits
letters.sort(key = lambda x: x.split()[1]) # sort lexicographically
```

## Cpp general

- Char to ascii and vice versa
```cpp
int x = int('c');  // ascii value of characters
char c = (char)x;  // character from ascii
```


#### Dynamic Programming
These must have:  
- Overlapping sub-problems: Same problems seen multiple times
- Optimal Sub-Structure: Optimal solution to sub-problem is part of real solution

- Examples:  
    - Coin Change Problem
    - KnackSack Problem
    - Longest palindromic substring


## Sorting Algorithms  

- Bubble sort  

C++

 ```cpp
void bubble_sort( int A[ ], int n ) {
    int temp;
    for(int k = 0; k< n-1; k++) {
        // (n-k-1) is for ignoring comparisons of elements which have already been compared in earlier iterations

        for(int i = 0; i < n-k-1; i++) {
            if(A[ i ] > A[ i+1] ) {
                // here swapping of positions is being done.
                temp = A[ i ];
                A[ i ] = A[ i+1 ];
                A[ i + 1] = temp;
            }
        }
    }
}
 ```  

Python: 

 ```python
def bubbleSort(arr): 
    n = len(arr) 
  
    # Traverse through all array elements 
    for i in range(n-1): 
    # range(n) also work but outer loop will repeat one time more than needed. 
  
        # Last i elements are already in place 
        for j in range(0, n-i-1): 
  
            # traverse the array from 0 to n-i-1 
            # Swap if the element found is greater 
            # than the next element 
            if arr[j] > arr[j+1] : 
                arr[j], arr[j+1] = arr[j+1], arr[j] 

 ```




- Insertion sort  

C++

```cpp
void insertion_sort(int A[], int n) {
    for (int i = 0; i < n; i++) {
        /*storing current element whose left side is checked for its 
                 correct position .*/

        int temp = A[i];
        int j = i;

        /* check whether the adjacent element in left side is greater or
             less than the current element. */

        while (j > 0 && temp < A[j - 1]) {

            // moving the left side element to one position forward.
            A[j] = A[j - 1];
            j = j - 1;

        }
        // moving current element to its  correct position.
        A[j] = temp;
    }
}

```
Python

```python
def insertionSort(arr): 
  
    # Traverse through 1 to len(arr) 
    for i in range(1, len(arr)): 
  
        key = arr[i] 
  
        # Move elements of arr[0..i-1], that are 
        # greater than key, to one position ahead 
        # of their current position 
        j = i-1
        while j >=0 and key < arr[j] : 
                arr[j+1] = arr[j] 
                j -= 1
        arr[j+1] = key 
```

- Merge Sort

Cpp   

```cpp
void merge(int A[], int start, int mid, int end) {
    //stores the starting position of both parts in temporary variables.
    int p = start, q = mid + 1;

    int Arr[end - start + 1], k = 0;

    for (int i = start; i <= end; i++) {
        if (p > mid) //checks if first part comes to an end or not .
            Arr[k++] = A[q++];

        else if (q > end) //checks if second part comes to an end or not
            Arr[k++] = A[p++];

        else if (A[p] < A[q]) //checks which part has smaller element.
            Arr[k++] = A[p++];

        else
            Arr[k++] = A[q++];
    }
    for (int p = 0; p < k; p++) {
        /* Now the real array has elements in sorted manner including both 
             parts.*/
        A[start++] = Arr[p];
    }
}

void merge_sort(int A[], int start, int end) {
    if (start < end) {
        int mid = (start + end) / 2; // defines the current array in 2 parts .
        merge_sort(A, start, mid); // sort the 1st part of array .
        merge_sort(A, mid + 1, end); // sort the 2nd part of array.

        // merge the both parts by comparing elements of both the parts.
        merge(A, start, mid, end);
    }
}

```

Python  

```python
def mergeSort(arr): 
    if len(arr) >1: 
        mid = len(arr)//2 # Finding the mid of the array 
        L = arr[:mid] # Dividing the array elements  
        R = arr[mid:] # into 2 halves 
  
        mergeSort(L) # Sorting the first half 
        mergeSort(R) # Sorting the second half 
  
        i = j = k = 0
          
        # Copy data to temp arrays L[] and R[] 
        while i < len(L) and j < len(R): 
            if L[i] < R[j]: 
                arr[k] = L[i] 
                i+= 1
            else: 
                arr[k] = R[j] 
                j+= 1
            k+= 1
          
        # Checking if any element was left 
        while i < len(L): 
            arr[k] = L[i] 
            i+= 1
            k+= 1
          
        while j < len(R): 
            arr[k] = R[j] 
            j+= 1
            k+= 1
```

- Quick Sort  

C++  

```cpp
int partition(int A[], int start, int end) {
    int i = start + 1;
    int piv = A[start]; //make the first element as pivot element.
    for (int j = start + 1; j <= end; j++) {
        /*rearrange the array by putting elements which are less than pivot
           on one side and which are greater that on other. */

        if (A[j] < piv) {
            swap(A[i], A[j]);
            i += 1;
        }
    }
    swap(A[start], A[i - 1]); //put the pivot element in its proper place.
    return i - 1; //return the position of the pivot
}
void quick_sort ( int A[ ] ,int start , int end ) {
   if( start < end ) {
        //stores the position of pivot element
         int piv_pos = partition (A,start , end ) ;     
         quick_sort (A,start , piv_pos -1);    //sorts the left side of pivot.
         quick_sort ( A,piv_pos +1 , end) ; //sorts the right side of pivot.
   }
}

```

Python 

```python
def partition(arr,low,high): 
    i = ( low-1 )         # index of smaller element 
    pivot = arr[high]     # pivot 
  
    for j in range(low , high): 
  
        # If current element is smaller than or 
        # equal to pivot 
        if   arr[j] <= pivot: 
          
            # increment index of smaller element 
            i = i+1 
            arr[i],arr[j] = arr[j],arr[i] 
  
    arr[i+1],arr[high] = arr[high],arr[i+1] 
    return ( i+1 ) 
  
# The main function that implements QuickSort 
# arr[] --> Array to be sorted, 
# low  --> Starting index, 
# high  --> Ending index 
  
# Function to do Quick sort 
def quickSort(arr,low,high): 
    if low < high: 
  
        # pi is partitioning index, arr[p] is now 
        # at right place 
        pi = partition(arr,low,high) 
  
        # Separately sort elements before 
        # partition and after partition 
        quickSort(arr, low, pi-1) 
        quickSort(arr, pi+1, high) 
```


References:  
- https://rikenshah.github.io/articles/codemonk-part1/
- geeksforgeeks.org


... to be continued
