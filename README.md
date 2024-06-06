
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

