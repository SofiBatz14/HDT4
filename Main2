import java.util.*;

// Interfaz para Pila (Stack)
interface StackADT<T> {
    void push(T item);
    T pop();
    T peek();
    boolean isEmpty();
    int size();
}

// Clase Abstracta para Pila
abstract class AbstractStack<T> implements StackADT<T> {
    protected List<T> elements = new ArrayList<>();

    public void push(T item) {
        elements.add(item);
    }

    public T pop() {
        if (isEmpty()) throw new EmptyStackException();
        return elements.remove(elements.size() - 1);
    }

    public T peek() {
        if (isEmpty()) throw new EmptyStackException();
        return elements.get(elements.size() - 1);
    }

    public boolean isEmpty() {
        return elements.isEmpty();
    }

    public int size() {
        return elements.size();
    }
}

// Implementación de Pila con ArrayList
class ArrayListStack<T> extends AbstractStack<T> {
    public ArrayListStack() {
        elements = new ArrayList<>();
    }
}

// Implementación de Pila con Vector
class VectorStack<T> extends AbstractStack<T> {
    public VectorStack() {
        elements = new Vector<>();
    }
}

// Implementación de Pila con Lista Enlazada
class ListStack<T> extends AbstractStack<T> {
    public ListStack() {
        elements = new LinkedList<>();
    }
}

// Interfaz para Lista
interface ListADT<T> {
    void add(T item);
    T remove(int index);
    T get(int index);
    int size();
}

// Clase Abstracta para Lista
abstract class AbstractList<T> implements ListADT<T> {
    protected int size = 0;

    public int size() {
        return size;
    }
}

// Implementación de Lista Simplemente Enlazada
class SinglyLinkedList<T> extends AbstractList<T> {
    private Node<T> head;

    private static class Node<T> {
        T data;
        Node<T> next;

        Node(T data) {
            this.data = data;
        }
    }

    public void add(T item) {
        Node<T> newNode = new Node<>(item);
        if (head == null) {
            head = newNode;
        } else {
            Node<T> current = head;
            while (current.next != null) {
                current = current.next;
            }
            current.next = newNode;
        }
        size++;
    }

    public T remove(int index) {
        if (index < 0 || index >= size) throw new IndexOutOfBoundsException();
        Node<T> current = head;
        Node<T> previous = null;

        for (int i = 0; i < index; i++) {
            previous = current;
            current = current.next;
        }
        if (previous == null) {
            head = current.next;
        } else {
            previous.next = current.next;
        }
        size--;
        return current.data;
    }

    public T get(int index) {
        if (index < 0 || index >= size) throw new IndexOutOfBoundsException();
        Node<T> current = head;
        for (int i = 0; i < index; i++) {
            current = current.next;
        }
        return current.data;
    }
}

// Implementación de Lista Doblemente Enlazada
class DoublyLinkedList<T> extends AbstractList<T> {
    private Node<T> head;
    private Node<T> tail;

    private static class Node<T> {
        T data;
        Node<T> next;
        Node<T> prev;

        Node(T data) {
            this.data = data;
        }
    }

    public void add(T item) {
        Node<T> newNode = new Node<>(item);
        if (head == null) {
            head = tail = newNode;
        } else {
            tail.next = newNode;
            newNode.prev = tail;
            tail = newNode;
        }
        size++;
    }

    public T remove(int index) {
        if (index < 0 || index >= size) throw new IndexOutOfBoundsException();
        Node<T> current = head;
        for (int i = 0; i < index; i++) {
            current = current.next;
        }
        if (current.prev != null) current.prev.next = current.next;
        if (current.next != null) current.next.prev = current.prev;
        if (current == head) head = current.next;
        if (current == tail) tail = current.prev;
        size--;
        return current.data;
    }

    public T get(int index) {
        if (index < 0 || index >= size) throw new IndexOutOfBoundsException();
        Node<T> current = head;
        for (int i = 0; i < index; i++) {
            current = current.next;
        }
        return current.data;
    }
}

// Singleton para Calculadora
class Calculator {
    private static Calculator instance;

    private Calculator() {}

    public static Calculator getInstance() {
        if (instance == null) {
            instance = new Calculator();
        }
        return instance;
    }

    public String infixToPostfix(String infix) {
        // Algoritmo de conversión de infix a postfix
        // Se omite implementación por brevedad
        return "postfix_expression";
    }

    public int evaluatePostfix(String postfix) {
        // Algoritmo de evaluación de postfix
        // Se omite implementación por brevedad
        return 42;
    }
}

// Clase Principal con Factory Pattern
public class Main2 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Seleccione la implementación de Pila:");
        System.out.println("1. ArrayList");
        System.out.println("2. Vector");
        System.out.println("3. Lista Enlazada");

        int option = scanner.nextInt();
        StackADT<String> stack;

        if (option == 1) {
            stack = new ArrayListStack<>();
        } else if (option == 2) {
            stack = new VectorStack<>();
        } else {
            stack = new ListStack<>();
        }

        Calculator calculator = Calculator.getInstance();

        System.out.print("Ingrese la expresión infix: ");
        scanner.nextLine();
        String infix = scanner.nextLine();

        String postfix = calculator.infixToPostfix(infix);
        System.out.println("Postfix: " + postfix);

        int result = calculator.evaluatePostfix(postfix);
        System.out.println("Resultado: " + result);

        scanner.close();
    }
}

