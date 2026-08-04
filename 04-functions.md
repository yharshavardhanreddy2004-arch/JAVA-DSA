1.Define two methods to print the maximum and the minimum number respectively among three numbers entered by the user.
import java.util.Scanner;

public class MaxMin {

    // Method to print maximum number
    static void printMax(int a, int b, int c) {
        if (a >= b && a >= c)
            System.out.println("Maximum = " + a);
        else if (b >= a && b >= c)
            System.out.println("Maximum = " + b);
        else
            System.out.println("Maximum = " + c);
    }

    // Method to print minimum number
    static void printMin(int a, int b, int c) {
        if (a <= b && a <= c)
            System.out.println("Minimum = " + a);
        else if (b <= a && b <= c)
            System.out.println("Minimum = " + b);
        else
            System.out.println("Minimum = " + c);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter first number: ");
        int a = sc.nextInt();

        System.out.print("Enter second number: ");
        int b = sc.nextInt();

        System.out.print("Enter third number: ");
        int c = sc.nextInt();

        printMax(a, b, c);
        printMin(a, b, c);

        sc.close();
    }
}

OUTPUT:
Enter first number: 3
Enter second number: 6
Enter third number: 9
Maximum = 9
Minimum = 3

2.Define a program to find out whether a given number is even or odd.

import java.util.Scanner;

public class EvenOdd {

    // Method to check even or odd
    static void checkNumber(int n) {
        if (n % 2 == 0)
            System.out.println(n + " is Even");
        else
            System.out.println(n + " is Odd");
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = sc.nextInt();

        checkNumber(num);

        sc.close();
    }
}
OUTPUT:
Enter a number: 1
1 is Odd

3.A person is eligible to vote if his/her age is greater than or equal to 18. Define a method to find out if he/she is eligible to vote.

import java.util.Scanner;

public class VoteEligibility {

    // Method to check voting eligibility
    static void checkVote(int age) {
        if (age >= 18)
            System.out.println("Eligible to vote");
        else
            System.out.println("Not eligible to vote");
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter your age: ");
        int age = sc.nextInt();

        checkVote(age);

        sc.close();
    }
}

OUTPUT:
Enter your age: 20
Eligible to vote

4.Write a program to print the sum of two numbers entered by user by defining your own method.

import java.util.Scanner;

public class SumOfTwoNumbers {

    // Method to calculate sum
    static void findSum(int a, int b) {
        int sum = a + b;
        System.out.println("Sum = " + sum);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter first number: ");
        int a = sc.nextInt();

        System.out.print("Enter second number: ");
        int b = sc.nextInt();

        findSum(a, b);

        sc.close();
    }
}
OUTPUT:
Enter first number: 1
Enter second number: 3
Sum = 4

5.Define a method that returns the product of two numbers entered by user.

import java.util.Scanner;

public class ProductOfTwoNumbers {

    // Method to return product
    static int findProduct(int a, int b) {
        return a * b;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter first number: ");
        int a = sc.nextInt();

        System.out.print("Enter second number: ");
        int b = sc.nextInt();

        int product = findProduct(a, b);

        System.out.println("Product = " + product);

        sc.close();
    }
}
OUTPUT:
Enter first number: 9
Enter second number: 7
Product = 63

6.Write a program to print the circumference and area of a circle of radius entered by user by defining your own method.

import java.util.Scanner;

public class Circle {

    // Method to print circumference
    static void circumference(double r) {
        double c = 2 * Math.PI * r;
        System.out.println("Circumference = " + c);
    }

    // Method to print area
    static void area(double r) {
        double a = Math.PI * r * r;
        System.out.println("Area = " + a);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter the radius: ");
        double radius = sc.nextDouble();

        circumference(radius);
        area(radius);

        sc.close();
    }
}

OUTPUT:
Enter the radius: 22.98
Circumference = 144.3875983589869
Area = 1659.0135051447596

7.Define a method to find out if a number is prime or not.

import java.util.Scanner;

public class PrimeNumber {

    // Method to check prime number
    static void checkPrime(int n) {
        if (n <= 1) {
            System.out.println(n + " is Not a Prime Number");
            return;
        }

        for (int i = 2; i <= n / 2; i++) {
            if (n % i == 0) {
                System.out.println(n + " is Not a Prime Number");
                return;
            }
        }

        System.out.println(n + " is a Prime Number");
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = sc.nextInt();

        checkPrime(num);

        sc.close();
    }
}
OUTPUT:
Enter a number: 4
4 is Not a Prime Number

8.Write a program that will ask the user to enter his/her marks (out of 100). Define a method that will display grades according to the marks entered as below:

import java.util.Scanner;

public class GradeCalculator {

    // Method to display grade
    static void displayGrade(int marks) {
        if (marks >= 90)
            System.out.println("Grade: A");
        else if (marks >= 80)
            System.out.println("Grade: B");
        else if (marks >= 70)
            System.out.println("Grade: C");
        else if (marks >= 60)
            System.out.println("Grade: D");
        else
            System.out.println("Grade: F");
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter your marks (0-100): ");
        int marks = sc.nextInt();

        displayGrade(marks);

        sc.close();
    }
}

OUTPUT:
Enter your marks (0-100): 99
Grade: A

9.Write a program to print the factorial of a number by defining a method named 'Factorial'.

import java.util.Scanner;

public class FactorialProgram {

    // Method to calculate factorial
    static int Factorial(int n) {
        int fact = 1;
        for (int i = 1; i <= n; i++) {
            fact = fact * i;
        }
        return fact;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = sc.nextInt();

        System.out.println("Factorial = " + Factorial(num));

        sc.close();
    }
}

OUTPUT:
Enter a number: 10
Factorial = 3628800

10.Write a function to find if a number is a palindrome or not. Take number as parameter.

import java.util.Scanner;

public class PalindromeNumber {

    // Method to check palindrome
    static void checkPalindrome(int num) {
        int original = num;
        int reverse = 0;

        while (num > 0) {
            int digit = num % 10;
            reverse = reverse * 10 + digit;
            num = num / 10;
        }

        if (original == reverse)
            System.out.println(original + " is a Palindrome Number");
        else
            System.out.println(original + " is Not a Palindrome Number");
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = sc.nextInt();

        checkPalindrome(num);

        sc.close();
    }
}

OUTPUT:
Enter a number: 44
44 is a Palindrome Number

11. Convert the programs in [flow of program](01-flow-of-program.md), [first java](02-first-java.md), [conditionals & loops](03-conditionals-loops.md) assignments into functions.
 01.FLOW OF PROGRAMME:
public class Main {

    static int add(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        System.out.println(add(10, 20));
    }
}
OUTPUT:
30

02.FIRST JAVA
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello Java");
    }
}
OUTPUT:
Hello Java
public class Main {
    public static void main(String[] args) {
        int num = 10;

        if (num % 2 == 0)
            System.out.println("Even");
        else
            System.out.println("Odd");
    }
}

OUTPUT:
Even

12.[Write a function to check if a given triplet is a Pythagorean triplet or not.
import java.util.Scanner;

public class PythagoreanTriplet {

    // Method to check Pythagorean triplet
    static void checkTriplet(int a, int b, int c) {
        int x = a * a;
        int y = b * b;
        int z = c * c;

        if (x + y == z || x + z == y || y + z == x)
            System.out.println("The given numbers are a Pythagorean Triplet");
        else
            System.out.println("The given numbers are not a Pythagorean Triplet");
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter first number: ");
        int a = sc.nextInt();

        System.out.print("Enter second number: ");
        int b = sc.nextInt();

        System.out.print("Enter third number: ");
        int c = sc.nextInt();

        checkTriplet(a, b, c);

        sc.close();
    }
}

OUTPUT:
Enter first number: 9
Enter second number: 9
Enter third number: 9
The given numbers are not a Pythagorean Triplet

13.Write a function that returns all prime numbers between two given numbers.
import java.util.Scanner;

public class PrimeNumbers {

    // Method to check if a number is prime
    static boolean isPrime(int num) {
        if (num <= 1)
            return false;

        for (int i = 2; i <= num / 2; i++) {
            if (num % i == 0)
                return false;
        }

        return true;
    }

    // Method to print prime numbers between two numbers
    static void printPrimes(int start, int end) {
        System.out.println("Prime numbers between " + start + " and " + end + " are:");

        for (int i = start; i <= end; i++) {
            if (isPrime(i))
                System.out.print(i + " ");
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter starting number: ");
        int start = sc.nextInt();

        System.out.print("Enter ending number: ");
        int end = sc.nextInt();

        printPrimes(start, end);

        sc.close();
    }
}
OUTPUT:
Enter starting number: 21
Enter ending number: 2
Prime numbers between 21 and 2 are:

14.Write a function that returns the sum of first n natural numbers.
import java.util.Scanner;

public class SumNaturalNumbers {

    // Method to return sum of first n natural numbers
    static int sumOfNaturalNumbers(int n) {
        int sum = 0;

        for (int i = 1; i <= n; i++) {
            sum = sum + i;
        }

        return sum;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter value of n: ");
        int n = sc.nextInt();

        int result = sumOfNaturalNumbers(n);

        System.out.println("Sum of first " + n + " natural numbers = " + result);

        sc.close();
    }
}

OUTPUT:
Enter value of n: 9
Sum of first 9 natural numbers = 45



 
