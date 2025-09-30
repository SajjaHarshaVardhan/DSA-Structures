# DSA-Structures
# 📘 Data Structures and Algorithms in Java

This repository contains **Data Structures and Algorithms (DSA)** implementations in **Java** with explanations and examples.
It is designed for beginners and intermediate learners preparing for **interviews, competitive programming, or academic purposes**.

---

## 📂 Table of Contents

1. [Introduction](#introduction)
2. [Arrays](#arrays)
3. [Strings](#strings)
4. [Linked List](#linked-list)
5. [Stacks](#stacks)
6. [Queues](#queues)
7. [Recursion](#recursion)
8. [Sorting Algorithms](#sorting-algorithms)
9. [Searching Algorithms](#searching-algorithms)
10. [Trees](#trees)
11. [Graphs](#graphs)
12. [Dynamic Programming](#dynamic-programming)
13. [Greedy Algorithms](#greedy-algorithms)
14. [Backtracking](#backtracking)
15. [Complexity Analysis](#complexity-analysis)

---

## 🚀 Introduction

A **Data Structure** is a way of organizing data efficiently.
An **Algorithm** is a step-by-step procedure to solve a problem.
Together, DSA helps in writing **optimized, scalable, and efficient programs**.

---

## 🔹 Arrays

### Example: Reverse an Array

```java
public class ReverseArray {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        int n = arr.length;

        for (int i = 0; i < n / 2; i++) {
            int temp = arr[i];
            arr[i] = arr[n - i - 1];
            arr[n - i - 1] = temp;
        }

        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

---

## 🔹 Strings

### Example: Check Palindrome

```java
public class PalindromeString {
    public static void main(String[] args) {
        String str = "madam";
        String rev = "";

        for (int i = str.length() - 1; i >= 0; i--) {
            rev += str.charAt(i);
        }

        if (str.equals(rev)) {
            System.out.println("Palindrome");
        } else {
            System.out.println("Not Palindrome");
        }
    }
}
```

---

## 🔹 Linked List

### Example: Singly Linked List Implementation

```java
class Node {
    int data;
    Node next;
    Node(int d) { data = d; next = null; }
}

public class LinkedList {
    Node head;

    public void insert(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node temp = head;
        while (temp.next != null) temp = temp.next;
        temp.next = newNode;
    }

    public void printList() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
    }

    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.insert(10);
        list.insert(20);
        list.insert(30);
        list.printList();
    }
}
```

---

## 🔹 Stack

### Example: Stack using Array

```java
class Stack {
    int arr[];
    int top;
    int capacity;

    Stack(int size) {
        arr = new int[size];
        capacity = size;
        top = -1;
    }

    void push(int x) {
        if (top == capacity - 1) {
            System.out.println("Stack Overflow");
            return;
        }
        arr[++top] = x;
    }

    int pop() {
        if (top == -1) {
            System.out.println("Stack Underflow");
            return -1;
        }
        return arr[top--];
    }

    public static void main(String[] args) {
        Stack stack = new Stack(5);
        stack.push(10);
        stack.push(20);
        System.out.println(stack.pop()); // 20
    }
}
```

---

## 🔹 Queue

### Example: Queue using Array

```java
class Queue {
    int arr[], front, rear, capacity, count;

    Queue(int size) {
        arr = new int[size];
        capacity = size;
        front = 0;
        rear = -1;
        count = 0;
    }

    void enqueue(int x) {
        if (count == capacity) {
            System.out.println("Queue Full");
            return;
        }
        rear = (rear + 1) % capacity;
        arr[rear] = x;
        count++;
    }

    int dequeue() {
        if (count == 0) {
            System.out.println("Queue Empty");
            return -1;
        }
        int item = arr[front];
        front = (front + 1) % capacity;
        count--;
        return item;
    }

    public static void main(String[] args) {
        Queue q = new Queue(5);
        q.enqueue(1);
        q.enqueue(2);
        System.out.println(q.dequeue()); // 1
    }
}
```

---

## 🔹 Sorting Algorithms

* **Bubble Sort**
* **Selection Sort**
* **Insertion Sort**
* **Merge Sort**
* **Quick Sort**

### Example: Bubble Sort

```java
public class BubbleSort {
    public static void main(String[] args) {
        int[] arr = {5, 4, 3, 2, 1};
        int n = arr.length;

        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }

        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

---

## 🔹 Searching Algorithms

### Example: Binary Search

```java
public class BinarySearch {
    public static int binarySearch(int arr[], int x) {
        int left = 0, right = arr.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == x)
                return mid;
            if (arr[mid] < x)
                left = mid + 1;
            else
                right = mid - 1;
        }
        return -1;
    }

    public static void main(String[] args) {
        int arr[] = {1, 2, 3, 4, 5};
        int result = binarySearch(arr, 3);
        System.out.println(result == -1 ? "Not Found" : "Found at index " + result);
    }
}
```

---

## 🔹 Trees

### Example: Binary Tree Traversal

```java
class Node {
    int data;
    Node left, right;
    Node(int d) { data = d; left = right = null; }
}

public class BinaryTree {
    Node root;

    void inorder(Node node) {
        if (node == null) return;
        inorder(node.left);
        System.out.print(node.data + " ");
        inorder(node.right);
    }

    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();
        tree.root = new Node(1);
        tree.root.left = new Node(2);
        tree.root.right = new Node(3);
        tree.root.left.left = new Node(4);
        tree.root.left.right = new Node(5);

        tree.inorder(tree.root); // 4 2 5 1 3
    }
}
```

---

## 🔹 Graphs

### Example: BFS Traversal

```java
import java.util.*;

public class BFS {
    private int V;
    private LinkedList<Integer> adj[];

    BFS(int v) {
        V = v;
        adj = new LinkedList[v];
        for (int i = 0; i < v; i++)
            adj[i] = new LinkedList<>();
    }

    void addEdge(int v, int w) { adj[v].add(w); }

    void bfs(int s) {
        boolean visited[] = new boolean[V];
        Queue<Integer> queue = new LinkedList<>();

        visited[s] = true;
        queue.add(s);

        while (!queue.isEmpty()) {
            int node = queue.poll();
            System.out.print(node + " ");
            for (int n : adj[node]) {
                if (!visited[n]) {
                    visited[n] = true;
                    queue.add(n);
                }
            }
        }
    }

    public static void main(String[] args) {
        BFS g = new BFS(4);
        g.addEdge(0, 1);
        g.addEdge(0, 2);
        g.addEdge(1, 2);
        g.addEdge(2, 0);
        g.addEdge(2, 3);
        g.addEdge(3, 3);

        g.bfs(2); // 2 0 3 1
    }
}
```

---

## 🔹 Dynamic Programming

### Example: Fibonacci with DP

```java
public class FibonacciDP {
    public static int fib(int n) {
        int dp[] = new int[n + 1];
        dp[0] = 0; dp[1] = 1;
        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        return dp[n];
    }

    public static void main(String[] args) {
        System.out.println(fib(10)); // 55
    }
}
```

---

## 🔹 Greedy Algorithms

### Example: Activity Selection Problem

```java
import java.util.*;

public class ActivitySelection {
    public static void main(String[] args) {
        int start[] = {1, 3, 0, 5, 8, 5};
        int end[] =   {2, 4, 6, 7, 9, 9};

        int n = start.length;
        int lastEnd = -1;
        System.out.println("Selected Activities:");

        for (int i = 0; i < n; i++) {
            if (start[i] >= lastEnd) {
                System.out.println("(" + start[i] + "," + end[i] + ")");
                lastEnd = end[i];
            }
        }
    }
}
```

---

## 🔹 Backtracking

### Example: N-Queens Problem

```java
public class NQueens {
    static final int N = 4;

    static void printBoard(int board[][]) {
        for (int[] row : board) {
            for (int col : row) {
                System.out.print(col + " ");
            }
            System.out.println();
        }
        System.out.println();
    }

    static boolean isSafe(int board[][], int row, int col) {
        for (int i = 0; i < row; i++)
            if (board[i][col] == 1) return false;

        for (int i=row, j=col; i>=0 && j>=0; i--, j--)
            if (board[i][j] == 1) return false;

        for (int i=row, j=col; i>=0 && j<N; i--, j++)
            if (board[i][j] == 1) return false;

        return true;
    }

    static boolean solveNQ(int board[][], int row) {
        if (row >= N) {
            printBoard(board);
            return true;
        }

        boolean res = false;
        for (int i = 0; i < N; i++) {
            if (isSafe(board, row, i)) {
                board[row][i] = 1;
                res = solveNQ(board, row + 1) || res;
                board[row][i] = 0;
            }
        }
        return res;
    }

    public static void main(String[] args) {
        int board[][] = new int[N][N];
        solveNQ(board, 0);
    }
}
```

---

## 🔹 Complexity Analysis

* **Time Complexity**: How execution time increases with input size.
* **Space Complexity**: How much memory an algorithm uses.
* Common complexities:

  * Constant → `O(1)`
  * Logarithmic → `O(log n)`
  * Linear → `O(n)`
  * Linearithmic → `O(n log n)`
  * Quadratic → `O(n²)`
  * Exponential → `O(2^n)`

---

## 📌 Conclusion

This repository covers the **most important Data Structures and Algorithms in Java**.
Each topic has **theory + Java code** for clarity.

👉 You can extend this repo by adding **more advanced algorithms** like:

* Dijkstra’s Algorithm
* Kruskal’s Algorithm
* Bellman-Ford Algorithm
* KMP String Matching
* Segment Trees
* Trie Data Structure

---

💡 *Happy Coding!* 🚀
