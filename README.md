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

**Answer:** D) 3

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

**Answer:** D) 5 3 1 2 4

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

### 41.
**Question:** What will be the output of the following C++ code?

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> vec = {3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5};
    std::sort(vec.begin(), vec.end(), std::greater<int>());
    auto it = std::unique(vec.begin(), vec.end());
    vec.resize(std::distance(vec.begin(), it));
    for(int i : vec) std::cout << i << " ";
    return 0;
}
```
- A. 9 6 5 4 3 2 1
- B. 5 4 3 2 1
- C. 9 6 5 4 3 1
- D. 9 5 4 3 2 1

**Answer:** A

### 42.
**Question:** What is the time complexity of merging two balanced binary search trees of size n and m respectively?

- A. O(n + m)
- B. O(n log m)
- C. O(n * m)
- D. O(n log n + m log m)

**Answer:** A

### 43.
**Question:** What is the output of the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Map<String, Integer> map = new HashMap<>();
        map.put("apple", 3);
        map.put("banana", 2);
        map.put("cherry", 5);
        map.put("date", 2);
        System.out.println(map.get("banana") + map.get("date"));
    }
}
```
- A. 2
- B. 3
- C. 4
- D. 5

**Answer:** C

### 44.
**Question:** How would you find the longest common subsequence of two strings?

- A. Use dynamic programming to build a table of solutions to subproblems
- B. Use a stack to store intermediate results
- C. Use a queue to manage different subsequence states
- D. Use a hash table to store subsequence lengths

**Answer:** A

### 45.
**Question:** What does the following C++ function do?

```cpp
int func(const std::vector<int>& vec) {
    int sum = 0, maxSum = INT_MIN;
    for (int num : vec) {
        sum = std::max(num, sum + num);
        maxSum = std::max(maxSum, sum);
    }
    return maxSum;
}
```
- A. Finds the maximum element in the vector
- B. Finds the maximum sum of a subarray
- C. Finds the sum of all elements
- D. Finds the maximum product of a subarray

**Answer:** B

### 46.
**Question:** What is the result of running the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Deque<Integer> deque = new ArrayDeque<>();
        deque.add(1);
        deque.addFirst(2);
        deque.addLast(3);
        System.out.println(deque.pollFirst());
        System.out.println(deque.pollLast());
        System.out.println(deque.poll());
    }
}
```
- A. 1 3 2
- B. 2 3 1
- C. 2 1 3
- D. 1 2 3

**Answer:** B

### 47.
**Question:** Which of the following data structures is most appropriate for implementing an LRU (Least Recently Used) cache?

- A. Array
- B. Stack
- C. Queue
- D. HashMap combined with a Doubly Linked List

**Answer:** D

### 48.
**Question:** What will be the output of the following C++ code?

```cpp
#include <iostream>
#include <list>

int main() {
    std::list<int> lst = {1, 2, 3, 4, 5};
    auto it = lst.begin();
    std::advance(it, 3);
    lst.insert(it, 10);
    for (int x : lst) std::cout << x << " ";
    return 0;
}
```
- A. 1 2 3 4 10 5
- B. 1 2 3 10 4 5
- C. 1 10 2 3 4 5
- D. 10 1 2 3 4 5

**Answer:** B

### 49.
**Question:** What is the output of the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
        pq.add(3);
        pq.add(1);
        pq.add(4);
        pq.add(1);
        pq.add(5);
        while (!pq.isEmpty()) {
            System.out.print(pq.poll() + " ");
        }
    }
}
```
- A. 1 1 3 4 5
- B. 5 4 3 1 1
- C. 5 3 4 1 1
- D. 1 3 4 5 1

**Answer:** B

### 50.
**Question:** What does the following C++ function do?

```cpp
void func(std::stack<int>& s) {
    if (s.empty()) return;
    int x = s.top();
    s.pop();
    func(s);
    s.push(x);
}
```
- A. Sorts the stack in ascending order
- B. Sorts the stack in descending order
- C. Reverses the stack
- D. None of above

**Answer:** D

### 51.
**Question:** What is the output of the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Set<String> set = new TreeSet<>();
        set.add("banana");
        set.add("apple");
        set.add("cherry");
        set.add("date");
        for (String s : set) {
            System.out.print(s + " ");
        }
    }
}
```
- A. apple banana cherry date
- B. banana apple cherry date
- C. date cherry banana apple
- D. apple banana date cherry

**Answer:** A

### 52.
**Question:** What will be the output of the following C++ code?

```cpp
#include <iostream>
#include <set>

int main() {
    std::set<int> s = {1, 2, 3, 4, 5};
    s.erase(3);
    s.insert(6);
    for (int x : s) std::cout << x << " ";
    return 0;
}
```
- A. 1 2 4 5 6
- B. 1 2 3 4 5 6
- C. 1 2 4 5
- D. 1 2 4 5 6 3

**Answer:** A

### 53.
**Question:** What is the output of the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>(Arrays.asList("a", "b", "c", "d"));
        ListIterator<String> it = list.listIterator();
        while (it.hasNext()) {
            String s = it.next();
            if (s.equals("b")) it.add("e");
        }
        for (String s : list) {
            System.out.print(s + " ");
        }
    }
}
```
- A. a b c d e
- B. a b e c d
- C. a e b c d
- D. a b c d

**Answer:** B

### 54.
**Question:** What is the output of the following C++ code?

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};
    std::rotate(vec.begin(), vec.begin() + 2, vec.end());
    for (int x : vec) std::cout << x << " ";
    return 0;
}
```
- A. 1 2 3 4 5
- B. 3 4 5 1 2
- C. 4 5 1 2 3
- D. 2 3 4 5 1

**Answer:** B

### 55.
**Question:** What is the output of the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(1, 2, 3, 4, 5);
        Collections.rotate(list, 2);
        for (int i : list) {
            System.out.print(i + " ");
        }
    }
}
```
- A. 1 2 3 4 5
- B. 4 5 1 2 3
- C.

 3 4 5 1 2
- D. 2 3 4 5 1

**Answer:** C

### 56.
**Question:** Given a binary tree, how can you find its maximum depth?

- A. Use a queue for level order traversal and count levels
- B. Use a stack for in-order traversal and count nodes
- C. Use depth-first search (DFS) and keep track of the depth
- D. Use breadth-first search (BFS) and keep track of the depth

**Answer:** C

### 57.
**Question:** What is the output of the following C++ code?

```cpp
#include <iostream>
#include <stack>

void sortStack(std::stack<int>& s) {
    if (!s.empty()) {
        int x = s.top();
        s.pop();
        sortStack(s);
        insertSorted(s, x);
    }
}

void insertSorted(std::stack<int>& s, int x) {
    if (s.empty() || x > s.top()) {
        s.push(x);
        return;
    }
    int temp = s.top();
    s.pop();
    insertSorted(s, x);
    s.push(temp);
}

int main() {
    std::stack<int> s;
    s.push(3);
    s.push(1);
    s.push(4);
    s.push(2);
    sortStack(s);
    while (!s.empty()) {
        std::cout << s.top() << " ";
        s.pop();
    }
    return 0;
}
```
- A. 1 2 3 4
- B. 4 3 2 1
- C. 2 1 4 3
- D. 3 4 2 1

**Answer:** B

### 58.
**Question:** What will be the output of the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(1, 2, 3, 4, 5);
        Collections.shuffle(list);
        for (int i : list) {
            System.out.print(i + " ");
        }
    }
}
```
- A. 1 2 3 4 5
- B. 5 4 3 2 1
- C. Random permutation of 1 2 3 4 5
- D. 1 3 2 4 5

**Answer:** C

### 59.
**Question:** What does the following C++ function do?

```cpp
bool isBalanced(const std::string& str) {
    std::stack<char> s;
    for (char ch : str) {
        if (ch == '(' || ch == '{' || ch == '[') {
            s.push(ch);
        } else {
            if (s.empty()) return false;
            char top = s.top();
            if ((ch == ')' && top != '(') || (ch == '}' && top != '{') || (ch == ']' && top != '[')) {
                return false;
            }
            s.pop();
        }
    }
    return s.empty();
}
```
- A. Checks if the string has balanced parentheses, brackets, and braces
- B. Checks if the string is a palindrome
- C. Checks if the string has balanced quotes
- D. Checks if the string is a valid identifier

**Answer:** A

### 60.
**Question:** What will be the output of the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Map<String, Integer> map = new LinkedHashMap<>();
        map.put("one", 1);
        map.put("two", 2);
        map.put("three", 3);
        map.put("four", 4);
        map.put("five", 5);
        map.remove("three");
        for (String key : map.keySet()) {
            System.out.print(key + " ");
        }
    }
}
```
- A. one two three four five
- B. one two four five
- C. two four five
- D. one two three five

**Answer:** B

### 61.
**Question:** Given an undirected graph, how would you determine if it contains a cycle?

- A. Use Depth First Search (DFS) 
- B. Use Breadth First Search (BFS)
- C. Use a union-find data structure 
- D. All of Above

**Answer:** D

### 62.
**Question:** What is the time complexity of the Floyd-Warshall algorithm for finding the shortest paths in a weighted graph with n vertices?

- A. O(n)
- B. O(n log n)
- C. O(n^2)
- D. O(n^3)

**Answer:** D

### 63.
**Question:** Which of the following methods would be most efficient for finding the longest increasing subsequence in an array?

- A. Simple Dynamic Programming 
- B. Using a stack to store the sequence
- C. Using a queue to store the sequence
- D. Dynamic Programming with Binary Search 

**Answer:** D

### 64.
**Question:** How would you count the number of set bits in an integer in the most efficient way?
- A. Use a loop to count bits one by one
- B. Use the Brian Kernighan's algorithm
- C. Use a stack to count the bits
- D. Use a queue to count the bits

**Answer:** B

### 65.
**Question:** What does the following C++ function do?

```cpp
int fun(const std::vector<int>& vec) {
    int result = 0;
    for (int num : vec) {
        result ^= num;
    }
    return result;
}
```
- A. Finds the maximum element in the vector
- B. Finds the minimum element in the vector
- C. Finds the unique element in the vector where every other element appears twice
- D. Finds the sum of all elements in the vector

**Answer:** C

### 66.
**Question:** Given a linked list, how would you reverse the nodes of a linked list k at a time and return its modified list?
- A. Use a stack to reverse the nodes k at a time
- B. Use a queue to reverse the nodes k at a time
- C. Use recursion to reverse the nodes k at a time
- D. Both A and C

**Answer:** D

### 67.
**Question:** Given a linked list, how can you detect if there is a cycle in it?
- A. Use a stack to store visited nodes
- B. Use a queue to store visited nodes
- C. Use two pointers, one moving twice as fast as the other (Floyd’s Cycle Detection Algorithm)
- D. Use recursion to detect the cycle

**Answer:** C

### 68.
**Question:** What is the most efficient way to evaluate an arithmetic expression given in reverse Polish notation (postfix notation)?
- A. Use a stack to evaluate the expression
- B. Use a queue to evaluate the expression
- C. Use recursion to evaluate the expression
- D. Use a linked list to evaluate the expression

**Answer:** A

### 69.
**Question:** What will be the output of the following C++ code?

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> vec = {3, 5, 6, 7};
    int x = vec[0];
    for (int i = 1; i < vec.size(); ++i) {
        x &= vec[i];
    }
    std::cout << x;
    return 0;
}
```
- A. 0
- B. 3
- C. 1
- D. 2

**Answer:** A

### 70.
**Question:** What does the following C++ function do?

```cpp
int fun(const std::vector<int>& vec, int n) {
    int x1 = vec[0];
    int x2 = 1;
    for (int i = 1; i < vec.size(); i++) {
        x1 = x1 ^ vec[i];
    }
    for (int i = 2; i <= n; i++) {
        x2 = x2 ^ i;
    }
    return (x1 ^ x2);
}
```

- A. Finds the missing number in an array containing numbers from 1 to n with one number missing
- B. Finds the duplicate number in an array containing numbers from 1 to n
- C. Finds the unique number in an array where all numbers except one appear twice
- D. Finds the sum of all numbers in the array

**Answer:** A

### 71.
**Question:** Given a graph represented as an adjacency matrix, how would you find the number of strongly connected components?

- A. Use Depth First Search (DFS) directly on the graph
- B. Use Kosaraju’s algorithm
- C. Use Prim’s algorithm
- D. Use Dijkstra’s algorithm

**Answer:** B

### 72.
**Question:** What is the time complexity of the Bellman-Ford algorithm for finding the shortest path in a graph with V vertices and E edges?
- A. O(V)
- B. O(E log V)
- C. O(V^2)
- D. O(VE)

**Answer:** D

### 73.
**Question:** Given a 2D grid of characters and a word, write a function that returns true if the word exists in the grid. The word can be constructed from letters of sequentially adjacent cells, where "adjacent" cells are horizontally or vertically neighboring. The same letter cell may not be used more than once. Which algorithm would be most suitable?
- A. Depth First Search (DFS) with backtracking
- B. Breadth First Search (BFS)
- C. Dynamic Programming
- D. Binary Search

**Answer:** A

### 74.
**Question:** What is the output of the following C++ code?

```cpp
#include <iostream>

int main() {
    unsigned int x = 1 << 31;
    std::cout << x << " ";
    x = x >> 31;
    std::cout << x;
    return 0;
}
```
- A. 0 1
- B. 2147483648 1
- C. 2147483648 0
- D. 0 0

**Answer:** B

### 75.
**Question:** What is the best approach to solve the problem of finding the maximum product subarray in an array of integers?

- A. Use a dynamic programming approach to keep track of the maximum and minimum products ending at each index
- B. Sort the array and find the product of the last three elements
- C. Use a stack to keep track of the maximum and minimum products
- D. Use a queue to keep track of the maximum and minimum products

**Answer:** A

### 76.
**Question:** Given an array of n integers where each integer is in the range from 1 to n, some elements appear twice and others appear once. Find all the elements that appear twice. Your algorithm should run in O(n) time and use only constant extra space. Which technique is **most** suitable?
- A. Use a hash set to track duplicates
- B. Use an additional array to count occurrences
- C. Use the elements as indices and mark visited positions
- D. Sort the array and find duplicates

**Answer:** C

### 77.
**Question:** What will be the output of the following C++ code?

```cpp
#include <iostream>

int main() {
    int x = 6;  // 0110
    int y = 3;  // 0011
    std::cout << (x & y) << " ";   
    std::cout << (x | y) << " ";   
    std::cout << (x ^ y) << " ";  
    std::cout << (~x) << " ";      
    std::cout << (x << 1) << " ";  
    std::cout << (x >> 1);         
    return 0;
}
```
- A. 2 7 5 -7 12 3
- B. 2 7 5 -6 12 3
- C. 2 7 5 -7 12 6
- D. 2 6 5 -7 12 3

**Answer:** B

### 78.
**Question:** What is the output of the following Java code?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Deque<Integer> deque = new LinkedList<>();
        deque.offerFirst(1);
        deque.offerLast(2);
        deque.offerFirst(3);
        deque.offerLast(4);
        System.out.println(deque.pollFirst());
        System.out.println(deque.pollLast());
        System.out.println(deque.pollFirst());
        System.out.println(deque.pollLast());
    }
}
```
- A. 1 2 3 4
- B. 3 4 1 2
- C. 3 4 2 1
- D. 1 4 3 2

**Answer:** B

### 79.
**Question:** Given a linked list, how would you merge two sorted linked lists to produce a single sorted linked list?

- A. Use a stack to merge the lists
- B. Use a queue to merge the lists
- C. Use two pointers to traverse the lists and merge them
- D. Use a priority queue to merge the lists

**Answer:** C

### 80.
**Question:** What does the following C++ function do?

```cpp
int fun(const std::vector<int>& vec, int k) {
    int max_sum = INT_MIN, window_sum = 0;
    for (int i = 0; i < vec.size(); i++) {
        window_sum += vec[i];
        if (i >= k - 1) {
            max_sum = std::max(max_sum, window_sum);
            window_sum -= vec[i - (k - 1)];
        }
    }
    return max_sum;
}
```
- A. Finds the maximum sum of any subarray of length k
- B. Finds the maximum sum of any subarray
- C. Finds the minimum sum of any subarray of length k
- D. Finds the minimum sum of any subarray

**Answer:** A

### 81.
**Question:** Given a sorted array, how would you find the first occurrence of a target value using binary search?

- A. Perform a standard binary search and return the found index
- B. Modify the binary search to continue searching in the left half even after finding the target
- C. Use a linear search to find the first occurrence
- D. Use a hash map to store occurrences and return the first

**Answer:** B

### 82.
**Question:** What is the time complexity of Heap Sort in the worst case?

- A. O(n log n)
- B. O(n^2)
- C. O(n)
- D. O(log n)

**Answer:** A

### 83.
**Question:** Which of the following sorting algorithms is the most efficient for sorting a nearly sorted array?

- A. Quick Sort
- B. Merge Sort
- C. Bubble Sort
- D. Insertion Sort

**Answer:** D

### 84.
**Question:** What is the output of the following C++ code?

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> vec = {5, 3, 8, 6, 2};
    std::partial_sort(vec.begin(), vec.begin() + 3, vec.end());
    for (int i : vec) std::cout << i << " ";
    return 0;
}
```
- A. 2 3 5 6 8
- B. 2 3 5 8 6
- C. 5 3 8 6 2
- D. 5 6 8 2 3

**Answer:** B

### 85.
**Question:** Given an array of n integers, how would you find the kth largest element using a min-heap?

- A. Build a max-heap and extract the maximum k times
- B. Build a min-heap of the first k elements and for each remaining element, if it is larger than the root of the heap, replace the root and heapify
- C. Sort the array and return the kth largest element
- D. Use a binary search to find the kth largest element

**Answer:** B

### 86.
**Question:** What is the time complexity of the Quickselect algorithm for finding the kth smallest element in the average case?

- A. O(n log n)
- B. O(n)
- C. O(log n)
- D. O(n^2)

**Answer:** B

### 87.
**Question:** How would you merge k sorted linked lists into one sorted linked list efficiently?

- A. Use a binary search approach to merge the lists pair by pair
- B. Use a min-heap to extract the smallest element from the heads of the lists
- C. Concatenate all lists and sort them
- D. Use a stack to merge the lists

**Answer:** B

### 88.
**Question:** What will be the output of the following C++ code?

```cpp
#include <iostream>
#include <vector>
#include <queue>

int main() {
    std::priority_queue<int, std::vector<int>, std::greater<int>> minHeap;
    minHeap.push(5);
    minHeap.push(3);
    minHeap.push(8);
    minHeap.push(6);
    minHeap.push(2);
    std::cout << minHeap.top() << " ";
    minHeap.pop();
    std::cout << minHeap.top() << " ";
    return 0;
}
```
- A. 8 6
- B. 2 3
- C. 5 3
- D. 3 2

**Answer:** B

### 89.
**Question:** What is the best approach to sort an array of 0s, 1s, and 2s?

- A. Use a comparison-based sorting algorithm like quicksort or mergesort
- B. Use a counting sort
- C. Use the Dutch National Flag algorithm
- D. Use bubble sort

**Answer:** C

### 90.
**Question:** What is the time complexity of searching for an element in a binary search tree (BST) in the worst case?

- A. O(1)
- B. O(log n)
- C. O(n)
- D. O(n log n)

**Answer:** C

### 91.
**Question:** Given an array of integers, how would you find the median of the array efficiently?

- A. Sort the array and return the middle element
- B. Use a max-heap for the lower half and a min-heap for the upper half, and balance the heaps as you iterate through the array
- C. Use a stack to keep track of the median
- D. Use binary search to find the median

**Answer:** B



