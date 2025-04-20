```markdown
# 📘 Lab 2 – Dart Introduction

**Course:** Mobile Application Development Lab (CSL-341)  
**Student Name:** *Muhammad Anas*  
**Enrollment No.:** *01-134222-089*  
**Class & Section:** *CS 6B*  
**Department of Computer Science – Bahria University Islamabad*  

---

## 🎯 Objectives:
- Understand the basic syntax of Dart programming language.

## 🛠️ Tools Used:
- VS Code

---

## ✅ Task 1: Find the Largest Number in a List

### 🔹 Code:
```dart
void main() {
  List<int> numbers = [23, 12, 56, 78, 34, 99, 2]; 

  int findLargest(List<int> list) {
    int max = list[0];
    for (int num in list) {
      if (num > max) {
        max = num;
      }
    }
    return max;
  }

  print("Largest number: ${findLargest(numbers)}");
}
```

### 🔹 Output:
```
Largest number: 99
```

---

## ✅ Task 2: Merge Sort on a List

### 🔹 Code:
```dart
void main() {
  List<int> numbers = [12, 11, 13, 5, 6, 7];

  List<int> merge(List<int> left, List<int> right) {
    List<int> sortedList = [];
    int i = 0, j = 0;

    while (i < left.length && j < right.length) {
      if (left[i] < right[j]) {
        sortedList.add(left[i]);
        i++;
      } else {
        sortedList.add(right[j]);
        j++;
      }
    }

    while (i < left.length) {
      sortedList.add(left[i]);
      i++;
    }

    while (j < right.length) {
      sortedList.add(right[j]);
      j++;
    }

    return sortedList;
  }

  List<int> mergeSort(List<int> list) {
    if (list.length <= 1) return list;

    int mid = list.length ~/ 2;
    List<int> left = mergeSort(list.sublist(0, mid));
    List<int> right = mergeSort(list.sublist(mid));

    return merge(left, right);
  }

  print("Sorted List: ${mergeSort(numbers)}");
}
```

### 🔹 Output:
```
Sorted List: [5, 6, 7, 11, 12, 13]
```

---

## ✅ Task 3: Implement Stack from Scratch

### 🔹 Code:
```dart
class Stack {
  List<int> _stack = [];

  void push(int value) {
    _stack.add(value);
  }

  int? pop() {
    if (_stack.isNotEmpty) {
      return _stack.removeLast();
    } else {
      print("Stack is empty");
      return null;
    }
  }

  int? peek() {
    return _stack.isNotEmpty ? _stack.last : null;
  }

  bool isEmpty() {
    return _stack.isEmpty;
  }
}

void main() {
  Stack stack = Stack();

  stack.push(10);
  stack.push(20);
  stack.push(30);
  print("Top element: ${stack.peek()}");
  print("Popped element: ${stack.pop()}");
  print("Stack empty? ${stack.isEmpty()}");
  stack.pop();
  stack.pop();
  print("Stack empty? ${stack.isEmpty()}");
}
```

### 🔹 Output:
```
Top element: 30
Popped element: 30
Stack empty? false
Stack empty? true
```

---



