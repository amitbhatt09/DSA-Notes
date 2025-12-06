# DSA-Notes

## Arrays
1-Rotating array left by k position
class Main {
    public static void reverseArray(int []arr, int start, int end){
        while(start<end){
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }
    public static void main(String[] args) {
        int arr[]= {1,2,3,4,5,6};
        int k = 2;
        
        reverseArray(arr,0,k-1);
        reverseArray(arr,k,arr.length-1);
        reverseArray(arr, 0, arr.length-1);
        for(int i=0; i<arr.length; i++){
            System.out.print(arr[i]+" ");
        }
    }
}
right by k position
 k = k % n;

        reverse(arr, 0, n-1);     // Step 1: reverse whole array
        reverse(arr, 0, k-1);     // Step 2: reverse first k
        reverse(arr, k, n-1);   // Step 3: reverse remaining
2- Group valid anagrams LC-49
Input: strs = ["eat","tea","tan","ate","nat","bat"]

Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String, List<String>> map = new HashMap<>();

        for(String s: strs){
            char arr[] = s.toCharArray();
            Arrays.sort(arr);

            map.putIfAbsent(key,new ArrayList<>());
            map.get(key).add(s);
        }
        return new ArrayLlist<>(map.values());

         
    }
}

3- Top K  frequent LC-347

class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        
        // Step 1: Count frequency
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int n : nums) {
            map.put(n, map.getOrDefault(n, 0) + 1);
        }

        // Step 2: Convert map entries to a list
        List<Map.Entry<Integer, Integer>> list = new ArrayList<>(map.entrySet());

        // Step 3: Sort list by frequency (descending)
        Collections.sort(list, (a, b) -> b.getValue() - a.getValue());

        // Step 4: Pick first k elements
        int[] result = new int[k];
        for (int i = 0; i < k; i++) {
            result[i] = list.get(i).getKey();
        }

        return result;
    }
}
