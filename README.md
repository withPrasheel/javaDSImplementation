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
