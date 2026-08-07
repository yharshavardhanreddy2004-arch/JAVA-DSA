1.Sum Triangle from Array.
import java.util.*;

public class SumTriangle {

    // Function to print the sum triangle
    static void printSumTriangle(int[] arr) {
        // Base case
        if (arr.length < 1)
            return;

        // If only one element, print it
        if (arr.length == 1) {
            System.out.println(Arrays.toString(arr));
            return;
        }

        // Create a new array of size n-1
        int[] temp = new int[arr.length - 1];

        // Fill the new array with adjacent sums
        for (int i = 0; i < arr.length - 1; i++) {
            temp[i] = arr[i] + arr[i + 1];
        }

        // Recursive call
        printSumTriangle(temp);

        // Print current array
        System.out.println(Arrays.toString(arr));
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};

        printSumTriangle(arr);
    }
}

OUTPUT:
[48]
[20, 28]
[8, 12, 16]
[3, 5, 7, 9]
[1, 2, 3, 4, 5]

2.Maximum and Minimum value in an array.
public class MinMaxRecursive {

    static int min;
    static int max;

    static void findMinMax(int[] arr, int index) {
        // Base case
        if (index == arr.length)
            return;

        // Update minimum
        if (arr[index] < min)
            min = arr[index];

        // Update maximum
        if (arr[index] > max)
            max = arr[index];

        // Recursive call
        findMinMax(arr, index + 1);
    }

    public static void main(String[] args) {
        int[] arr = {3, 5, 1, 8, 2, 9, -4, 7};

        min = arr[0];
        max = arr[0];

        findMinMax(arr, 0);

        System.out.println("Minimum: " + min);
        System.out.println("Maximum: " + max);
    }
}
OUTPUT:
Minimum: -4
Maximum: 9

3.Binary Search using recursion.
public class BinarySearchRecursive {

    static int binarySearch(int[] nums, int left, int right, int target) {
        // Base case
        if (left > right)
            return -1;

        int mid = left + (right - left) / 2;

        if (nums[mid] == target)
            return mid;

        if (target < nums[mid])
            return binarySearch(nums, left, mid - 1, target);

        return binarySearch(nums, mid + 1, right, target);
    }

    public static void main(String[] args) {
        int[] nums = {-1, 0, 3, 5, 9, 12};
        int target = 9;

        int result = binarySearch(nums, 0, nums.length - 1, target);

        System.out.println("Index: " + result);
    }
}

OUTPUT:
Index: 4

4.First Uppercase Letter in a String.
public class FirstUppercase {

    static char firstUppercase(String str, int index) {
        // Base case
        if (index == str.length())
            return '\0';

        // Check if current character is uppercase
        if (Character.isUpperCase(str.charAt(index)))
            return str.charAt(index);

        // Recursive call
        return firstUppercase(str, index + 1);
    }

    public static void main(String[] args) {
        String str = "geeksforGeeks";

        char result = firstUppercase(str, 0);

        if (result == '\0')
            System.out.println("No uppercase letter found.");
        else
            System.out.println("First uppercase letter: " + result);
    }
}
output:
First uppercase letter: G

5.Reverse String.
public class ReverseStringRecursive {

    static void reverse(char[] s, int left, int right) {
        // Base case
        if (left >= right)
            return;

        // Swap characters
        char temp = s[left];
        s[left] = s[right];
        s[right] = temp;

        // Recursive call
        reverse(s, left + 1, right - 1);
    }

    public static void main(String[] args) {
        char[] s = {'h', 'e', 'l', 'l', 'o'};

        reverse(s, 0, s.length - 1);

        System.out.println(new String(s));
    }
}
output:
olleh

6.Print 1 To N Without Loop.
public class Solution {

    static void printNos(int n) {
        // Base case
        if (n == 0)
            return;

        // Recursive call
        printNos(n - 1);

        // Print current number
        System.out.print(n + " ");
    }

    public static void main(String[] args) {
        int n = 5;
        printNos(n);
    }
}
output:
1 2 3 4 5 

7.Fibonacci Number.
public class FibonacciRecursive {

    static int fib(int n) {
        // Base cases
        if (n == 0)
            return 0;
        if (n == 1)
            return 1;

        // Recursive call
        return fib(n - 1) + fib(n - 2);
    }

    public static void main(String[] args) {
        int n = 6;

        System.out.println(fib(n));
    }
}
output:
8

8.Special Fibonacci 
import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int t = sc.nextInt();

        while (t-- > 0) {
            long n = sc.nextLong();

            if (n % 3 == 0)
                System.out.println(0);
            else
                System.out.println(1);
        }

        sc.close();
    }
}
output:
0
1
1
0
1
9.Length of string using Recursion.
public class StringLengthRecursive {

    static int findLength(String str, int index) {
        // Base case
        if (index == str.length())
            return 0;

        // Recursive call
        return 1 + findLength(str, index + 1);
    }

    public static void main(String[] args) {
        String str = "GeeksForGeeks";

        int length = findLength(str, 0);

        System.out.println("Length of string: " + length);
    }
}
output:
Length of string: 13.

10.Geek-onacci Number.
import java.util.*;

public class Main {

    static int geekonacci(int n, int a, int b, int c) {
        // Base cases
        if (n == 1)
            return a;

        if (n == 2)
            return b;

        if (n == 3)
            return c;

        // Recursive call
        return geekonacci(n - 1, a, b, c)
             + geekonacci(n - 2, a, b, c)
             + geekonacci(n - 3, a, b, c);
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int t = sc.nextInt();

        while (t-- > 0) {
            int n = sc.nextInt();
            int a = sc.nextInt();
            int b = sc.nextInt();
            int c = sc.nextInt();

            System.out.println(geekonacci(n, a, b, c));
        }

        sc.close();
    }
}
output:
11

11.Recursive Bubble Sort.
import java.util.*;

public class RecursiveBubbleSort {

    static void bubbleSort(int[] arr, int n) {
        // Base case
        if (n == 1)
            return;

        // One pass of bubble sort
        for (int i = 0; i < n - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                // Swap
                int temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }

        // Recursive call for remaining elements
        bubbleSort(arr, n - 1);
    }

    public static void main(String[] args) {

        int[] arr = {64, 34, 25, 12, 22, 11, 90};

        bubbleSort(arr, arr.length);

        System.out.println("Sorted Array:");
        System.out.println(Arrays.toString(arr));
    }
}
output:
Sorted Array:
[11, 12, 22, 25, 34, 64, 90]

12.Recursive Insertion Sort 

import java.util.*;

public class RecursiveInsertionSort {

    static void insertionSort(int[] arr, int n) {

        // Base case
        if (n <= 1)
            return;

        // Sort first n-1 elements
        insertionSort(arr, n - 1);

        // Insert last element at its correct position
        int key = arr[n - 1];
        int j = n - 2;

        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }

        arr[j + 1] = key;
    }

    public static void main(String[] args) {

        int[] arr = {12, 11, 13, 5, 6};

        insertionSort(arr, arr.length);

        System.out.println("Sorted Array:");
        System.out.println(Arrays.toString(arr));
    }
}
output:
Sorted Array:
[5, 6, 11, 12, 13]

13.Sum of digit of a number using Recursion.

import java.util.*;

public class SumOfDigitsRecursive {

    static int sumOfDigits(int n) {
        // Base case
        if (n == 0)
            return 0;

        // Recursive call
        return (n % 10) + sumOfDigits(n / 10);
    }

    public static void main(String[] args) {

        int n = 12345;

        int result = sumOfDigits(n);

        System.out.println("Sum of digits: " + result);
    }
}
output:
Sum of digits: 15

14.Product of two numbers using Recursion.
import java.util.*;

public class ProductUsingRecursion {

    static int product(int a, int b) {
        // Base case
        if (b == 0)
            return 0;

        // Handle negative multiplier
        if (b < 0)
            return -product(a, -b);

        // Recursive addition
        return a + product(a, b - 1);
    }

    public static void main(String[] args) {

        int a = 5;
        int b = 4;

        int result = product(a, b);

        System.out.println("Product: " + result);
    }
}
output:
Product: 20

15.Check Prime or not 
import java.util.*;

public class CheckPrimeRecursive {

    static boolean isPrime(int n, int i) {

        // Base cases
        if (n <= 1)
            return false;

        if (i == n)
            return true;

        // If divisible by i, not prime
        if (n % i == 0)
            return false;

        // Recursive call
        return isPrime(n, i + 1);
    }

    public static void main(String[] args) {

        int n = 29;

        if (isPrime(n, 2))
            System.out.println(n + " is Prime");
        else
            System.out.println(n + " is Not Prime");
    }
}
output:
29 is Prime.

16.Sum of Natural numbers using Recursion.
import java.util.*;

public class SumNaturalNumbersRecursive {

    static int sum(int n) {
        // Base case
        if (n == 0)
            return 0;

        // Recursive call
        return n + sum(n - 1);
    }

    public static void main(String[] args) {

        int n = 10;

        int result = sum(n);

        System.out.println("Sum of natural numbers: " + result);
    }
}
output:
Sum of natural numbers: 55

17.Power of Two.
public class PowerOfTwoRecursive {

    static boolean isPowerOfTwo(int n) {

        // Base case
        if (n == 1)
            return true;

        // Check invalid cases
        if (n <= 0 || n % 2 != 0)
            return false;

        return isPowerOfTwo(n / 2);
    }

    public static void main(String[] args) {

        int n = 16;

        if (isPowerOfTwo(n))
            System.out.println(n + " is a power of two");
        else
            System.out.println(n + " is not a power of two");
    }
}
output:
16 is a power of two

18.Power of Three
class Solution {
    public boolean isPowerOfThree(int n) {

        // Base case
        if (n == 1)
            return true;

        // Invalid cases
        if (n <= 0 || n % 3 != 0)
            return false;

        // Recursive call
        return isPowerOfThree(n / 3);
    }
}
output:
27 is a power of three

19.Power of Four
public class PowerOfFourRecursive {

    static boolean isPowerOfFour(int n) {

        // Base case
        if (n == 1)
            return true;

        // Check invalid cases
        if (n <= 0 || n % 4 != 0)
            return false;

        return isPowerOfFour(n / 4);
    }

    public static void main(String[] args) {

        int n = 64;

        if (isPowerOfFour(n))
            System.out.println(n + " is a power of four");
        else
            System.out.println(n + " is not a power of four");
    }
}
output:
64 is a power of four

20.Write a recursive function that returns the factorial of a number.

program:
import java.util.Scanner;

public class Factorial {

    static int factorial(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }

        return n * factorial(n - 1);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int n = sc.nextInt();

        System.out.println("Factorial = " + factorial(n));

        sc.close();
    }
}

output:

Enter a number: 5
Factorial = 120

21. Write a recursive function to check whether an array is sorted or not.

program:
import java.util.Scanner;

public class SortedArray {

    static boolean isSorted(int[] arr, int index) {

        // Base case
        if (index == arr.length - 1) {
            return true;
        }

        // If current element is greater than next element
        if (arr[index] > arr[index + 1]) {
            return false;
        }

        // Recursive call
        return isSorted(arr, index + 1);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter size: ");
        int n = sc.nextInt();

        int[] arr = new int[n];

        System.out.println("Enter array elements:");
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        if (isSorted(arr, 0)) {
            System.out.println("Array is sorted");
        } else {
            System.out.println("Array is not sorted");
        }

        sc.close();
    }
}

output:

5
1 2 3 4 5

Array is sorted

22.Number of Steps to Reduce a Number to Zero.

program:
import java.util.Scanner;

public class NumberOfSteps {

    static int numberOfSteps(int num) {
        if (num == 0) {
            return 0;
        }

        if (num % 2 == 0) {
            return 1 + numberOfSteps(num / 2);
        } else {
            return 1 + numberOfSteps(num - 1);
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = sc.nextInt();

        System.out.println("Number of steps = " + numberOfSteps(num));

        sc.close();
    }
}

output:

Enter a number: 14
Number of steps = 6
14 → 7 → 6 → 3 → 2 → 1 → 0

23. Check for balanced paranthesis using recursion without stack.

program:
import java.util.Scanner;

public class BalancedParentheses {

    static boolean isBalanced(String str, int index, int count) {

        // If count becomes negative, closing parenthesis has no match
        if (count < 0) {
            return false;
        }

        // End of string
        if (index == str.length()) {
            return count == 0;
        }

        char ch = str.charAt(index);

        if (ch == '(') {
            count++;
        } else if (ch == ')') {
            count--;
        }

        return isBalanced(str, index + 1, count);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter parentheses: ");
        String str = sc.nextLine();

        if (isBalanced(str, 0, 0)) {
            System.out.println("Balanced");
        } else {
            System.out.println("Not Balanced");
        }

        sc.close();
    }
}

output:

Enter parentheses: {{{}}}
Balanced

24. Remove consecutive duplicate characters from a string.

program:
import java.util.Scanner;

public class RemoveDuplicates {

    static String removeDuplicates(String str, int index) {

        // Base case
        if (index == str.length() - 1) {
            return str.substring(index);
        }

        // If current character equals next character
        if (str.charAt(index) == str.charAt(index + 1)) {
            return removeDuplicates(str, index + 1);
        }

        return str.charAt(index) + removeDuplicates(str, index + 1);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String str = sc.nextLine();

        if (str.length() == 0) {
            System.out.println("Output: ");
        } else {
            System.out.println("Output: " + removeDuplicates(str, 0));
        }

        sc.close();
    }
}

output:

Enter a string: TThaanuushh
Output: Thanush

25. Print all possible palindromic partitions of a string.

program:
import java.util.Scanner;

public class PalindromicPartitions {

    static boolean isPalindrome(String str, int start, int end) {
        if (start >= end) {
            return true;
        }

        if (str.charAt(start) != str.charAt(end)) {
            return false;
        }

        return isPalindrome(str, start + 1, end - 1);
    }

    static void printPartitions(String str, int start, String result) {

        // Base case
        if (start == str.length()) {
            System.out.println(result);
            return;
        }

        // Try every possible substring
        for (int end = start; end < str.length(); end++) {

            if (isPalindrome(str, start, end)) {

                String part = str.substring(start, end + 1);

                printPartitions(
                    str,
                    end + 1,
                    result + part + " "
                );
            }
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String str = sc.nextLine();

        System.out.println("Palindromic partitions:");

        printPartitions(str, 0, "");

        sc.close();
    }
}

output:

Enter a string: aabc
Palindromic partitions:
a a b c 
aa b c 

26. Power Set of permutations of a string in Lexicographic order.

program:
import java.util.Arrays;
import java.util.Scanner;

public class LexicographicPermutations {

    static void generatePermutations(char[] arr, int index) {

        // Base case
        if (index == arr.length) {
            System.out.println(new String(arr));
            return;
        }

        for (int i = index; i < arr.length; i++) {

            // Swap
            char temp = arr[index];
            arr[index] = arr[i];
            arr[i] = temp;

            // Recursive call
            generatePermutations(arr, index + 1);

            // Backtrack
            temp = arr[index];
            arr[index] = arr[i];
            arr[i] = temp;
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String str = sc.nextLine();

        char[] arr = str.toCharArray();

        // Sort first for lexicographic order
        Arrays.sort(arr);

        generatePermutations(arr, 0);

        sc.close();
    }
}

output:

Enter a string: 123
123
132
213
231
321
312
