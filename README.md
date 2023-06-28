# UnibitCoding
import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        int[] nums = {1, 3, 2, 2, -4, -6, -2, 8};
        int target = 4;

        List<List<Integer>> firstCombination = findCombination(nums, target);
        int[] mergedArray = mergeAndSort(nums);
        int doubledTarget = target * 2;
        List<List<Integer>> secondCombination = findCombination(mergedArray, doubledTarget);

        System.out.println("First Combination For " + target + " : " + firstCombination);
        System.out.println("Merge Into a Single Array: " + Arrays.toString(mergedArray));
        System.out.println("Second Combination For " + doubledTarget + " : " + secondCombination);
    }

    public static List<List<Integer>> findCombination(int[] nums, int target) {
        List<List<Integer>> result = new ArrayList<>();
        Map<Integer, Integer> complementMap = new HashMap<>();

        for (int num : nums) {
            int complement = target - num;
            if (complementMap.containsKey(complement)) {
                result.add(Arrays.asList(num, complement));
            } else {
                complementMap.put(num, 1);
            }
        }

        return result;
    }

    public static int[] mergeAndSort(int[] nums) {
        int[] mergedArray = new int[nums.length];
        System.arraycopy(nums, 0, mergedArray, 0, nums.length);
        Arrays.sort(mergedArray);
        return mergedArray;
    }
}
