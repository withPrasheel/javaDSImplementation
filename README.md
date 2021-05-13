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

## 
