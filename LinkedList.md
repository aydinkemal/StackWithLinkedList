using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace DSLAB22102014
{
    class LinkedList<T> where T : IComparable
    {
        Node<T> head;

        public Node<T> createNode(T val)
        {
            return new Node<T>(val);
        }
        public void addToEnd(T val)
        {
            if (head == null)
                head = createNode(val);//new Node<T>(val);
            else
            {
                Node<T> iterator = head;
                while (iterator.next != null)
                {
                    iterator = iterator.next;
                }
                iterator.next = createNode(val);
            }
        }
        public void addToFront(T val)
        {
            Node<T> temp = createNode(val);
            temp.next = head;
            head = temp;
        }
        public void display()
        {
            Node<T> iterator = head;
            int counter = 0;
            while (iterator != null)
            {
                counter++;
                Console.WriteLine(iterator.value.ToString());
                iterator = iterator.next;
            }
            Console.WriteLine("Length:" + counter);


        }
        public void addAfterHead(T val)
        {
            if (head == null)
                head = createNode(val);
            else
            {
                Node<T> temp = createNode(val);
                temp.next = head.next;
                head.next = temp;
            }
        }
        private Node<T> findPrev(Node<T> current)
        {
            Node<T> iterator = head;
            while (iterator.next != current)
            {
                iterator = iterator.next;
            }
            return iterator;
        }
        public void reverse()
        {
            Node<T> tempHead, iterator;
            iterator = head;
            while (iterator.next != null)
                iterator = iterator.next;
            tempHead = iterator;
            while (iterator != head)
            {
                iterator.next = findPrev(iterator);
                iterator = iterator.next;
            }
            iterator.next = null;//head.next=null;
            head = tempHead;
        }
        public void delete(T val)
        {
            //Silinecek eleman listede yoksa çöker
            if (head != null)//hiç eleman yoksa
            {
                if (head.value.CompareTo(val) == 0)//İlk eleman silinecekse
                    head = head.next;
                else
                {
                    Node<T> iterator = head;
                    Node<T> prev = head;
                    while (iterator.value.CompareTo(val) != 0)
                    {
                        prev = iterator;
                        iterator = iterator.next;
                    }
                    //while sonrası iterator silinecek node u tutar
                    if (iterator.next == null)//Son eleman silinecekse
                        prev.next = null;
                    else//Aradaki bir eleman silinecekse
                    {
                        prev.next = iterator.next;
                    }

                }

            }

        }

        public int Length()
        {
            Node<T> iterator = head;
            int counter = 0;
            while (iterator != null)
            {
                counter++;
                iterator = iterator.next;
            }
            return counter;
        }
    }
}
