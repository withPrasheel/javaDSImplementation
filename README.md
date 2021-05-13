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
