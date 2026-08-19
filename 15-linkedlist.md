1. Reverse Nodes in k-Group.
  class ReverseKGroup {

    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    // Reverse nodes in groups of k
    static Node reverseKGroup(Node head, int k) {

        if (head == null || k == 1) {
            return head;
        }

        // Check if k nodes are available
        Node temp = head;

        for (int i = 0; i < k; i++) {
            if (temp == null) {
                return head;
            }
            temp = temp.next;
        }

        // Reverse k nodes
        Node prev = null;
        Node current = head;

        for (int i = 0; i < k; i++) {
            Node next = current.next;
            current.next = prev;
            prev = current;
            current = next;
        }

        // Reverse remaining groups
        head.next = reverseKGroup(current, k);

        return prev;
    }

    // Display
    static void display(Node head) {

        Node temp = head;

        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }

        System.out.println();
    }

    public static void main(String[] args) {

        Node head = new Node(32);
        head.next = new Node(45);
        head.next.next = new Node(78);
        head.next.next.next = new Node(93);
        head.next.next.next.next = new Node(56);

        int k = 2;

        System.out.println("Original List:");
        display(head);

        head = reverseKGroup(head, k);

        System.out.println("After Reverse in k-Group:");
        display(head);
    }
}
output:
Original List:
32 45 78 93 56 
After Reverse in k-Group:
45 32 93 78 56

   2.Design Skiplist
   import java.util.Random;

class Skiplist {

    private static final int MAX_LEVEL = 32;
    private static final double P = 0.25;

    private static class Node {
        int val;
        Node[] next;

        Node(int val, int level) {
            this.val = val;
            this.next = new Node[level];
        }
    }

    private final Node head = new Node(-1, MAX_LEVEL);
    private int level = 0;
    private final Random random = new Random();

    // Search
    public boolean search(int target) {

        Node current = head;

        for (int i = level - 1; i >= 0; i--) {

            while (current.next[i] != null &&
                   current.next[i].val < target) {
                current = current.next[i];
            }
        }

        current = current.next[0];

        return current != null && current.val == target;
    }

    // Add
    public void add(int num) {

        Node[] update = new Node[MAX_LEVEL];
        Node current = head;

        for (int i = level - 1; i >= 0; i--) {

            while (current.next[i] != null &&
                   current.next[i].val < num) {
                current = current.next[i];
            }

            update[i] = current;
        }

        int newLevel = randomLevel();

        if (newLevel > level) {

            for (int i = level; i < newLevel; i++) {
                update[i] = head;
            }

            level = newLevel;
        }

        Node newNode = new Node(num, newLevel);

        for (int i = 0; i < newLevel; i++) {

            newNode.next[i] = update[i].next[i];
            update[i].next[i] = newNode;
        }
    }

    // Erase
    public boolean erase(int num) {

        Node[] update = new Node[MAX_LEVEL];
        Node current = head;

        for (int i = level - 1; i >= 0; i--) {

            while (current.next[i] != null &&
                   current.next[i].val < num) {
                current = current.next[i];
            }

            update[i] = current;
        }

        current = current.next[0];

        if (current == null || current.val != num) {
            return false;
        }

        for (int i = 0; i < level; i++) {

            if (update[i].next[i] != current) {
                break;
            }

            update[i].next[i] = current.next[i];
        }

        while (level > 0 && head.next[level - 1] == null) {
            level--;
        }

        return true;
    }

    // Generate random level
    private int randomLevel() {

        int newLevel = 1;

        while (newLevel < MAX_LEVEL &&
               random.nextDouble() < P) {
            newLevel++;
        }

        return newLevel;
    }

    // Main method for testing
    public static void main(String[] args) {

        Skiplist skiplist = new Skiplist();

        skiplist.add(32);
        skiplist.add(45);
        skiplist.add(78);
        skiplist.add(93);
        skiplist.add(56);

        System.out.println("Search 78: " +
                skiplist.search(78));

        System.out.println("Search 100: " +
                skiplist.search(100));

        System.out.println("Erase 78: " +
                skiplist.erase(78));

        System.out.println("Search 78 after erase: " +
                skiplist.search(78));
    }
}
output:
Search 78: true
Search 100: false
Erase 78: true
Search 78 after erase: false

3.LFU Cache 
import java.util.*;

class LFUCache {

    class Node {
        int key;
        int value;
        int frequency;

        Node(int key, int value) {
            this.key = key;
            this.value = value;
            this.frequency = 1;
        }
    }

    int capacity;
    int minFrequency;

    HashMap<Integer, Node> cache;
    HashMap<Integer, LinkedHashSet<Integer>> frequencyMap;

    public LFUCache(int capacity) {
        this.capacity = capacity;
        this.minFrequency = 0;

        cache = new HashMap<>();
        frequencyMap = new HashMap<>();
    }

    // Get value
    public int get(int key) {

        if (!cache.containsKey(key)) {
            return -1;
        }

        Node node = cache.get(key);

        increaseFrequency(node);

        return node.value;
    }

    // Insert or update value
    public void put(int key, int value) {

        if (capacity == 0) {
            return;
        }

        // Key already exists
        if (cache.containsKey(key)) {

            Node node = cache.get(key);

            node.value = value;

            increaseFrequency(node);

            return;
        }

        // Cache is full
        if (cache.size() == capacity) {

            LinkedHashSet<Integer> set =
                frequencyMap.get(minFrequency);

            int removeKey = set.iterator().next();

            set.remove(removeKey);

            cache.remove(removeKey);

            if (set.isEmpty()) {
                frequencyMap.remove(minFrequency);
            }
        }

        // Add new node
        Node newNode = new Node(key, value);

        cache.put(key, newNode);

        minFrequency = 1;

        frequencyMap
            .computeIfAbsent(1, k -> new LinkedHashSet<>())
            .add(key);
    }

    // Increase frequency
    private void increaseFrequency(Node node) {

        int oldFrequency = node.frequency;

        LinkedHashSet<Integer> oldSet =
            frequencyMap.get(oldFrequency);

        oldSet.remove(node.key);

        if (oldSet.isEmpty()) {

            frequencyMap.remove(oldFrequency);

            if (minFrequency == oldFrequency) {
                minFrequency++;
            }
        }

        node.frequency++;

        frequencyMap
            .computeIfAbsent(
                node.frequency,
                k -> new LinkedHashSet<>()
            )
            .add(node.key);
    }

    // Main method
    public static void main(String[] args) {

        LFUCache cache = new LFUCache(2);

        cache.put(1, 1);
        cache.put(2, 2);

        System.out.println(cache.get(1));

        cache.put(3, 3);

        System.out.println(cache.get(2));
        System.out.println(cache.get(3));

        cache.put(4, 4);

        System.out.println(cache.get(1));
        System.out.println(cache.get(3));
        System.out.println(cache.get(4));
    }
}
output:
1
-1
3
-1
3
4

4.Merge In Between Linked Lists.
class MergeInBetween {

    static class ListNode {
        int val;
        ListNode next;

        ListNode(int val) {
            this.val = val;
            this.next = null;
        }
    }

    static ListNode mergeInBetween(
            ListNode list1,
            int a,
            int b,
            ListNode list2) {

        // Node before a
        ListNode beforeA = list1;

        for (int i = 0; i < a - 1; i++) {
            beforeA = beforeA.next;
        }

        // Node after b
        ListNode afterB = beforeA;

        for (int i = 0; i < b - a + 2; i++) {
            afterB = afterB.next;
        }

        // Last node of list2
        ListNode last2 = list2;

        while (last2.next != null) {
            last2 = last2.next;
        }

        // Join lists
        beforeA.next = list2;
        last2.next = afterB;

        return list1;
    }

    static void display(ListNode head) {

        while (head != null) {
            System.out.print(head.val + " ");
            head = head.next;
        }

        System.out.println();
    }

    public static void main(String[] args) {

        // list1
        ListNode list1 = new ListNode(10);
        list1.next = new ListNode(20);
        list1.next.next = new ListNode(30);
        list1.next.next.next = new ListNode(40);
        list1.next.next.next.next = new ListNode(50);
        list1.next.next.next.next.next = new ListNode(60);

        // list2
        ListNode list2 = new ListNode(100);
        list2.next = new ListNode(200);
        list2.next.next = new ListNode(300);

        int a = 2;
        int b = 4;

        System.out.println("Original List1:");
        display(list1);

        System.out.println("List2:");
        display(list2);

        list1 = mergeInBetween(list1, a, b, list2);

        System.out.println("After Merge:");
        display(list1);
    }
}
output:
Original List1:
10 20 30 40 50 60 
List2:
100 200 300 
After Merge:
10 20 100 200 300 60 

5.Swap Nodes in Pairs.
class SwapNodesInPairs {

    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    static Node swapPairs(Node head) {

        Node dummy = new Node(0);
        dummy.next = head;

        Node previous = dummy;

        while (previous.next != null &&
               previous.next.next != null) {

            Node first = previous.next;
            Node second = first.next;

            // Swap the two nodes
            previous.next = second;
            first.next = second.next;
            second.next = first;

            // Move to the next pair
            previous = first;
        }

        return dummy.next;
    }

    static void display(Node head) {

        Node temp = head;

        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }

        System.out.println();
    }

    public static void main(String[] args) {

        Node head = new Node(32);
        head.next = new Node(45);
        head.next.next = new Node(78);
        head.next.next.next = new Node(93);
        head.next.next.next.next = new Node(56);

        System.out.println("Original List:");
        display(head);

        head = swapPairs(head);

        System.out.println("After Swapping Pairs:");
        display(head);
    }
}

output:
Original List:
32 45 78 93 56 
After Swapping Pairs:
45 32 93 78 56 

6.Swapping Nodes in a Linked List.
class SwappingNodes {

    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    static Node swapNodes(Node head, int k) {

        Node fast = head;

        // Find kth node from beginning
        for (int i = 1; i < k; i++) {
            fast = fast.next;
        }

        Node first = fast;

        // Find kth node from end
        Node slow = head;

        while (fast.next != null) {
            fast = fast.next;
            slow = slow.next;
        }

        Node second = slow;

        // Swap values
        int temp = first.data;
        first.data = second.data;
        second.data = temp;

        return head;
    }

    static void display(Node head) {

        Node temp = head;

        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }

        System.out.println();
    }

    public static void main(String[] args) {

        Node head = new Node(32);
        head.next = new Node(45);
        head.next.next = new Node(78);
        head.next.next.next = new Node(93);
        head.next.next.next.next = new Node(56);

        int k = 2;

        System.out.println("Original List:");
        display(head);

        head = swapNodes(head, k);

        System.out.println("After Swapping:");
        display(head);
    }
}
output:
Original List:
32 45 78 93 56 
After Swapping:
32 93 78 45 56 

7.Merge Two Sorted Lists.
class MergeTwoSortedLists {

    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    static Node merge(Node list1, Node list2) {

        Node dummy = new Node(0);
        Node current = dummy;

        while (list1 != null && list2 != null) {

            if (list1.data <= list2.data) {
                current.next = list1;
                list1 = list1.next;
            } else {
                current.next = list2;
                list2 = list2.next;
            }

            current = current.next;
        }

        // Add remaining nodes
        if (list1 != null) {
            current.next = list1;
        } else {
            current.next = list2;
        }

        return dummy.next;
    }

    static void display(Node head) {

        Node temp = head;

        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }

        System.out.println();
    }

    public static void main(String[] args) {

        // First sorted list
        Node list1 = new Node(32);
        list1.next = new Node(45);
        list1.next.next = new Node(78);
        list1.next.next.next = new Node(93);

        // Second sorted list
        Node list2 = new Node(34);
        list2.next = new Node(56);
        list2.next.next = new Node(80);
        list2.next.next.next = new Node(100);

        System.out.println("List 1:");
        display(list1);

        System.out.println("List 2:");
        display(list2);

        Node result = merge(list1, list2);

        System.out.println("Merged Sorted List:");
        display(result);
    }
}
output:
List 1:
32 45 78 93 
List 2:
34 56 80 100 
Merged Sorted List:
32 34 45 56 78 80 93 100 

8.Palindrome Linked List.
class PalindromeLinkedList {

    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    static boolean isPalindrome(Node head) {

        if (head == null || head.next == null) {
            return true;
        }

        // Find the middle
        Node slow = head;
        Node fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // Reverse second half
        Node previous = null;
        Node current = slow;

        while (current != null) {
            Node next = current.next;
            current.next = previous;
            previous = current;
            current = next;
        }

        // Compare both halves
        Node first = head;
        Node second = previous;

        while (second != null) {

            if (first.data != second.data) {
                return false;
            }

            first = first.next;
            second = second.next;
        }

        return true;
    }

    static void display(Node head) {

        Node temp = head;

        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }

        System.out.println();
    }

    public static void main(String[] args) {

        Node head = new Node(32);
        head.next = new Node(45);
        head.next.next = new Node(78);
        head.next.next.next = new Node(45);
        head.next.next.next.next = new Node(32);

        System.out.println("Linked List:");
        display(head);

        if (isPalindrome(head)) {
            System.out.println("Palindrome");
        } else {
            System.out.println("Not Palindrome");
        }
    }
}
output:
Linked List:
32 45 78 45 32 
Palindrome

9.Delete Node in a Linked List.
class DeleteNode {

    static class Node {
        int data;
        Node next;

        Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    // Delete the given node
    static void deleteNode(Node node) {

        node.data = node.next.data;
        node.next = node.next.next;
    }

    // Display linked list
    static void display(Node head) {

        Node temp = head;

        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }

        System.out.println();
    }

    public static void main(String[] args) {

        Node head = new Node(32);
        head.next = new Node(45);
        head.next.next = new Node(78);
        head.next.next.next = new Node(93);
        head.next.next.next.next = new Node(56);

        System.out.println("Original List:");
        display(head);

        // Delete node 78
        deleteNode(head.next.next);

        System.out.println("After Deletion:");
        display(head);
    }
}
output:
Original List:
32 45 78 93 56 
After Deletion:
32 45 93 56 
