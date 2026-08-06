1. Area Of Circle.
   public class Main {
    public static void main(String[] args) {

        double radius = 5;
        double area = Math.PI * radius * radius;

        System.out.println("Area of Circle = " + area);
    }
}
output:
Area of Circle = 78.53981633974483

2. Area Of Triangle.
   public class Main {
    public static void main(String[] args) {

        double base = 10;
        double height = 5;

        double area = 0.5 * base * height;

        System.out.println("Area of Triangle = " + area);
    }
}

output:
Area of Triangle = 25.0

3. Area Of Rectangle
   public class Main {
    public static void main(String[] args) {

        int length = 10;
        int breadth = 5;

        int area = length * breadth;

        System.out.println("Area of Rectangle = " + area);
    }
}
output:
Area of Rectangle = 50

4. Area Of Isosceles Triangle.
   public class Main {
    public static void main(String[] args) {

        double base = 8;
        double height = 6;

        double area = 0.5 * base * height;

        System.out.println("Area of Isosceles Triangle = " + area);
    }
}
output:
Area of Isosceles Triangle = 24.0

5. Area Of Parallelogram.
   public class Main {
    public static void main(String[] args) {

        int base = 12;
        int height = 5;

        int area = base * height;

        System.out.println("Area of Parallelogram = " + area);
    }
}
output:
Area of Parallelogram = 60

6.Area Of Rhombus
public class Main {
    public static void main(String[] args) {

        double d1 = 10;
        double d2 = 8;

        double area = (d1 * d2) / 2;

        System.out.println("Area of Rhombus = " + area);
    }
}
output:
Area of Rhombus = 40.0

7.Area Of Equilateral Triangle
public class Main {
    public static void main(String[] args) {

        double side = 6;

        double area = (Math.sqrt(3) / 4) * side * side;

        System.out.println("Area of Equilateral Triangle = " + area);
    }
}
output:
Area of Equilateral Triangle = 15.588457268119896

8.Perimeter Of Circle
public class Main {
    public static void main(String[] args) {

        double radius = 5;

        double perimeter = 2 * Math.PI * radius;

        System.out.println("Perimeter of Circle = " + perimeter);
    }
}
output:
Perimeter of Circle = 31.41592653589793

9.Perimeter Of Equilateral Triangle
public class Main {
    public static void main(String[] args) {

        int side = 7;

        int perimeter = 3 * side;

        System.out.println("Perimeter of Equilateral Triangle = " + perimeter);
    }
}
output:
Perimeter of Equilateral Triangle = 21

10.Perimeter Of Parallelogram
public class Main {
    public static void main(String[] args) {

        int side1 = 10;
        int side2 = 5;

        int perimeter = 2 * (side1 + side2);

        System.out.println("Perimeter of Parallelogram = " + perimeter);
    }
}
output:
Perimeter of Parallelogram = 30

11.Perimeter of Rectangle
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double length = sc.nextDouble();
        double width = sc.nextDouble();

        double perimeter = 2 * (length + width);

        System.out.println("Perimeter = " + perimeter);
    }
}
output
Perimeter = 26.0

12.Perimeter of Square
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double side = sc.nextDouble();

        double perimeter = 4 * side;

        System.out.println("Perimeter = " + perimeter);
    }
}
output
Perimeter = 28.0

13.Perimeter of Rhombus
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double side = sc.nextDouble();

        double perimeter = 4 * side;

        System.out.println("Perimeter = " + perimeter);
    }
}
output
Perimeter = 36.0

14.Volume of Cone
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double radius = sc.nextDouble();
        double height = sc.nextDouble();

        double volume = (Math.PI * radius * radius * height) / 3;

        System.out.println("Volume = " + volume);
    }
}
output
Volume = 47.12388980384689

15.Volume of Prism
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double baseArea = sc.nextDouble();
        double height = sc.nextDouble();

        double volume = baseArea * height;

        System.out.println("Volume = " + volume);
    }
}
output
Volume = 160.0

16.Volume of Cylinder
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double radius = sc.nextDouble();
        double height = sc.nextDouble();

        double volume = Math.PI * radius * radius * height;

        System.out.println("Volume = " + volume);
    }
}
output:
Volume of Cylinder = 785.3981633974483

17.Volume of Sphere
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double radius = sc.nextDouble();

        double volume = (4.0 / 3.0) * Math.PI * radius * radius * radius;

        System.out.println("Volume = " + volume);
    }
}
output
Volume = 113.09733552923255

18.Volume of Pyramid
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double baseArea = sc.nextDouble();
        double height = sc.nextDouble();

        double volume = (baseArea * height) / 3;

        System.out.println("Volume = " + volume);
    }
}
output
Volume = 90.0

19.Curved Surface Area of Cylinder
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double radius = sc.nextDouble();
        double height = sc.nextDouble();

        double csa = 2 * Math.PI * radius * height;

        System.out.println("Curved Surface Area = " + csa);
    }
}
output
Curved Surface Area = 94.24777960769379

20.Total Surface Area of Cube
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double side = sc.nextDouble();

        double surfaceArea = 6 * side * side;

        System.out.println("Total Surface Area = " + surfaceArea);
    }
}
output
Total Surface Area = 96.0

21. Fibonacci Series In Java Programs

program:
import java.util.Scanner;

public class FibonacciSeries {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of terms: ");
        int n = sc.nextInt();

        int first = 0, second = 1;

        System.out.print("Fibonacci Series: ");

        for (int i = 1; i <= n; i++) {
            System.out.print(first + " ");

            int next = first + second;
            first = second;
            second = next;
        }

        sc.close();
    }
}

output

Enter number of terms: 5
Fibonacci Series: 0 1 1 2 3 

22. Subtract the Product and Sum of Digits of an Integer.

program:
import java.util.Scanner;

public class SubtractProductAndSum {
    public static int subtractProductAndSum(int n) {

        int product = 1;
        int sum = 0;

        while (n > 0) {
            int digit = n % 10;
            product *= digit;
            sum += digit;
            n /= 10;
        }

        return product - sum;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number: ");
        int n = sc.nextInt();

        System.out.println(subtractProductAndSum(n));

        sc.close();
    }
}

output:
Enter number: 132
0

23. Input a number and print all the factors of that number (use loops).

 program:
  import java.util.Scanner;

public class Factors {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number: ");
        int n = sc.nextInt();

        System.out.println("Factors:");

        for (int i = 1; i <= n; i++) {
            if (n % i == 0) {
                System.out.print(i + " ");
            }
        }

        sc.close();
    }
}

output:
Enter number: 111
Factors:
1 3 37 111

24. Take integer inputs till the user enters 0 and print the sum of all numbers

program:
import java.util.Scanner;

public class SumUntilZero {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int sum = 0;
        int num;

        System.out.println("Enter numbers (0 to stop):");

        while (true) {
            num = sc.nextInt();

            if (num == 0)
                break;

            sum += num;
        }

        System.out.println("Sum = " + sum);

        sc.close();
    }
}


Input:5
10
15
0
output:
Sum = 30

25. Take integer inputs till the user enters 0 and print the largest number from
all.

program:
import java.util.Scanner;

public class LargestNumber {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int num;
        int largest = Integer.MIN_VALUE;

        System.out.println("Enter numbers (0 to stop):");

        while (true) {
            num = sc.nextInt();

            if (num == 0)
                break;

            if (num > largest) {
                largest = num;
            }
        }

        if (largest == Integer.MIN_VALUE)
            System.out.println("No numbers entered.");
        else
            System.out.println("Largest = " + largest);

        sc.close();
    }
}

output:

Enter numbers (0 to stop):
12
8
45
19
0
Largest = 45

26. Addition Of Two Numbers

program:
import java.util.Scanner;

public class Addition {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter first number: ");
        int a = sc.nextInt();

        System.out.print("Enter second number: ");
        int b = sc.nextInt();

        int sum = a + b;

        System.out.println("Sum = " + sum);

        sc.close();
    }
}

output:

Enter first number: 15
Enter second number: 25
Sum = 40


   

