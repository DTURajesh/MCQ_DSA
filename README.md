```markdown
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
