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
