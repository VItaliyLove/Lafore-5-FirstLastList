# Lafore-5-FirstLastList

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.nio.Buffer;

class Algorithm {

    static class Link {

        public int data;
        public Link next;

        public Link(int newData){
            data = newData;
            next = null;
        }
    }

    static class FirstLastList{

        private double data;
        private Link first;
        private Link last;


        public FirstLastList()
        {
            first = null;
            last = null;
        }

        public boolean isEmpty() {
            return (first == null);
        }

        public void insertFirst(int data) {
            Link newLink = new Link(data);
            if (isEmpty())
                last = newLink;
            newLink.next = first;
            first = newLink;
        }

        public void deleteFirst() {
            if (!isEmpty()) {
                first = first.next;
                    if (first == null)
                        last = null;
            }
        }

        public void deletelast() {
            if (!isEmpty()) {
                Link previous = first;
                Link current = previous.next;
                if (current == null) {
                    first = null;
                    last = null;
                }
                else {
                    while (current.next != null) {
                        previous = previous.next;
                        current = current.next;
                    }
                    previous.next = null;
                }
            }
        }

        public void insertLast(int data) {
            Link newLink = new Link(data);
            if (isEmpty())
                first = newLink;
            else
                last.next = newLink;
            last = newLink;
        }

        public void displayList() {
            Link current = first;
            while (current != null) {
                System.out.print(current.data + " ");
                current = current.next;
            }
            System.out.println();
        }

    }

    public static void main(String[] arg) throws IOException {

        FirstLastList list = new FirstLastList();
        list.insertFirst(6);
        list.insertFirst(5);
        list.displayList();
        list.insertLast(7);
        list.insertLast(8);
        list.displayList();
        list.insertFirst(4);
        list.insertFirst(3);
        list.displayList();
        list.deleteFirst();
        list.displayList();
        list.deletelast();
        list.displayList();

    }
}
