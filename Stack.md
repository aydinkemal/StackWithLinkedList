namespace DSLAB22102014
{
    class Stack<T> where T : IComparable
    {

        int size;
        Node<T> top;

        public Stack(int size)
        {

            this.size = size;
            Node<T> top = null;
        }
        public bool isEmpty()
        {
            return top == null;

        }
        public bool isFull()
        {

            return (nodeCount() == this.size && !(nodeCount() > size));
        }

        public int nodeCount()
        {
            int counter = 0;
            Node<T> iterator = top;
            while (iterator != null)
            {
                counter++;
                iterator = iterator.next;
            }
            return counter;
        }
        public void push(T val)
        {
            if (isFull())
            {
                throw new Exception("Stack is full!");
            }
           
            else if (isEmpty())
            {
                top = createNode(val);
            }
            else {
                Node<T> temp = createNode(val);
                temp.next = top;
                top = temp;
                }


        }
        public T pop()
        {
            if (isFull())
            {
                throw new Exception("Stack is Full!");
            }
            else
            {
            Node<T> temp = top;
            top = top.next;
            return temp.value;
            }
        }
        public Node<T> createNode(T val)
        {

            return new Node<T>(val);
        }
        public void display()
        {

            
            Node<T> iterator = top;
            while (iterator != null)
            {
                Console.WriteLine(iterator.value);
                iterator = iterator.next;
            }
            


        }

        //push
        //pop
        //isFull
        //isEmpty
        //display
        //createNode
    }
}
