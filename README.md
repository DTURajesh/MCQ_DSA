
# MCQ_DSA

1. What will the output of the following code snippet?

```cpp
void solve() {
    int a[] = {1, 2, 3, 4, 5};
    int sum = 0;
    for(int i = 0; i < 5; i++) {
        if(i % 2 == 0) {
            sum += *(a + i);
        }
        else {
            sum -= *(a + i);
        }
    }
    cout << sum << endl;
}
```
A) 2  
B) 15  
C) Syntax Error  
D) 3

2. What will be the output of the following code snippet?
```cpp
void solve() {
   deque<int> dq;
   for(int i = 1; i <= 5; i++) {
       if(i % 2 == 0) {
           dq.push_back(i);
       }
       else {
           dq.push_front(i);
       }
   }
   for(auto x: dq) {
       cout << x << " ";
   }
   cout << endl;
}
```
A) 1 2 3 4 5  
B) 5 4 3 2 1  
C) 1 3 5 2 3  
D) 5 3 1 2 4

3. Given a binary tree, what will be the output of the following code snippet ?
```cpp
struct Node {
    int data;
    Node* left;
    Node* right;
    Node(int val) : data(val), left(nullptr), right(nullptr) {}
};

int getMaxWidth(Node* root) {
    if (root == nullptr) return 0;
    int maxWidth = 0;
    queue<Node*> q;
    q.push(root);
    while (!q.empty()) {
        int count = q.size();
        maxWidth = max(maxWidth, count);
        while (count--) {
            Node* temp = q.front();
            q.pop();
            if (temp->left != nullptr) q.push(temp->left);
            if (temp->right != nullptr) q.push(temp->right);
        }
    }
    return maxWidth;
}

void solve() {
    Node* root = new Node(1);
    root->left = new Node(2);
    root->right = new Node(3);
    root->left->left = new Node(4);
    root->left->right = new Node(5);
    root->right->right = new Node(8);
    root->right->right->left = new Node(6);
    root->right->right->right = new Node(7);
    
    cout << getMaxWidth(root) << endl;
}
```
A) 2  
B) 3  
C) 4  
D) 5  

**Answer:** C) 4

4. Which of the following algorithms is used for finding strongly connected components in a directed graph?

A) Dijkstra's Algorithm  
B) Kosaraju's Algorithm  
C) Prim's Algorithm  
D) Kruskal's Algorithm  

**Answer:** B) Kosaraju's Algorithm

5. What will be the output of the following code snippet ?
```cpp
class A {
    vector<int> tree;
    int n;

    void build(vector<int>& arr, int v, int tl, int tr) {
        if (tl == tr) {
            tree[v] = arr[tl];
        } else {
            int tm = (tl + tr) / 2;
            build(arr, 2*v, tl, tm);
            build(arr, 2*v+1, tm+1, tr);
            tree[v] = tree[2*v] + tree[2*v+1];
        }
    }

    int get(int v, int tl, int tr, int l, int r) {
        if (l > r)
            return 0;
        if (l == tl && r == tr)
            return tree[v];
        int tm = (tl + tr) / 2;
        return get(2*v, tl, tm, l, min(r, tm))
             + get(2*v+1, tm+1, tr, max(l, tm+1), r);
    }

public:
    A(vector<int>& arr) {
        n = arr.size();
        tree.resize(4 * n);
        build(arr, 1, 0, n-1);
    }

    int get(int l, int r) {
        return get(1, 0, n-1, l, r);
    }
};

void solve() {
    vector<int> arr = {1, 2, 3, 4, 5};
    A st(arr);
    cout << st.get(1, 3) << endl;
}
```
A) 6  
B) 7  
C) 9  
D) 12  

**Answer:** C) 9

6. What is the time complexity of the following code snippet ?
```cpp
int helper(vector<int>& nums) {
    vector<int> lis;
    for (int num : nums) {
        auto it = lower_bound(lis.begin(), lis.end(), num);
        if (it == lis.end()) lis.push_back(num);
        else *it = num;
    }
    return lis.size();
}

void solve() {
    vector<int> nums = {10, 9, 2, 5, 3, 7, 101, 18};
    cout << helper(nums) << endl;
}
```
A) O(n^2)  
B) O(n log n)  
C) O(log n)  
D) O(n)  

**Answer:** B) O(n log n)

7. What will be the output of the following code snippet?
```java
interface A {
    default void show() {
        System.out.println("A");
    }
}

abstract class B implements A {
    abstract void show();
}

class C extends B {
    void show() {
        System.out.println("C");
    }
}

public class Main {
    public static void main(String[] args) {
        B obj = new C();
        obj.show();
    }
}
```
A) A  
B) C  
C) Compilation Error  
D) Runtime Exception  

**Answer:** B) C

8. What will be the output of the following code snippet?
```java
interface A {
    default void show() {
        System.out.println("A");
    }
}

interface B extends A {
    default void show() {
        System.out.println("B");
    }
}

class C implements B {
    public void show() {
        B.super.show();
    }
}

public class Main {
    public static void main(String[] args) {
        C obj = new C();
        obj.show();
    }
}
```
A) A  
B) B  
C) AB  
D) Compilation Error  

**Answer:** B) B

9. What will be the output of the following code snippet?
```java
class Outer {
    private int data = 10;
    
    class Inner {
        void display() {
            System.out.println(data);
        }
    }
    
    void display() {
        Inner in = new Inner() {
            void display() {
                System.out.println(data * 2);
            }
        };
        in.display();
    }
}

public class Main {
    public static void main(String[] args) {
        Outer out = new Outer();
        out.display();
    }
}
```
A) 10  
B) 20  
C) 10 20  
D) Compilation Error  

**Answer:** B) 20

10. What will be the output of the following code snippet?
```java
abstract class Base {
    abstract void display();
    
    void show() {
        System.out.println("Base show");
    }
}

class Derived extends Base {
    void display() {
        System.out.println("Derived display");
    }
}

public class Main {
    public static void main(String[] args) {
        Derived d = new Derived();
        d.display();
        d.show();
    }
}
```
A) Derived display  
B) Base show  
C) Derived display Base show  
D) Compilation Error  

**Answer:** C) Derived display Base show

11. What will be the output of the following code snippet?
```java
class A {
    void show() {
        System.out.println("A");
    }
}

class B extends A {
    void show() {
        super.show();
        System.out.println("B");
    }
}

class C extends B {
    void show() {
        super.show();
        System.out.println("C");
    }
}

public class Main {
    public static void main(String[] args) {
        C obj = new C();
        obj.show();
    }
}
```
A) A B C  
B) C B A  
C) A B  
D) A B B C  

**Answer:** A) A B C

12. What will be the output of the following code snippet?
```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    void sound() {
        System.out.println("Cat meows");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound();
        Cat c = (Cat) a;
        c.sound();
    }
}
```
A) Animal sound  
B) Dog barks  
C) Cat meows  
D) Runtime Exception  

**Answer:** D) Runtime Exception

13. What will be the output of the following code snippet?
```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() { cout << "Base\n"; }
};

class Derived1 : virtual public Base {
public:
    void show() override { cout << "Derived1\n"; }
};

class Derived2 : virtual public Base {
public:
    void show() override { cout << "Derived2\n"; }
};

class Multiple : public Derived1, public Derived2 {
public:
    void show() override { cout << "Multiple\n"; }
};

void solve() {
    Multiple obj;
    Base *ptr = &obj;
    ptr->show();
}
```
A) Base  
B) Derived1  
C) Derived2  
D) Multiple  

**Answer:** D) Multiple

14. What will be the output of the following code snippet?
```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() { cout << "Base\n"; }
};

class Derived : public Base {
public:
    void show() override { cout << "Derived\n"; }
};

void solve() {
    Base *ptr = new Derived();
    ptr->show();
    delete ptr;
}
```
A) Base  
B) Derived  
C) Compilation Error  
D) Runtime Exception  

**Answer:** B) Derived

15. What will be the output of the following code snippet?
```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() { cout << "Base\n"; }
};

class Derived : public Base {
public:
    void show() override { cout << "Derived\n"; }
};

void solve() {
    Derived d;
    Base &b = d;
    b.show();
}
```
A) Base  
B) Derived  
C) Compilation Error  
D) Runtime Exception  

**Answer:** B) Derived

16. What will be the output of the following code snippet?
```cpp
#include <iostream>
using namespace std;

class A {
public:
    virtual void show() { cout << "A\n"; }
};

class B : public A {
public:
    void show() override { cout << "B\n"; }
};

void solve() {
    A *ptr = new B();
    B *bptr = dynamic_cast<B*>(ptr);
    bptr->show();
}
```
A) A  
B) B  
C) Compilation Error  
D) Runtime Exception  

**Answer:** B) B

17. What will be the output of the following code snippet?
```cpp
#include <iostream>
using namespace std;

class A {
public:
    virtual void show() { cout << "A\n"; }
};

class B : public A {
public:
    void show() override { cout << "B\n"; }
};

class C : public B {
public:
    void show() override { cout << "C\n"; }
};

void solve() {
    A *ptr = new C();
    B *bptr = dynamic_cast<B*>(ptr);
    bptr->show();
}
```
A) A  
B) B  
C) C  
D) Compilation Error  

**Answer:** C) C

18. What will be the output of the following code snippet?
```cpp
#include <iostream>
using namespace std;

class A {
public:
    virtual void show() { cout << "A\n"; }
};

class B : public A {
public:
    void show() override { cout << "B\n"; }
};

class C : public A {
public:
    void show() override { cout << "C\n"; }
};

void solve() {
    A *ptr = new B();
    C *cptr = dynamic_cast<C*>(ptr);
    if (cptr != nullptr) {
        cptr->show();
    } else {
        cout << "Null\n";
    }
}
```
A) A  
B) B  
C) C  
D) Null  

**Answer:** D) Null

19. What will be the output of the following code snippet?
```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() { cout << "Base\n"; }
};

class Derived1 : virtual public Base {
public:
    void show() override { cout << "Derived1\n"; }
};

class Derived2 : virtual public Base {
public:
    void show() override { cout << "Derived2\n"; }
};

class Multiple : public Derived1, public Derived2 {
public:
    void show() override { cout << "Multiple\n"; }
};

void solve() {
    Multiple obj;
    Derived1 *dptr = &obj;
    dptr->show();
}
```
A) Base  
B) Derived1  
C) Derived2  
D) Multiple  

**Answer:** D) Multiple

20. What will be the output of the following code snippet?
```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() { cout << "Base\n"; }
};

class Derived : public Base {
public:
    void show() override { cout << "Derived\n"; }
};

void solve() {
    Base *ptr = new Derived();
    Derived *dptr = dynamic_cast<Derived*>(ptr);
    dptr->show();
}
```
A) Base  
B) Derived  
C) Compilation Error  
D) Runtime Exception  

**Answer:** B) Derived

Sure, here are all the questions numbered from 21 onwards:

### 21.
**Question:** Given a sorted array rotated at an unknown pivot, how would you find a given target value?
- A. Use linear search
- B. Use binary search directly
- C. Use a modified binary search to find the pivot first, then search in the appropriate half
- D. Sort the array first, then use binary search

**Answer:** C

### 22.
**Question:** Given a string array, write a function to group anagrams together. What is the most efficient way to achieve this?
- A. Sort each string and use a hashmap to group them
- B. Compare each string with every other string and group them
- C. Sort the entire array and then find groups
- D. Use a Trie to group the anagrams

**Answer:** A

### 23.
**Question:** How would you check if a singly linked list is a palindrome?
- A. Reverse the linked list and compare with the original
- B. Use a stack to store the first half, then compare while traversing the second half
- C. Use two pointers, one fast and one slow, to find the middle and compare halves
- D. Convert the linked list to a string and check if the string is a palindrome

**Answer:** B

### 24.
**Question:** How would you implement a circular queue using an array?
- A. Use a fixed-size array and two pointers, one for the front and one for the rear
- B. Use a dynamic array that resizes as needed
- C. Use a single pointer that increments and wraps around when the end of the array is reached
- D. Use two stacks, one for enqueuing and one for dequeuing

**Answer:** A

### 25.
**Question:** How can you find the middle element of a singly linked list in one pass?
- A. Use a slow and a fast pointer, where the fast pointer moves two steps for each one step of the slow pointer
- B. Count the elements first, then traverse to the middle
- C. Use a stack to store elements and then pop half the elements
- D. Use recursion to reach the middle element

**Answer:** A

### 26.
**Question:** Given an array of n integers, find the kth smallest element in linear time.
- A. Sort the array and return the kth element
- B. Use a min-heap to extract the minimum k times
- C. Use the Quickselect algorithm
- D. Use a binary search to find the kth smallest element

**Answer:** C

### 27.
**Question:** How would you check for balanced parentheses in an expression string?
- A. Use a stack to push opening brackets and pop for closing brackets
- B. Use counters for each type of bracket
- C. Traverse the string and directly match pairs
- D. Use a hashmap to store bracket pairs

**Answer:** A

### 28.
**Question:** How can you sort a linked list in O(n log n) time complexity?
- A. Use bubble sort
- B. Use merge sort
- C. Use quicksort
- D. Use insertion sort

**Answer:** B

### 29.
**Question:** How would you implement a priority queue ?
- A. Use an array where each element has an associated priority
- B. Use a linked list where each element has an associated priority
- C. Use a binary heap to efficiently manage the priorities
- D. Use a stack where each element has an associated priority

**Answer:** C

### 30.
**Question:** Given an unsorted array of integers, find the length of the longest consecutive elements sequence. Your algorithm should run in O(n) complexity.
- A. Sort the array and find the longest consecutive subsequence
- B. Use a hashmap to keep track of consecutive sequences
- C. Use a set to store elements and then iterate to find the longest sequence
- D. Use dynamic programming to find the longest consecutive sequence

**Answer:** C

### 31.


### 32.
**Question:** What is the time complexity of finding the intersection of two sorted linked lists?
- A. O(n + m)
- B. O(n * m)
- C. O(n log m)
- D. O(n^2)

**Answer:** A

### 33.
**Question:** What is the output of the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        String[] arr = {"apple", "banana", "cherry", "apple", "date"};
        Set<String> set = new LinkedHashSet<>(Arrays.asList(arr));
        set.add("apple");
        set.add("banana");
        for (String s : set) {
            System.out.print(s + " ");
        }
    }
}
```
- A. apple banana cherry date
- B. apple cherry date banana
- C. cherry date banana apple
- D. date apple banana cherry

**Answer:** A

### 34.
**Question:** What is the most efficient way to merge two balanced binary search trees?
- A. Perform an inorder traversal of both trees, merge the two sorted lists, and build a balanced BST from the merged list
- B. Insert each element of the second tree into the first tree
- C. Perform a level order traversal of both trees and merge them
- D. Convert both trees into max-heaps and merge the heaps

**Answer:** A

### 35.
**Question:** Which of the following algorithms can be used to find the shortest path in a weighted graph with negative weights but no negative cycles?
- A. Dijkstra's algorithm
- B. Prim's algorithm
- C. Floyd-Warshall algorithm
- D. Bellman-Ford algorithm

**Answer:** D

### 36.
**Question:** What does the following C++ function do?

```cpp
void func(std::vector<int>& vec) {
    std::stack<int> s;
    for (int x : vec) {
        while (!s.empty() && s.top() < x) {
            s.pop();
        }
        s.push(x);
    }
    vec.clear();
    while (!s.empty()) {
        vec.push_back(s.top());
        s.pop();
    }
    std::reverse(vec.begin(), vec.end());
}
```
- A. Finds the next greater element for each element in the vector
- B. Removes all elements smaller than the previous element
- C. Sorts the vector in non-decreasing order
- D. Filters out all duplicate elements

**Answer:** B

### 37.
**Question:** What is the result of running the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<>();
        queue.add(1);
        queue.add(2);
        queue.add(3);
        System.out.println(queue.peek());
        queue.remove();
        queue.add(4);
        System.out.println(queue.peek());
        queue.remove();
        System.out.println(queue.peek());
    }
}
```
- A. 1 2 3
- B. 1 1 2
- C. 1 2 4
- D. 1 2 3 4

**Answer:** A

### 38.
**Question:** Which sorting algorithm is the most efficient in the average case for sorting a large number of elements?
- A. Bubble sort
- B. Insertion sort
- C. Merge sort
- D. Quick sort

**Answer:** D

### 39.
**Question:** What will be the output of the following C++ code?

```cpp
#include <iostream>
#include <stack>

int main() {
    std::stack<int> s;
    s.push(1);
    s.push(2);
    s.push(3);
    std::cout << s.top() << " ";
    s.pop();
    std::cout << s.top() << " ";
    s.pop();
    s.push(4);
    std::cout << s.top() << " ";
    return 0;
}
```
- A. 3 2 4
- B. 3 2 1
- C. 3 1 4
- D. 1 2 3 4

**Answer:** A

### 40.
**Question:** What is the output of the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(5, 3, 8, 6, 2);
        Collections.sort(list,

 (a, b) -> b - a);
        list.forEach(System.out::print);
    }
}
```
- A. 2 3 5 6 8
- B. 8 6 5 3 2
- C. 5 3 8 6 2
- D. 8 5 3 6 2

**Answer:** B

