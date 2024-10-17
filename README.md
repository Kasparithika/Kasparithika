import java.util.Scanner;

public class BestBubble {
    
    // Function to count swaps for Bubble Sort in the given order
    public static int countSwaps(int[] arr, String order) {
        int swaps = 0;
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if ((order.equals("asc") && arr[j] > arr[j + 1]) || 
                    (order.equals("desc") && arr[j] < arr[j + 1])) {
                    // Swap adjacent elements
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swaps++;
                }
            }
        }
        return swaps;
    }
    
    // Function to find minimum swaps to make array beautiful
    public static int minimumSwapsToBeautiful(int[] arr) {
        // Make copies of the original array for both sorting orders
        int[] arrAsc = arr.clone();
        int[] arrDesc = arr.clone();
        
        // Calculate number of swaps for ascending order
        int ascSwaps = countSwaps(arrAsc, "asc");
        
        // Calculate number of swaps for descending order
        int descSwaps = countSwaps(arrDesc, "desc");
        
        // Return the minimum of the two
        return Math.min(ascSwaps, descSwaps);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Read number of elements
        int n = scanner.nextInt();
        
        // Read array elements
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }
        
        // Output the minimum number of swaps required
        System.out.println(minimumSwapsToBeautiful(arr));
        
        scanner.close();
    }
}
