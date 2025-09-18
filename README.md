# java
1-REVERSE STRING
import java.util.Scanner;

public class Main {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        String str = sc.nextLine();   // input string
        String rev = new StringBuilder(str).reverse().toString();
        System.out.println(rev);
    }
}
2. Find the Maximum and Minimum Element in an Array
Input: [3, 5, 1, 8, -2]
Output: Max = 8, Min = -2


import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        int[] arr = {3, 5, 1, 8, -2};
        int max = arr[0];
        int min = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
            if (arr[i] < min) {
                min = arr[i];
            }
        }
        System.out.println("Max = " + max + ", Min = " + min);
    }
}

3. Find the Kth Maximum and Minimum Element of an Array
Input: [7, 10, 4, 3, 20, 15], k = 3
Output: 3rd Min = 7, 3rd Max = 10

import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] arr = {7, 10, 4, 3, 20, 15};
        int k = 3;
        Arrays.sort(arr);
        int kthMin = arr[k - 1];
        int kthMax = arr[arr.length - k];
        System.out.println(k + "rd Min = " + kthMin + ", " + k + "rd Max = " + kthMax);
    }
}

 4. Sort 0s, 1s, 2s 
Input: [0, 2, 1, 2, 0]
Output: [0, 0, 1, 2, 2]

import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] arr = {0, 2, 1, 2, 0};
        int low = 0, mid = 0, high = arr.length - 1;
        while (mid <= high) {
            switch (arr[mid]) {
                case 0:
                    int temp0 = arr[low];
                    arr[low] = arr[mid];
                    arr[mid] = temp0;
                    low++;
                    mid++;
                    break;
                case 1:
                    mid++;
                    break;
                case 2:
                    int temp2 = arr[mid];
                    arr[mid] = arr[high];
                    arr[high] = temp2;
                    high--;
                    break;
            }
        }
        System.out.println(Arrays.toString(arr));
    }
}

5. Move All Negative Elements to One Side
Input: [1, -1, 3, 2, -7, -5, 11, 6]
Output: [-1, -7, -5, 1, 3, 2, 11, 6] (any order with all negatives on one side is fine)

import java.util.Arrays;
public class Main {
    public static void main(String[] args) {
        int[] arr = {1, -1, 3, 2, -7, -5, 11, 6};
        int j = 0; 
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] < 0) {
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
                j++;
            }
        }
        System.out.println(Arrays.toString(arr));
    }
}

6. Find Union and Intersection of Two Sorted Arrays
Input: arr1 = [1, 2, 4, 5], arr2 = [2, 3, 5, 6]
Output: Union = [1, 2, 3, 4, 5, 6]
Intersection = [2, 5]

import java.util.*;
public class Main {
    public static void main(String[] args) {
        int[] arr1 = {1, 2, 4, 5};
        int[] arr2 = {2, 3, 5, 6};
        Set<Integer> union = new TreeSet<>();
        Set<Integer> intersection = new TreeSet<>();
        for (int x : arr1) union.add(x);
        for (int x : arr2) {
            if (union.contains(x)) intersection.add(x);
            union.add(x);
        }
        System.out.println("Union = " + union);
        System.out.println("Intersection = " + intersection);
    }
}

7. Cyclically Rotate an Array by One
Input: [1, 2, 3, 4, 5]
Output: [5, 1, 2, 3, 4]

import java.util.Arrays;
public class Main {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        int last = arr[arr.length - 1];
        for (int i = arr.length - 1; i > 0; i--) {
            arr[i] = arr[i - 1];
        }
        arr[0] = last;
        System.out.println(Arrays.toString(arr));
    }
}

8. Largest Sum Contiguous Subarray (Kadane’s Algorithm)
Input: [-2, -3, 4, -1, -2, 1, 5, -3]
Output: Max Sum = 7 (Subarray: [4, -1, -2, 1, 5])


public class Main {
    public static void main(String[] args) {
        int[] arr = {-2, -3, 4, -1, -2, 1, 5, -3};

        int maxSoFar = arr[0];
        int maxEndingHere = arr[0];

        for (int i = 1; i < arr.length; i++) {
            maxEndingHere = Math.max(arr[i], maxEndingHere + arr[i]);
            maxSoFar = Math.max(maxSoFar, maxEndingHere);
        }

        System.out.println("Max Sum = " + maxSoFar);
    }
}
