# 212-week-9
package Test;
// LinkedIntList.java

public class LinkedIntList {


    // first value in the list
    private ListNode front;


    // construct an empty list
    public LinkedIntList() {
        front = null;
    }


    // return number of elements in the list
    public int size() {
        int count = 0;
        ListNode current = front;
        while (current != null) {
            current = current.next;
            count++;
        }
        return count;
    }


    // return the integer at the given index. assumes 0 <= index < size()
    public int get(int index) {
        return nodeAt(index).data;
    }


    // return the position of the first occurrence of the value
    // return -1 if not found
    public int indexOf(int value) {
        int index = 0;
        ListNode current = front;
        while (current != null) {
            if (current.data == value) {
                return index;
            }
            index++;
            current = current.next;
        }
        return -1;
    }


    // append given value to the end of the list
    public void add(int value) {
        if (front == null) {
            front = new ListNode(value);
        } else {
            ListNode current = front;
            while (current.next != null) {
                current = current.next;
            }
            current.next = new ListNode(value);
        }
    }


    // inserts given value at the given index. assumes 0 <= index <= size()
    public void add(int index, int value) {
        if (index == 0) {
            front = new ListNode(value, front);
        } else {
            ListNode current = nodeAt(index - 1);
            current.next = new ListNode(value, current.next);
        }
    }


    // remove value at the given index. assumes pre : 0 <= index < size()
    public void remove(int index) {
        if (index == 0) {
            front = front.next;
        } else {
            ListNode current = nodeAt(index - 1);
            current.next = current.next.next;
        }
    }


    // helper method: return a reference to the node at the given index
    // assumes0 <= i < size()
    private ListNode nodeAt(int index) {
        ListNode current = front;
        for (int i = 0; i < index; i++) {
            current = current.next;
        }
        return current;
    }

    public boolean isSorted(){
        ListNode current = front;
        while (current.next != null) {
            if(current.data > current.next.data){
                return false;
            }
            current = current.next;
        }
        return true;
    }

    // create a printable version of the list
    public String toString() {
        if (front == null) {
            return "[]";
        } else {
            String result = "[" + front.data;
            ListNode current = front.next;
            while (current != null) {
                result += ", " + current.data;
                current = current.next;
            }
            result += "]";
            return result;
        }
    }


}

// Class to test methods of LinkedIntList class


public class ListTest {

    public static void main(String[] args) {



        LinkedIntList list = new LinkedIntList();
        processList(list);
    }


    public static void processList(LinkedIntList list) {
        list.add(20);
        list.add(11);
        list.add(73);
        list.add(111);
        System.out.println(list);
        list.remove(1);
        System.out.println(list);
        System.out.println("List sorted? "+ list.isSorted());

        list.add(7);
        System.out.println(list);
        list.remove(1);
        System.out.println(list);
        System.out.println("List sorted? "+ list.isSorted());
    }
}
