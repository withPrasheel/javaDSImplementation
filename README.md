# javaDSImplementation

## LinkedList
```java
  public class LinkedList{
    static Node head;
    
    static class Node{
        int data;
        Node next;
        
        Node(int val)
        {
            data = val;
            next = null;
        }
    }
    
    public static void add(int val)
    {
        Node newNode = new Node(val);
        
        if(head==null)
        {
            head = newNode;    
        }
        else
        {
            Node temp = head;
            while(temp.next!=null)
            {
                temp = temp.next;
            }
            temp.next = newNode;
        }
    }
    
    public static void printList()
    {
        Node temp = head;
        while(temp.next!=null)
        {
            System.out.println(temp.data);
            temp = temp.next;
        }
    }
    
    
    public static void main(String []args){
        LinkedList ll = new LinkedList();
        for(int i=1;i<9;i++)
            ll.add(i);
        ll.printList();
    }
}
```

---------

## Stack using Linked List

```java
public class StackAsLinkedList{
    static StackNode root;
    
    static class StackNode{
        int data;
        StackNode next;
        
        StackNode(int val)
        {
            this.data = val;
            next = null;
        }
    }
    
    public static void push(int data)
    {
        StackNode newNode = new StackNode(data);
        if(root==null)
        {
            root = newNode;
        }
        else
        {
            newNode.next = root;
            root = newNode;
        }
    }
    
    public static int peek()
    {
        if(root==null)
        {
            System.out.println("Stack is Empty");
            return -1;
        }
        return root.data;
    }
    
    public static int pop()
    {
        if(root==null)
        {
            System.out.println("Stack is Empty");
            return -1;
        }
        int popped = root.data;
        root = root.next;
        return popped;
    }
    
    public static void main(String[] args)
    {
        StackAsLinkedList sll = new StackAsLinkedList();
        sll.push(1);
        sll.push(2);
        sll.pop();
        sll.push(20);
        sll.peek();
        sll.push(211);
        System.out.println(sll.peek());
    }
}
```
----------
## Stack using Array

```java
  class Stack {
    static final int MAX = 1000;
    int top;
    int a[] = new int[MAX]; // Maximum size of Stack
 
    boolean isEmpty()
    {
        return (top < 0);
    }
    Stack()
    {
        top = -1;
    }
 
    boolean push(int x)
    {
        if (top >= (MAX - 1)) {
            System.out.println("Stack Overflow");
            return false;
        }
        else {
            a[++top] = x;
            System.out.println(x + " pushed into stack");
            return true;
        }
    }
 
    int pop()
    {
        if (top < 0) {
            System.out.println("Stack Underflow");
            return 0;
        }
        else {
            int x = a[top--];
            return x;
        }
    }
 
    int peek()
    {
        if (top < 0) {
            System.out.println("Stack Underflow");
            return 0;
        }
        else {
            int x = a[top];
            return x;
        }
    }
}
 
// Driver code
class Main {
    public static void main(String args[])
    {
        Stack s = new Stack();
        s.push(10);
        s.push(20);
        s.push(30);
        System.out.println(s.pop() + " Popped from stack");
    }
}
```
---------------
## Queue using Array

```java
  class Queue {
    int front, rear, size;
    int capacity;
    int array[];
 
    public Queue(int capacity)
    {
        this.capacity = capacity;
        front = this.size = 0;
        rear = capacity - 1;
        array = new int[this.capacity];
    }
 
    // Queue is full when size becomes
    // equal to the capacity
    boolean isFull(Queue queue)
    {
        return (queue.size == queue.capacity);
    }
 
    // Queue is empty when size is 0
    boolean isEmpty(Queue queue)
    {
        return (queue.size == 0);
    }
 
    // Method to add an item to the queue.
    // It changes rear and size
    void enqueue(int item)
    {
        if (isFull(this))
            return;
        this.rear = (this.rear + 1)
                    % this.capacity;
        this.array[this.rear] = item;
        this.size = this.size + 1;
        System.out.println(item
                           + " enqueued to queue");
    }
 
    // Method to remove an item from queue.
    // It changes front and size
    int dequeue()
    {
        if (isEmpty(this))
            return Integer.MIN_VALUE;
 
        int item = this.array[this.front];
        this.front = (this.front + 1)
                     % this.capacity;
        this.size = this.size - 1;
        return item;
    }
 
    // Method to get front of queue
    int front()
    {
        if (isEmpty(this))
            return Integer.MIN_VALUE;
 
        return this.array[this.front];
    }
 
    // Method to get rear of queue
    int rear()
    {
        if (isEmpty(this))
            return Integer.MIN_VALUE;
 
        return this.array[this.rear];
    }
}
 
// Driver class
public class Test {
    public static void main(String[] args)
    {
        Queue queue = new Queue(1000);
 
        queue.enqueue(10);
        queue.enqueue(20);
        queue.enqueue(30);
        queue.enqueue(40);
 
        System.out.println(queue.dequeue()
                           + " dequeued from queue\n");
 
        System.out.println("Front item is "
                           + queue.front());
 
        System.out.println("Rear item is "
                           + queue.rear());
    }
}
```
-------
## Binary Tree

```java
  class Node
{
    int key;
    Node left, right;
 
    public Node(int item)
    {
        key = item;
        left = right = null;
    }
}
 
// A Java program to introduce Binary Tree
class BinaryTree
{
    // Root of Binary Tree
    Node root;
 
    // Constructors
    BinaryTree(int key)
    {
        root = new Node(key);
    }
 
    BinaryTree()
    {
        root = null;
    }
 
    public static void main(String[] args)
    {
        BinaryTree tree = new BinaryTree();
 
        /*create root*/
        tree.root = new Node(1);
 
        /* following is the tree after above statement
 
              1
            /   \
          null  null     */
 
        tree.root.left = new Node(2);
        tree.root.right = new Node(3);
 
        /* 2 and 3 become left and right children of 1
               1
            /     \
          2        3
        /   \     /  \
      null null null null  */
 
 
        tree.root.left.left = new Node(4);
        /* 4 becomes left child of 2
                    1
                /       \
               2          3
             /   \       /  \
            4    null  null  null
           /   \
          null null
         */
    }
}
```


## Binary Search Tree
### Search
```java 
  public Node search(Node root, int key)
{
    // Base Cases: root is null or key is present at root
    if (root==null || root.key==key)
        return root;
 
    // Key is greater than root's key
    if (root.key < key)
       return search(root.right, key);
 
    // Key is smaller than root's key
    return search(root.left, key);
}
```
### Insertion, Deletion and Traversal
```java
    class BinarySearchTree {
    /* Class containing left
    and right child of current node
     * and key value*/
    class Node {
        int key;
        Node left, right;
 
        public Node(int item)
        {
            key = item;
            left = right = null;
        }
    }
 
    // Root of BST
    Node root;
 
    // Constructor
    BinarySearchTree() { root = null; }
 
    // This method mainly calls deleteRec()
    void deleteKey(int key) { root = deleteRec(root, key); }
 
    /* A recursive function to
      delete an existing key in BST
     */
    Node deleteRec(Node root, int key)
    {
        /* Base Case: If the tree is empty */
        if (root == null)
            return root;
 
        /* Otherwise, recur down the tree */
        if (key < root.key)
            root.left = deleteRec(root.left, key);
        else if (key > root.key)
            root.right = deleteRec(root.right, key);
 
        // if key is same as root's
        // key, then This is the
        // node to be deleted
        else {
            // node with only one child or no child
            if (root.left == null)
                return root.right;
            else if (root.right == null)
                return root.left;
 
            // node with two children: Get the inorder
            // successor (smallest in the right subtree)
            root.key = minValue(root.right);
 
            // Delete the inorder successor
            root.right = deleteRec(root.right, root.key);
        }
 
        return root;
    }
 
    int minValue(Node root)
    {
        int minv = root.key;
        while (root.left != null)
        {
            minv = root.left.key;
            root = root.left;
        }
        return minv;
    }
 
    // This method mainly calls insertRec()
    void insert(int key) { root = insertRec(root, key); }
 
    /* A recursive function to
       insert a new key in BST */
    Node insertRec(Node root, int key)
    {
 
        /* If the tree is empty,
          return a new node */
        if (root == null) {
            root = new Node(key);
            return root;
        }
 
        /* Otherwise, recur down the tree */
        if (key < root.key)
            root.left = insertRec(root.left, key);
        else if (key > root.key)
            root.right = insertRec(root.right, key);
 
        /* return the (unchanged) node pointer */
        return root;
    }
 
    // This method mainly calls InorderRec()
    void inorder() { inorderRec(root); }
 
    // A utility function to do inorder traversal of BST
    void inorderRec(Node root)
    {
        if (root != null) {
            inorderRec(root.left);
            System.out.print(root.key + " ");
            inorderRec(root.right);
        }
    }
 
    // Driver Code
    public static void main(String[] args)
    {
        BinarySearchTree tree = new BinarySearchTree();
 
        /* Let us create following BST
              50
           /     \
          30      70
         /  \    /  \
        20   40  60   80 */
        tree.insert(50);
        tree.insert(30);
        tree.insert(20);
        tree.insert(40);
        tree.insert(70);
        tree.insert(60);
        tree.insert(80);
 
        System.out.println(
            "Inorder traversal of the given tree");
        tree.inorder();
 
        System.out.println("\nDelete 20");
        tree.deleteKey(20);
        System.out.println(
            "Inorder traversal of the modified tree");
        tree.inorder();
 
        System.out.println("\nDelete 30");
        tree.deleteKey(30);
        System.out.println(
            "Inorder traversal of the modified tree");
        tree.inorder();
 
        System.out.println("\nDelete 50");
        tree.deleteKey(50);
        System.out.println(
            "Inorder traversal of the modified tree");
        tree.inorder();
    }
}
```
## Index Mapping(Trivial Hashing) with -ves allowed
```java
  class Hashing
{
  
final static int MAX = 1000;
  
// Since array is global, it 
// is initialized as 0. 
static boolean[][] has = new boolean[MAX + 1][2];
  
// searching if X is Present in 
// the given array or not. 
static boolean search(int X) 
{
    if (X >= 0) 
    {
        if (has[X][0] == true) 
        {
            return true;
        } 
        else 
        {
            return false;
        }
    }
  
    // if X is negative take the 
    // absolute value of X. 
    X = Math.abs(X);
    if (has[X][1] == true) 
    {
        return true;
    }
  
    return false;
}
  
static void insert(int a[], int n) 
{
    for (int i = 0; i < n; i++) 
    {
        if (a[i] >= 0) 
        {
            has[a[i]][0] = true;
        } 
        else 
        {
            has[Math.abs(a[i])][1] = true;
        }
    }
}
  
// Driver code 
public static void main(String args[]) 
{
    int a[] = {-1, 9, -5, -8, -5, -2};
    int n = a.length;
    insert(a, n);
    int X = -5;
    if (search(X) == true)
    {
        System.out.println("Present");
    } 
    else 
    {
        System.out.println("Not Present");
    }
}
}

```
----------
##  Priority Queue using Heap using Array 
#### Ins- O(Log(n)) 
#### Del- O(Log(n))  
#### Peek- O(1)
```java
public class PQHeap {
    private static final int MAX_SIZE = 15;
    private int [] heap;
    private int size;

    public PQHeap() {
        heap = new int[MAX_SIZE];
        size = 0;
    }

    // returns the index of the parent node
    public static int parent(int i) {
        return (i - 1) / 2;
    }

    // return the index of the left child 
    public static int leftChild(int i) {
        return 2*i + 1;
    }

    // return the index of the right child 
    public static int rightChild(int i) {
        return 2*i + 2;
    }

    // insert the item at the appropriate position
    public void enqueue(int data) {
        if (size >= MAX_SIZE) {
            System.out.println("The queue is full. Cannot insert");
            return;
        }

        // first insert the time at the last position of the array 
        // and move it up
        heap[size] = data;
        size = size + 1;


        // move up until the heap property satisfies
        int i = size - 1;
        while (i != 0 && heap[PQHeap.parent(i)] < heap[i]) {
            int temp = heap[i];
            heap[i] = heap[parent(i)];
            heap[parent(i)] = temp;
            i = PQHeap.parent(i);
        }
    }

    // moves the item at position i of array a
    // into its appropriate position
    public void maxHeapify(int i){
        // find left child node
        int left = PQHeap.leftChild(i);

        // find right child node
        int right = PQHeap.rightChild(i);

        // find the largest among 3 nodes
        int largest = i;

        // check if the left node is larger than the current node
        if (left <= size && heap[left] > heap[largest]) {
            largest = left;
        }

        // check if the right node is larger than the current node 
        // and left node
        if (right <= size && heap[right] > heap[largest]) {
            largest = right;
        }

        // swap the largest node with the current node 
        // and repeat this process until the current node is larger than 
        // the right and the left node
        if (largest != i) {
            int temp = heap[i];
            heap[i] = heap[largest];
            heap[largest] = temp;
            maxHeapify(largest);
        }

    }

    // returns the  maximum item of the heap
    public int peek() {
        return heap[0];
    }

    // deletes the max item and return
    public int dequeue() {
        int maxItem = heap[0];

        // replace the first item with the last item
        heap[0] = heap[size - 1];
        size = size - 1;

        // maintain the heap property by heapifying the 
        // first item
        maxHeapify(0);
        return maxItem;
    }

    // prints the queue
    public void printQueue() {
        for (int i = 0; i < size; i++) {
            System.out.print(heap[i] + " ");
        }
        System.out.println();
    }

    public static void main(String [] args) {
        PQHeap queue = new PQHeap();
        queue.enqueue(43);
        queue.enqueue(333);
        queue.enqueue(345);
        queue.enqueue(45);
        queue.enqueue(3);
        queue.enqueue(400);
        System.out.println(queue.dequeue());
        System.out.println(queue.dequeue());
    }
}
```
--------
Heap and Graph left and Tries
