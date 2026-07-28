Input a year and find whether it is a leap year or not.
import java.util.Scanner;

public class LeapYear {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a year: ");
        int year = sc.nextInt();

        if ((year % 400 == 0) || (year % 4 == 0 && year % 100 != 0)) {
            System.out.println(year + " is a Leap Year.");
        } else {
            System.out.println(year + " is Not a Leap Year.");
        }

        sc.close();
    }
}
output:
Enter a year: 2022
2022 is Not a Leap Year.

=== Code Execution Successful ===

2.Take two numbers and print the sum of both.
import java.util.Scanner;

public class SumOfTwoNumbers {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter first number: ");
        int num1 = sc.nextInt();

        System.out.print("Enter second number: ");
        int num2 = sc.nextInt();

        int sum = num1 + num2;

        System.out.println("Sum = " + sum);

        sc.close();
    }
}
output:
Enter first number: 9
Enter second number: 2
Sum = 11

=== Code Execution Successful ===

3.Take a number as input and print the multiplication table for it.
import java.util.Scanner;

public class MultiplicationTable {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = sc.nextInt();

        System.out.println("Multiplication Table of " + num + ":");

        for (int i = 1; i <= 10; i++) {
            System.out.println(num + " x " + i + " = " + (num * i));
        }

        sc.close();
    }
}
output:
Enter a number: 9
Multiplication Table of 9:
9 x 1 = 9
9 x 2 = 18
9 x 3 = 27
9 x 4 = 36
9 x 5 = 45
9 x 6 = 54
9 x 7 = 63
9 x 8 = 72
9 x 9 = 81
9 x 10 = 90

=== Code Execution Successful ===

4.Take 2 numbers as inputs and find their HCF and LCM.
import java.util.Scanner;

public class HCFAndLCM {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter first number: ");
        int num1 = sc.nextInt();

        System.out.print("Enter second number: ");
        int num2 = sc.nextInt();

        int a = num1;
        int b = num2;

        // Find HCF (GCD) using Euclidean Algorithm
        while (b != 0) {
            int temp = b;
            b = a % b;
            a = temp;
        }

        int hcf = a;
        int lcm = (num1 * num2) / hcf;

        System.out.println("HCF = " + hcf);
        System.out.println("LCM = " + lcm);

        sc.close();
    }
}
output:
Enter first number: 2
Enter second number: 4
HCF = 2
LCM = 4

=== Code Execution Successful ===

5.Keep taking numbers as inputs till the user enters ‘x’, after that print sum of all
import java.util.Scanner;

public class SumUntilX {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int sum = 0;

        while (true) {
            System.out.print("Enter a number (or 'x' to stop): ");
            String input = sc.next();

            if (input.equalsIgnoreCase("x")) {
                break;
            }

            sum += Integer.parseInt(input);
        }

        System.out.println("Sum = " + sum);

        sc.close();
    }
}
output:
Enter a number (or 'x' to stop): 10
Enter a number (or 'x' to stop): 20
Enter a number (or 'x' to stop): 30
Enter a number (or 'x' to stop): x
Sum = 60

=== Code Execution Successful ===
