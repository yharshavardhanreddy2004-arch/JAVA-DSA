## Easy
1.Roman to Integer.
public class RomanToInteger {

    public static int romanToInt(String s) {
        int total = 0;

        for (int i = 0; i < s.length(); i++) {
            int current = value(s.charAt(i));

            if (i < s.length() - 1 && current < value(s.charAt(i + 1))) {
                total -= current;
            } else {
                total += current;
            }
        }

        return total;
    }

    public static int value(char c) {
        switch (c) {
            case 'I': return 1;
            case 'V': return 5;
            case 'X': return 10;
            case 'L': return 50;
            case 'C': return 100;
            case 'D': return 500;
            case 'M': return 1000;
            default: return 0;
        }
    }

    public static void main(String[] args) {
        String roman = "MCMXCIV";
        System.out.println(romanToInt(roman)); // Output: 1994
    }
}
OUTPUT:
1994

2.Happy Number.
public class HappyNumber {

    public static boolean isHappy(int n) {
        while (n != 1 && n != 4) {
            int sum = 0;

            while (n > 0) {
                int digit = n % 10;
                sum += digit * digit;
                n /= 10;
            }

            n = sum;
        }

        return n == 1;
    }

    public static void main(String[] args) {
        int n = 19;

        if (isHappy(n)) {
            System.out.println(n + " is a Happy Number");
        } else {
            System.out.println(n + " is not a Happy Number");
        }
    }
}

OUTPUT:
19 is a Happy Number

3.Armstrong Numbers.
public class ArmstrongNumber {

    public static boolean isArmstrong(int n) {
        int original = n;
        int sum = 0;

        // Count the number of digits
        int digits = String.valueOf(n).length();

        while (n > 0) {
            int digit = n % 10;
            sum += Math.pow(digit, digits);
            n /= 10;
        }

        return sum == original;
    }

    public static void main(String[] args) {
        int n = 153;

        if (isArmstrong(n)) {
            System.out.println(n + " is an Armstrong Number");
        } else {
            System.out.println(n + " is not an Armstrong Number");
        }
    }
}
OUTPUT:
153 is an Armstrong Number.

4.Power of Four.
public class PowerOfFour {

    public static boolean isPowerOfFour(int n) {
        if (n <= 0) {
            return false;
        }

        while (n % 4 == 0) {
            n = n / 4;
        }

        return n == 1;
    }

    public static void main(String[] args) {
        int n = 64;

        if (isPowerOfFour(n)) {
            System.out.println(n + " is a Power of Four");
        } else {
            System.out.println(n + " is not a Power of Four");
        }
    }
}
OUTPUT:
64 is a Power of Four.

5.Factorial.
public class Factorial {

    public static int factorial(int n) {
        int result = 1;

        for (int i = 1; i <= n; i++) {
            result = result * i;
        }

        return result;
    }

    public static void main(String[] args) {
        int n = 5;
        System.out.println("Factorial of " + n + " is " + factorial(n));
    }
}
OUTPUT:
Factorial of 5 is 120.

6.Excel Sheet Column Title.
public class ExcelSheetColumnTitle {

    public static String convertToTitle(int columnNumber) {
        StringBuilder result = new StringBuilder();

        while (columnNumber > 0) {
            columnNumber--; // Convert to 0-based index
            int remainder = columnNumber % 26;
            result.append((char) ('A' + remainder));
            columnNumber = columnNumber / 26;
        }

        return result.reverse().toString();
    }

    public static void main(String[] args) {
        int columnNumber = 28;
        System.out.println(convertToTitle(columnNumber)); // Output: AB
    }
}
OUTPUT:
AB

7.Maximum Product of Three Numbers.
import java.util.Arrays;

public class MaximumProduct {

    public static int maximumProduct(int[] nums) {
        Arrays.sort(nums);

        int n = nums.length;

        // Maximum of:
        // 1. Product of the three largest numbers
        // 2. Product of the two smallest (negative) numbers and the largest number
        return Math.max(
                nums[n - 1] * nums[n - 2] * nums[n - 3],
                nums[0] * nums[1] * nums[n - 1]
        );
    }

    public static void main(String[] args) {
        int[] nums = {-10, -10, 5, 2};

        System.out.println(maximumProduct(nums)); // Output: 500
    }
}
OUTPUT:
500

8.Climbing Stairs.
public class ClimbingStairs {

    public static int climbStairs(int n) {
        if (n <= 2) {
            return n;
        }

        int first = 1;
        int second = 2;

        for (int i = 3; i <= n; i++) {
            int current = first + second;
            first = second;
            second = current;
        }

        return second;
    }

    public static void main(String[] args) {
        int n = 5;
        System.out.println(climbStairs(n)); // Output: 8
    }
}
OUTPUT:
8

9.Self Dividing Number.
import java.util.ArrayList;
import java.util.List;

public class SelfDividingNumbers {

    public static List<Integer> selfDividingNumbers(int left, int right) {
        List<Integer> result = new ArrayList<>();

        for (int i = left; i <= right; i++) {
            if (isSelfDividing(i)) {
                result.add(i);
            }
        }

        return result;
    }

    public static boolean isSelfDividing(int num) {
        int original = num;

        while (num > 0) {
            int digit = num % 10;

            // If digit is 0 or doesn't divide the number
            if (digit == 0 || original % digit != 0) {
                return false;
            }

            num /= 10;
        }

        return true;
    }

    public static void main(String[] args) {
        int left = 1;
        int right = 22;

        System.out.println(selfDividingNumbers(left, right));
    }
}
OUTPUT:
[1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]

10.Add Binary.
public class AddBinary {

    public static String addBinary(String a, String b) {
        StringBuilder result = new StringBuilder();

        int i = a.length() - 1;
        int j = b.length() - 1;
        int carry = 0;

        while (i >= 0 || j >= 0 || carry > 0) {
            int sum = carry;

            if (i >= 0) {
                sum += a.charAt(i) - '0';
                i--;
            }

            if (j >= 0) {
                sum += b.charAt(j) - '0';
                j--;
            }

            result.append(sum % 2);
            carry = sum / 2;
        }

        return result.reverse().toString();
    }

    public static void main(String[] args) {
        String a = "1010";
        String b = "1011";

        System.out.println(addBinary(a, b)); // Output: 10101
    }
}
OUTPUT:
10101

11.Power of Two.
public class PowerOfTwo {

    public static boolean isPowerOfTwo(int n) {
        if (n <= 0) {
            return false;
        }

        while (n % 2 == 0) {
            n = n / 2;
        }

        return n == 1;
    }

    public static void main(String[] args) {
        int n = 16;

        if (isPowerOfTwo(n)) {
            System.out.println(n + " is a Power of Two");
        } else {
            System.out.println(n + " is not a Power of Two");
        }
    }
}
OUTPUT:
16 is a Power of Two

## MEDIUM
1.Integer to Roman.
public class IntegerToRoman {

    public static String intToRoman(int num) {
        int[] values = {
            1000, 900, 500, 400,
            100, 90, 50, 40,
            10, 9, 5, 4, 1
        };

        String[] symbols = {
            "M", "CM", "D", "CD",
            "C", "XC", "L", "XL",
            "X", "IX", "V", "IV", "I"
        };

        StringBuilder result = new StringBuilder();

        for (int i = 0; i < values.length; i++) {
            while (num >= values[i]) {
                result.append(symbols[i]);
                num -= values[i];
            }
        }

        return result.toString();
    }

    public static void main(String[] args) {
        int num = 1994;

        System.out.println(intToRoman(num)); // Output: MCMXCIV
    }
}
OUTPUT:
MCMXCIV

2.Unique Paths.
public class UniquePaths {

    public static int uniquePaths(int m, int n) {
        int[] dp = new int[n];

        // First row has only one way to reach each cell
        for (int i = 0; i < n; i++) {
            dp[i] = 1;
        }

        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[j] = dp[j] + dp[j - 1];
            }
        }

        return dp[n - 1];
    }

    public static void main(String[] args) {
        int m = 3;
        int n = 7;

        System.out.println(uniquePaths(m, n)); // Output: 28
    }
}
OUTPUT:
28

3.Gray Code.
import java.util.ArrayList;
import java.util.List;

public class GrayCode {

    public static List<Integer> grayCode(int n) {
        List<Integer> result = new ArrayList<>();

        int size = 1 << n; // Total number of gray codes

        for (int i = 0; i < size; i++) {
            result.add(i ^ (i >> 1));
        }

        return result;
    }

    public static void main(String[] args) {
        int n = 2;

        System.out.println(grayCode(n));
    }
}

OUTPUT:
[0, 1, 3, 2]

4.Perfect Squares.
import java.util.Arrays;

public class PerfectSquares {

    public static int numSquares(int n) {
        int[] dp = new int[n + 1];

        // Initialize with maximum possible value
        Arrays.fill(dp, Integer.MAX_VALUE);

        dp[0] = 0;

        for (int i = 1; i <= n; i++) {
            for (int j = 1; j * j <= i; j++) {
                dp[i] = Math.min(dp[i], dp[i - j * j] + 1);
            }
        }

        return dp[n];
    }

    public static void main(String[] args) {
        int n = 12;

        System.out.println(numSquares(n)); // Output: 3
    }
}

OUTPUT:
3

5.Next Greater Element III.
public class NextGreaterElementIII {

    public static int nextGreaterElement(int n) {
        char[] digits = String.valueOf(n).toCharArray();

        int i = digits.length - 2;

        // Step 1: Find the first decreasing digit
        while (i >= 0 && digits[i] >= digits[i + 1]) {
            i--;
        }

        // If no such digit exists, next greater number is impossible
        if (i < 0) {
            return -1;
        }

        // Step 2: Find the smallest digit greater than digits[i]
        int j = digits.length - 1;
        while (digits[j] <= digits[i]) {
            j--;
        }

        // Step 3: Swap the two digits
        char temp = digits[i];
        digits[i] = digits[j];
        digits[j] = temp;

        // Step 4: Reverse the remaining digits
        reverse(digits, i + 1, digits.length - 1);

        long result = Long.parseLong(new String(digits));

        // Check integer range
        return result <= Integer.MAX_VALUE ? (int) result : -1;
    }

    public static void reverse(char[] arr, int start, int end) {
        while (start < end) {
            char temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;

            start++;
            end--;
        }
    }

    public static void main(String[] args) {
        int n = 12443322;

        System.out.println(nextGreaterElement(n)); 
        // Output: 13222344
    }
}
OUTPUT:
13222344

6.Angle Between Hands of a Clock.
public class AngleBetweenHandsOfClock {

    public static double angleClock(int hour, int minutes) {
        // Calculate hour hand angle
        double hourAngle = (hour % 12) * 30 + minutes * 0.5;

        // Calculate minute hand angle
        double minuteAngle = minutes * 6;

        // Find the difference
        double angle = Math.abs(hourAngle - minuteAngle);

        // Return the smaller angle
        return Math.min(angle, 360 - angle);
    }

    public static void main(String[] args) {
        int hour = 3;
        int minutes = 15;

        System.out.println(angleClock(hour, minutes)); // Output: 7.5
    }
}
OUTPUT:
7.5

7.String to Integer (atoi).
public class StringToInteger {

    public static int myAtoi(String s) {
        int i = 0;
        int sign = 1;
        int result = 0;

        // Remove leading spaces
        while (i < s.length() && s.charAt(i) == ' ') {
            i++;
        }

        // Check sign
        if (i < s.length() && (s.charAt(i) == '+' || s.charAt(i) == '-')) {
            if (s.charAt(i) == '-') {
                sign = -1;
            }
            i++;
        }

        // Convert digits to integer
        while (i < s.length() && Character.isDigit(s.charAt(i))) {
            int digit = s.charAt(i) - '0';

            // Check overflow
            if (result > (Integer.MAX_VALUE - digit) / 10) {
                return sign == 1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            }

            result = result * 10 + digit;
            i++;
        }

        return result * sign;
    }

    public static void main(String[] args) {
        String s = "   -42";

        System.out.println(myAtoi(s)); // Output: -42
    }
}
OUTPUT:
-42

8.The k<sup>th</sup> Factor of n.
public class KthFactorOfN {

    public static int kthFactor(int n, int k) {
        int count = 0;

        for (int i = 1; i <= n; i++) {
            if (n % i == 0) {
                count++;

                if (count == k) {
                    return i;
                }
            }
        }

        return -1;
    }

    public static void main(String[] args) {
        int n = 12;
        int k = 3;

        System.out.println(kthFactor(n, k)); // Output: 3
    }
}
OUTPUT:
3

9.Queries on Number of Points Inside a Circle.
import java.util.ArrayList;
import java.util.List;

public class PointsInsideCircle {

    public static int[] countPoints(int[][] points, int[][] queries) {
        int[] result = new int[queries.length];

        for (int i = 0; i < queries.length; i++) {
            int count = 0;

            int centerX = queries[i][0];
            int centerY = queries[i][1];
            int radius = queries[i][2];

            for (int[] point : points) {
                int x = point[0];
                int y = point[1];

                // Distance formula (without square root)
                int distance = (x - centerX) * (x - centerX)
                             + (y - centerY) * (y - centerY);

                if (distance <= radius * radius) {
                    count++;
                }
            }

            result[i] = count;
        }

        return result;
    }

    public static void main(String[] args) {
        int[][] points = {
            {1, 3},
            {3, 3},
            {5, 3},
            {2, 2}
        };

        int[][] queries = {
            {2, 3, 1},
            {4, 3, 1},
            {1, 1, 2}
        };

        int[] answer = countPoints(points, queries);

        for (int count : answer) {
            System.out.println(count);
        }
    }
}
OUTPUT:
3
2
2

10.Product of Array Except Sel.
public class ProductExceptSelf {

    public static int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];

        // Store prefix products
        result[0] = 1;
        for (int i = 1; i < n; i++) {
            result[i] = result[i - 1] * nums[i - 1];
        }

        // Store suffix products and multiply with prefix
        int suffix = 1;

        for (int i = n - 1; i >= 0; i--) {
            result[i] = result[i] * suffix;
            suffix = suffix * nums[i];
        }

        return result;
    }

    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4};

        int[] answer = productExceptSelf(nums);

        for (int num : answer) {
            System.out.print(num + " ");
        }
        // Output: 24 12 8 6
    }
}
OUTPUT:
24 12 8 6 

11.Multiply Strings.
public class MultiplyStrings {

    public static String multiply(String num1, String num2) {
        // Handle zero case
        if (num1.equals("0") || num2.equals("0")) {
            return "0";
        }

        int n1 = num1.length();
        int n2 = num2.length();

        int[] result = new int[n1 + n2];

        // Multiply each digit
        for (int i = n1 - 1; i >= 0; i--) {
            for (int j = n2 - 1; j >= 0; j--) {

                int digit1 = num1.charAt(i) - '0';
                int digit2 = num2.charAt(j) - '0';

                int product = digit1 * digit2;

                int sum = product + result[i + j + 1];

                result[i + j + 1] = sum % 10;
                result[i + j] += sum / 10;
            }
        }

        // Convert array to string
        StringBuilder answer = new StringBuilder();

        for (int num : result) {
            if (answer.length() == 0 && num == 0) {
                continue;
            }
            answer.append(num);
        }

        return answer.toString();
    }

    public static void main(String[] args) {
        String num1 = "123";
        String num2 = "456";

        System.out.println(multiply(num1, num2)); 
        // Output: 56088
    }
}
OUTPUT:
56088

12.Encode and Decode TinyURL.
import java.util.HashMap;
import java.util.Map;

public class EncodeDecodeTinyURL {

    private Map<String, String> urlMap = new HashMap<>();
    private int id = 1;

    // Encodes a URL to a shortened URL
    public String encode(String longUrl) {
        String shortKey = "abc" + id;
        id++;

        urlMap.put(shortKey, longUrl);

        return "http://tinyurl.com/" + shortKey;
    }

    // Decodes a shortened URL to the original URL
    public String decode(String shortUrl) {
        String key = shortUrl.substring(shortUrl.lastIndexOf("/") + 1);

        return urlMap.get(key);
    }

    public static void main(String[] args) {
        EncodeDecodeTinyURL obj = new EncodeDecodeTinyURL();

        String longUrl = "https://www.example.com/my-long-url";

        String shortUrl = obj.encode(longUrl);

        System.out.println("Short URL: " + shortUrl);
        System.out.println("Original URL: " + obj.decode(shortUrl));
    }
}
OUTPUT:
Short URL: http://tinyurl.com/abc1
Original URL: https://www.example.com/my-long-url

13.Integer Break.
public class IntegerBreak {

    public static int integerBreak(int n) {
        int[] dp = new int[n + 1];

        dp[1] = 1;

        for (int i = 2; i <= n; i++) {
            for (int j = 1; j < i; j++) {
                // Either split i into j and (i-j)
                dp[i] = Math.max(dp[i], Math.max(j * (i - j), j * dp[i - j]));
            }
        }

        return dp[n];
    }

    public static void main(String[] args) {
        int n = 10;

        System.out.println(integerBreak(n)); // Output: 36
    }
}

OUTPUT:
36

## HARD


1.Permutation Sequence.
import java.util.ArrayList;
import java.util.List;

public class PermutationSequence {

    public static String getPermutation(int n, int k) {
        List<Integer> numbers = new ArrayList<>();

        // Store numbers 1 to n
        for (int i = 1; i <= n; i++) {
            numbers.add(i);
        }

        // Calculate factorials
        int[] fact = new int[n];
        fact[0] = 1;

        for (int i = 1; i < n; i++) {
            fact[i] = fact[i - 1] * i;
        }

        StringBuilder result = new StringBuilder();

        // Convert k to 0-based index
        k--;

        for (int i = n; i >= 1; i--) {
            int index = k / fact[i - 1];

            result.append(numbers.get(index));
            numbers.remove(index);

            k = k % fact[i - 1];
        }

        return result.toString();
    }

    public static void main(String[] args) {
        int n = 3;
        int k = 3;

        System.out.println(getPermutation(n, k)); 
        // Output: 213
    }
}
OUTPUT:
213

2.Basic Calculator.
import java.util.Stack;

public class BasicCalculator {

    public static int calculate(String s) {
        Stack<Integer> stack = new Stack<>();

        int result = 0;
        int number = 0;
        int sign = 1;

        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);

            if (Character.isDigit(ch)) {
                number = number * 10 + (ch - '0');
            } 
            else if (ch == '+') {
                result += sign * number;
                number = 0;
                sign = 1;
            } 
            else if (ch == '-') {
                result += sign * number;
                number = 0;
                sign = -1;
            } 
            else if (ch == '(') {
                stack.push(result);
                stack.push(sign);

                result = 0;
                sign = 1;
            } 
            else if (ch == ')') {
                result += sign * number;
                number = 0;

                result *= stack.pop(); // previous sign
                result += stack.pop(); // previous result
            }
        }

        return result + sign * number;
    }

    public static void main(String[] args) {
        String s = "(1+(4+5+2)-3)+(6+8)";

        System.out.println(calculate(s));
        // Output: 23
    }
}
OUTPUT:
23

3.Max Points on a Line.
import java.util.HashMap;
import java.util.Map;

public class MaxPointsOnLine {

    public static int maxPoints(int[][] points) {
        int n = points.length;

        if (n <= 2) {
            return n;
        }

        int max = 0;

        for (int i = 0; i < n; i++) {
            Map<String, Integer> map = new HashMap<>();
            int samePoint = 1;
            int localMax = 0;

            for (int j = i + 1; j < n; j++) {
                int x1 = points[i][0];
                int y1 = points[i][1];

                int x2 = points[j][0];
                int y2 = points[j][1];

                int dx = x2 - x1;
                int dy = y2 - y1;

                // Same point
                if (dx == 0 && dy == 0) {
                    samePoint++;
                    continue;
                }

                // Reduce slope using GCD
                int gcd = gcd(dx, dy);
                dx /= gcd;
                dy /= gcd;

                String slope = dx + "/" + dy;

                map.put(slope, map.getOrDefault(slope, 0) + 1);

                localMax = Math.max(localMax, map.get(slope));
            }

            max = Math.max(max, localMax + samePoint);
        }

        return max;
    }

    public static int gcd(int a, int b) {
        a = Math.abs(a);
        b = Math.abs(b);

        while (b != 0) {
            int temp = a % b;
            a = b;
            b = temp;
        }

        return a;
    }

    public static void main(String[] args) {
        int[][] points = {
            {1, 1},
            {2, 2},
            {3, 3}
        };

        System.out.println(maxPoints(points)); 
        // Output: 3
    }
}
OUTPUT:
3

4.Number of Digit One.
public class NumberOfDigitOne {

    public static int countDigitOne(int n) {
        int count = 0;

        for (long factor = 1; factor <= n; factor *= 10) {
            long lower = n % factor;
            long current = (n / factor) % 10;
            long higher = n / (factor * 10);

            if (current == 0) {
                count += higher * factor;
            } 
            else if (current == 1) {
                count += higher * factor + lower + 1;
            } 
            else {
                count += (higher + 1) * factor;
            }
        }

        return count;
    }

    public static void main(String[] args) {
        int n = 13;

        System.out.println(countDigitOne(n)); 
        // Output: 6
    }
}
OUTPUT:
6

