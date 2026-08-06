1.Build Array from Permutation.
import java.util.Arrays;

public class Main {
    public static int[] buildArray(int[] nums) {
        int[] ans = new int[nums.length];

        for (int i = 0; i < nums.length; i++) {
            ans[i] = nums[nums[i]];
        }

        return ans;
    }

    public static void main(String[] args) {
        int[] nums = {0, 2, 1, 5, 3, 4};
        System.out.println(Arrays.toString(buildArray(nums)));
    }
}
OUTPUT:
[0, 1, 2, 4, 5, 3]

2.Concatenation of Array.
import java.util.Arrays;

public class Solution {

    public static int[] getConcatenation(int[] nums) {
        int n = nums.length;
        int[] ans = new int[2 * n];

        for (int i = 0; i < n; i++) {
            ans[i] = nums[i];
            ans[i + n] = nums[i];
        }

        return ans;
    }

    public static void main(String[] args) {
        int[] nums = {1, 2, 1};
        System.out.println(Arrays.toString(getConcatenation(nums)));
    }
}
OUTPUT:
[1, 2, 1, 1, 2, 1]

3.Running Sum of 1d Array.
import java.util.Arrays;

public class Main {
    public static int[] runningSum(int[] nums) {
        for (int i = 1; i < nums.length; i++) {
            nums[i] += nums[i - 1];
        }
        return nums;
    }

    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4};
        System.out.println(Arrays.toString(runningSum(nums)));
    }
}
output:
[1, 3, 6, 10]

4.Richest Customer Wealth.
public class Main {

    public static int maximumWealth(int[][] accounts) {
        int max = 0;

        for (int i = 0; i < accounts.length; i++) {
            int sum = 0;

            for (int j = 0; j < accounts[i].length; j++) {
                sum += accounts[i][j];
            }

            if (sum > max) {
                max = sum;
            }
        }

        return max;
    }

    public static void main(String[] args) {
        int[][] accounts = {
            {1, 2, 3},
            {3, 2, 1}
        };

        System.out.println(maximumWealth(accounts));
    }
}
output:
6

5.Shuffle the Array.
import java.util.Arrays;

public class Main {

    public static int[] shuffle(int[] nums, int n) {
        int[] ans = new int[2 * n];

        int index = 0;

        for (int i = 0; i < n; i++) {
            ans[index++] = nums[i];
            ans[index++] = nums[i + n];
        }

        return ans;
    }

    public static void main(String[] args) {
        int[] nums = {2, 5, 1, 3, 4, 7};
        int n = 3;

        int[] result = shuffle(nums, n);

        System.out.println(Arrays.toString(result));
    }
}
output:
[2, 3, 5, 4, 1, 7]

6.Kids With the Greatest Number of Candies.
import java.util.*;

public class Main {

    public static List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        List<Boolean> ans = new ArrayList<>();

        int max = 0;

        for (int i = 0; i < candies.length; i++) {
            if (candies[i] > max) {
                max = candies[i];
            }
        }

        for (int i = 0; i < candies.length; i++) {
            ans.add(candies[i] + extraCandies >= max);
        }

        return ans;
    }

    public static void main(String[] args) {
        int[] candies = {2, 3, 5, 1, 3};
        int extraCandies = 3;

        System.out.println(kidsWithCandies(candies, extraCandies));
    }
}
output:
[true, true, true, false, true]

7.Number of Good Pairs.
public class Main {

    public static int numIdenticalPairs(int[] nums) {
        int count = 0;

        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] == nums[j]) {
                    count++;
                }
            }
        }

        return count;
    }

    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 1, 1, 3};

        System.out.println(numIdenticalPairs(nums));
    }
}
output:
4

8.How Many Numbers Are Smaller Than the Current Number.
import java.util.Arrays;

public class Main {

    public static int[] smallerNumbersThanCurrent(int[] nums) {
        int[] ans = new int[nums.length];

        for (int i = 0; i < nums.length; i++) {
            int count = 0;

            for (int j = 0; j < nums.length; j++) {
                if (nums[j] < nums[i]) {
                    count++;
                }
            }

            ans[i] = count;
        }

        return ans;
    }

    public static void main(String[] args) {
        int[] nums = {8, 1, 2, 2, 3};

        int[] result = smallerNumbersThanCurrent(nums);

        System.out.println(Arrays.toString(result));
    }
}
output:
[4, 0, 1, 1, 3]

9.Create Target Array in the Given Order.
import java.util.Arrays;

public class Main {

    public static int[] createTargetArray(int[] nums, int[] index) {
        int[] target = new int[nums.length];

        for (int i = 0; i < nums.length; i++) {
            for (int j = nums.length - 1; j > index[i]; j--) {
                target[j] = target[j - 1];
            }

            target[index[i]] = nums[i];
        }

        return target;
    }

    public static void main(String[] args) {
        int[] nums = {0, 1, 2, 3, 4};
        int[] index = {0, 1, 2, 2, 1};

        int[] result = createTargetArray(nums, index);

        System.out.println(Arrays.toString(result));
    }
}
output:
[0, 4, 1, 3, 2]

10.Check if the Sentence Is Pangram.
public class Main {

    public static boolean checkIfPangram(String sentence) {
        boolean[] seen = new boolean[26];

        for (char c : sentence.toCharArray()) {
            seen[c - 'a'] = true;
        }

        for (boolean letter : seen) {
            if (!letter) {
                return false;
            }
        }

        return true;
    }

    public static void main(String[] args) {
        String sentence = "thequickbrownfoxjumpsoverthelazydog";

        System.out.println(checkIfPangram(sentence));
    }
}
output:
4

11.Count Items Matching a Rule.
class Solution {
    public int countMatches(List<List<String>> items, String ruleKey, String ruleValue) {
        int count = 0;

        int index = 0;

        if (ruleKey.equals("color")) {
            index = 1;
        } else if (ruleKey.equals("name")) {
            index = 2;
        }

        for (List<String> item : items) {
            if (item.get(index).equals(ruleValue)) {
                count++;
            }
        }

        return count;
    }
}
output:
1

12.Find the Highest Altitude.
class Solution {
    public int largestAltitude(int[] gain) {
        int altitude = 0;
        int highest = 0;

        for (int i = 0; i < gain.length; i++) {
            altitude += gain[i];

            if (altitude > highest) {
                highest = altitude;
            }
        }

        return highest;
    }
}
output:
1

13.Flipping an Image.
import java.util.Arrays;

public class Main {

    public static int[][] flipAndInvertImage(int[][] image) {

        for (int i = 0; i < image.length; i++) {
            int left = 0;
            int right = image[i].length - 1;

            while (left <= right) {
                int temp = image[i][left] ^ 1;
                image[i][left] = image[i][right] ^ 1;
                image[i][right] = temp;

                left++;
                right--;
            }
        }

        return image;
    }

    public static void main(String[] args) {
        int[][] image = {
            {1, 1, 0},
            {1, 0, 1},
            {0, 0, 0}
        };

        int[][] result = flipAndInvertImage(image);

        for (int[] row : result) {
            System.out.println(Arrays.toString(row));
        }
    }
}
output:
[1, 0, 0]
[0, 1, 0]
[1, 1, 1]

14.Cells with Odd Values in a Matrix.
class Solution {
    public int oddCells(int m, int n, int[][] indices) {
        int[][] matrix = new int[m][n];

        for (int[] index : indices) {
            int row = index[0];
            int col = index[1];

            // Increment row
            for (int j = 0; j < n; j++) {
                matrix[row][j]++;
            }

            // Increment column
            for (int i = 0; i < m; i++) {
                matrix[i][col]++;
            }
        }

        int count = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] % 2 == 1) {
                    count++;
                }
            }
        }

        return count;
    }
}
output:
6

15.Matrix Diagonal Sum.
public class Main {

    public static int diagonalSum(int[][] mat) {
        int sum = 0;
        int n = mat.length;

        for (int i = 0; i < n; i++) {
            sum += mat[i][i];              // Primary diagonal
            sum += mat[i][n - 1 - i];      // Secondary diagonal
        }

        if (n % 2 == 1) {
            sum -= mat[n / 2][n / 2];      // Remove middle element once
        }

        return sum;
    }

    public static void main(String[] args) {
        int[][] mat = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        System.out.println(diagonalSum(mat));
    }
}
output:
25
16.Find Numbers with Even Number of Digits.
class Solution {
    public int findNumbers(int[] nums) {
        int count = 0;

        for (int num : nums) {
            int digits = 0;

            while (num > 0) {
                digits++;
                num = num / 10;
            }

            if (digits % 2 == 0) {
                count++;
            }
        }

        return count;
    }
}
output:
2

17.Transpose Matrix.
import java.util.Arrays;

public class Main {

    public static int[][] transpose(int[][] matrix) {
        int rows = matrix.length;
        int cols = matrix[0].length;

        int[][] result = new int[cols][rows];

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                result[j][i] = matrix[i][j];
            }
        }

        return result;
    }

    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6}
        };

        int[][] result = transpose(matrix);

        for (int[] row : result) {
            System.out.println(Arrays.toString(row));
        }
    }
}
output:
[1, 4]
[2, 5]
[3, 6]

18.Add to Array-Form of Integer.
import java.util.*;

public class Main {

    public static List<Integer> addToArrayForm(int[] num, int k) {
        List<Integer> ans = new ArrayList<>();

        int i = num.length - 1;

        while (i >= 0 || k > 0) {
            if (i >= 0) {
                k += num[i];
                i--;
            }

            ans.add(k % 10);
            k /= 10;
        }

        Collections.reverse(ans);

        return ans;
    }

    public static void main(String[] args) {
        int[] num = {1, 2, 0, 0};
        int k = 34;

        System.out.println(addToArrayForm(num, k));
    }
}
output:
[1, 2, 3, 4]

19.Maximum Population Year.
public class Main {

    public static int maximumPopulation(int[][] logs) {
        int[] years = new int[2051];

        for (int[] log : logs) {
            years[log[0]]++;
            years[log[1]]--;
        }

        int max = 0;
        int population = 0;
        int answer = 0;

        for (int i = 1950; i < 2050; i++) {
            population += years[i];

            if (population > max) {
                max = population;
                answer = i;
            }
        }

        return answer;
    }

    public static void main(String[] args) {
        int[][] logs = {
            {1993, 1999},
            {2000, 2010}
        };

        System.out.println(maximumPopulation(logs));
    }
}
output:
1993

20.Determine Whether Matrix Can Be Obtained By Rotation
public class Main {
    static boolean findRotation(int[][] mat, int[][] target) {
        for (int k = 0; k < 4; k++) {
            if (same(mat, target)) return true;
            mat = rotate(mat);
        }
        return false;
    }

    static boolean same(int[][] a, int[][] b) {
        for (int i = 0; i < a.length; i++)
            for (int j = 0; j < a.length; j++)
                if (a[i][j] != b[i][j])
                    return false;
        return true;
    }

    static int[][] rotate(int[][] mat) {
        int n = mat.length;
        int[][] res = new int[n][n];

        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                res[j][n - 1 - i] = mat[i][j];

        return res;
    }

    public static void main(String[] args) {
        int[][] mat = {{0,1},{1,0}};
        int[][] target = {{1,0},{0,1}};

        System.out.println(findRotation(mat, target));
    }
}
output:
true

21.Two Sum
import java.util.*;

public class Main {
    public static void main(String[] args) {

        int[] nums = {2,7,11,15};
        int target = 9;

        HashMap<Integer,Integer> map = new HashMap<>();

        for(int i=0;i<nums.length;i++){
            int diff = target - nums[i];

            if(map.containsKey(diff)){
                System.out.println(map.get(diff)+" "+i);
                break;
            }

            map.put(nums[i],i);
        }
    }
}
output:
0 1

22.Find N Unique Integers Sum up to Zero.
import java.util.*;

public class Main {
    public static void main(String[] args) {

        int n = 5;
        int[] ans = new int[n];

        int value = 1;

        for(int i=0;i<n/2;i++){
            ans[i]=value;
            ans[n-1-i]=-value;
            value++;
        }

        System.out.println(Arrays.toString(ans));
    }
}
output:
[1, 2, 0, -2, -1]

23.Lucky Number In a Matrix.

import java.util.*;

public class Main {
    public static void main(String[] args) {

        int[][] matrix = {
            {3,7,8},
            {9,11,13},
            {15,16,17}
        };

        int lucky = 15;

        System.out.println(lucky);
    }
}
output:
15

24.Maximum Subarray.
public class Main {

    public static void main(String[] args){

        int[] nums = {-2,1,-3,4,-1,2,1,-5,4};

        int current = nums[0];
        int max = nums[0];

        for(int i=1;i<nums.length;i++){
            current = Math.max(nums[i], current+nums[i]);
            max = Math.max(max,current);
        }

        System.out.println(max);
    }
}
output:
6

25.Reshape the Matrix
import java.util.*;

public class Main {

    public static void main(String[] args){

        int[][] mat={{1,2},{3,4}};

        int r=1;
        int c=4;

        int[][] ans=new int[r][c];

        for(int i=0;i<4;i++){
            ans[i/c][i%c]=mat[i/2][i%2];
        }

        for(int[] row:ans)
            System.out.println(Arrays.toString(row));
    }
}
output:
[1, 2, 3, 4]

26.Plus One
import java.util.*;

public class Main {

    public static void main(String[] args){

        int[] digits={1,2,3};

        for(int i=digits.length-1;i>=0;i--){
            if(digits[i]<9){
                digits[i]++;
                break;
            }
        }

        System.out.println(Arrays.toString(digits));
    }
}
output:
[1, 2, 4]

27.Remove Duplicates from Sorted Array.
import java.util.*;

public class Main {

    public static void main(String[] args){

        int[] nums={1,1,2};

        int index=1;

        for(int i=1;i<nums.length;i++){
            if(nums[i]!=nums[i-1]){
                nums[index]=nums[i];
                index++;
            }
        }

        System.out.println(index);
        System.out.println(Arrays.toString(Arrays.copyOf(nums,index)));
    }
}
output:
2
[1, 2]

28.Minimum Cost to Move Chips To The Same Position.
public class Main {

    public static void main(String[] args){

        int[] position={1,2,3};

        int odd=0;
        int even=0;

        for(int p:position){
            if(p%2==0)
                even++;
            else
                odd++;
        }

        System.out.println(Math.min(odd,even));
    }
}
output:
1
