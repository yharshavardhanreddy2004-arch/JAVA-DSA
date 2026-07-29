Write a program to print whether a number is even or odd, also take input from the user.
import java.util.Scanner;

public class EvenOdd {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = sc.nextInt();

        System.out.println(num % 2 == 0 ? "Even" : "Odd");

        sc.close();
    }
}
output:
Enter a number: 3
Odd

2.Take name as input and print a greeting message for that particular name.
import java.util.Scanner;

public class Greeting {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Take name as input
        System.out.print("Enter your name: ");
        String name = sc.nextLine();

        // Print greeting
        System.out.println("Hello, " + name + "! Welcome!");

        sc.close();
    }
}
output:
Enter your name: ram krishna
Hello, ram krishna! Welcome!
3.Write a program to input principal, time, and rate (P, T, R) from the user and find Simple Interest.
import java.util.Scanner;

public class SimpleInterest {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input principal, time, and rate
        System.out.print("Enter Principal (P): ");
        double principal = sc.nextDouble();

        System.out.print("Enter Time (T): ");
        double time = sc.nextDouble();

        System.out.print("Enter Rate (R): ");
        double rate = sc.nextDouble();

        // Calculate Simple Interest
        double simpleInterest = (principal * time * rate) / 100;

        // Display the result
        System.out.println("Simple Interest = " + simpleInterest);

        sc.close();
    }
}
output:
Enter Principal (P): 2
Enter Time (T): 4
Enter Rate (R): 6
Simple Interest = 0.48

4.Take in two numbers and an operator (+, -, *, /) and calculate the value. (Use if conditions)
import java.util.Scanner;

public class Calculator {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input two numbers
        System.out.print("Enter first number: ");
        double num1 = sc.nextDouble();

        System.out.print("Enter second number: ");
        double num2 = sc.nextDouble();

        // Input operator
        System.out.print("Enter operator (+, -, *, /): ");
        char operator = sc.next().charAt(0);

        // Calculate using switch
        switch (operator) {
            case '+':
                System.out.println("Result = " + (num1 + num2));
                break;

            case '-':
                System.out.println("Result = " + (num1 - num2));
                break;

            case '*':
                System.out.println("Result = " + (num1 * num2));
                break;

            case '/':
                System.out.println("Result = " + (num1 / num2));
                break;

            default:
                System.out.println("Invalid operator");
        }

        sc.close();
    }
}
output:
Enter first number: 2
Enter second number: 3
Enter operator (+, -, *, /): /
Result = 0.6666666666666666

5.Take 2 numbers as input and print the largest number.
import java.util.Scanner;

public class LargestNumber {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input two numbers
        System.out.print("Enter first number: ");
        int num1 = sc.nextInt();

        System.out.print("Enter second number: ");
        int num2 = sc.nextInt();

        // Print largest number
        System.out.println("Largest number = " + Math.max(num1, num2));

        sc.close();
    }
}Enter first number: 1
Enter second number: 8
Largest number = 8

6.Input currency in rupees and output in USD.
import java.util.Scanner;

public class CurrencyConverter {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input amount in Rupees
        System.out.print("Enter amount in Rupees: ");
        double rupees = sc.nextDouble();

        // Conversion rate (example: 1 USD = 83 INR)
        double exchangeRate = 83.0;

        // Convert Rupees to USD
        double dollars = rupees / exchangeRate;

        // Display result
        System.out.println("Amount in USD = $" + dollars);

        sc.close();
    }
}
output:
Enter amount in Rupees: 3
Amount in USD = $0.03614457831325301

7.To calculate Fibonacci Series up to n numbers.
import java.util.Scanner;

public class FibonacciSeries {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input number of terms
        System.out.print("Enter number of terms: ");
        int n = sc.nextInt();

        int first = 0, second = 1;

        System.out.println("Fibonacci Series:");

        // Generate Fibonacci series
        for (int i = 1; i <= n; i++) {
            System.out.print(first + " ");

            int next = first + second;
            first = second;
            second = next;
        }

        sc.close();
    }
}
output:
Enter number of terms: 9
Fibonacci Series:
0 1 1 2 3 5 8 13 21

8.To find out whether the given String is Palindrome or not.
import java.util.Scanner;

public class StringPalindrome {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input string
        System.out.print("Enter a string: ");
        String str = sc.nextLine();

        // Reverse the string
        String rev = new StringBuilder(str).reverse().toString();

        // Check palindrome without if-else
        System.out.println(str.equals(rev) ? "Palindrome" : "Not Palindrome");

        sc.close();
    }
}
output:
1st : Enter a string: madam
Palindrome.
2nd : Enter a string: domnick
Not Palindrome.

9.To find Armstrong Number between two given number.
import java.util.Scanner;

public class ArmstrongRange {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter starting number: ");
        int start = sc.nextInt();

        System.out.print("Enter ending number: ");
        int end = sc.nextInt();

        System.out.println("Armstrong Numbers:");

        for (int i = start; i <= end; i++) {

            int num = i;
            int sum = 0;
            int digits = String.valueOf(i).length();

            while (num > 0) {
                int rem = num % 10;
                sum += Math.pow(rem, digits);
                num /= 10;
            }

            String result = (sum == i) ? String.valueOf(i) : "";

            System.out.println(result);
        }

        sc.close();
    }
}


output:
Enter starting number: 3
Enter ending number: 9
Armstrong Numbers:
3
4
5
6
7
8
9
