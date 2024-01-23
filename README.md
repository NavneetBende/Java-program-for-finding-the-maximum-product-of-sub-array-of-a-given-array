Maximum product of sub-array in Java
Here, in this page we will discuss the program to find the maximum product of sub-array in java programming language. We are given with an integer array and need to print the value of maximum product that obtained.

maximum product of sub-array in java
Here, in this page we will discuss the two different ways for finding the maximum product sub array, and compare there efficiency.

Method 1 : Naive Approach
Method 2 : Efficient Approach
Method 1 :
In this method we will find the product of all a sub-array and find the product that obtained.

Create a variable say result that will hold the value of maximum product that obtained.
Set, result = arr[0].
Run a loop from index 0 to n,
Create a variable mul = arr[i], that will hold the product of sub-array.
Run a inner loop from index i+1 to n.
Set, result = Math.max(result, mul)
And, mul to mul *= arr[j]
Method 1: Code in Java
Run
import java.io.*;
 
class Main {
    /* Returns the product of max product subarray.*/
    static int maxSubarrayProduct(int arr[])
    {
        // Initializing result
        int result = arr[0];
        int n = arr.length;
 
        for (int i = 0; i < n; i++)
        {
            int mul = arr[i];
            // traversing in current subarray
            for (int j = i + 1; j < n; j++)
            {
                // updating result every time
                // to keep an eye over the
                // maximum product
                result = Math.max(result, mul);
                mul *= arr[j];
            }
            // updating the result for (n-1)th index.
            result = Math.max(result, mul);
        }
        return result;
    }
 
    // Driver Code
    public static void main(String[] args)
    {
        int arr[] = { 10, -20, -30, 0, 70, -80, -20 };
        System.out.println("Maximum Sub array product is " + maxSubarrayProduct(arr));
    }
}
Output
Maximum Sub array product is 112000
Related Pages
Counting the number of even and odd elements in an array

Find all Symmetric pairs in an array

Finding Arrays are disjoint or not

Determine Array is a subset of another array or not

Determine can all numbers of an array be made equal

Method 2:
This is the efficient solution and is also similar to Largest Sum Contiguous Subarray problem which uses Kadane’s algorithm.

Declare three variables say max_so_far, max_ending_here & min_ending_here.
For every index the maximum number ending at that index will be the maximum(arr[i], max_ending_here * arr[i], min_ending_here[i]*arr[i]).
Similarly the minimum number ending here will be the minimum of these 3.
Thus we get the final value for maximum product subarray.
Method 2: Code in Java
Run
import java.io.*;
 
class Main {
    /* Returns the product of max product subarray.*/
    static int maxSubarrayProduct(int arr[], int n){
        // max positive product
        // ending at the current position
        int max_ending_here = arr[0];
 
        // min negative product ending
        // at the current position
        int min_ending_here = arr[0];
 
        // Initialize overall max product
        int max_so_far = arr[0];
    
        for (int i = 1; i < n; i++)
        {
            int temp = max({arr[i], arr[i] * max_ending_here, arr[i] * min_ending_here});
       
            min_ending_here = min({arr[i], arr[i] * max_ending_here, arr[i] * min_ending_here});
            max_ending_here = temp;
            max_so_far = max(max_so_far, max_ending_here);
        }
        return max_so_far;
    }
 
    // Driver Code
    public static void main(String[] args)
    {
        int arr[] = { 10, -20, -30, 0, 70, -80, -20 };
        System.out.println("Maximum Sub array product is " + maxSubarrayProduct(arr));
    }
}
Output
Maximum Sub array product is 112000
