


# 📘 Lab 5 – Introduction to Widgets and State Management

**Course:** Mobile Application Development Lab (CSL-341)  
**Student Name:** Muhammad Anas  
**Enrollment No.:** 01-134222-089  
**Class & Section:** BSCS-6B  
**Department of Computer Science – Bahria University Islamabad**

---

## 🎯 Objectives

- Creating custom widgets in Flutter.
- Implementing state management using Stateful widgets.
- Designing a tab-based application interface with multiple sections.

---

## 🛠️ Tools Used

- Visual Studio Code (VS Code)
- Dart & Flutter SDK

---

## ✅ Task 1: Dice Rolling App

### 🔹 Requirements:
- The app should display a dice image.
- When a button is pressed, the dice image changes randomly.

### 🔹 Key Concepts Used:
- Stateful widgets
- Image asset update on `setState()`
- Random number generation

### 🔹 Code (Simplified):

```dart
import 'package:flutter/material.dart';
import 'dart:math';

void main() {
  runApp(const DiceApp());
}

class DiceApp extends StatelessWidget {
  const DiceApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: DicePage(),
      debugShowCheckedModeBanner: false,
    );
  }
}

class DicePage extends StatefulWidget {
  @override
  _DicePageState createState() => _DicePageState();
}

class _DicePageState extends State<DicePage> {
  int diceNumber = 1;

  void rollDice() {
    setState(() {
      diceNumber = Random().nextInt(6) + 1;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Dice Roller')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Image.asset('assets/dice$diceNumber.png', height: 150),
            const SizedBox(height: 20),
            ElevatedButton(
              onPressed: rollDice,
              child: const Text('Roll Dice'),
            ),
          ],
        ),
      ),
    );
  }
}
````

---

## ✅ Task 2: Tab-Based Introduction App

### 🔹 Requirements:

* App should have 3 tabs with icons.
* Each tab should display:

  * Tab 1: Self Introduction
  * Tab 2: Education Information
  * Tab 3: Hobbies
* Use `TextSpan` for rich text formatting.

### 🔹 Key Concepts Used:

* `DefaultTabController`
* `TabBar` and `TabBarView`
* `RichText` and `TextSpan`

### 🔹 Code (Simplified):

```dart
import 'package:flutter/material.dart';

void main() => runApp(const MyTabbedApp());

class MyTabbedApp extends StatelessWidget {
  const MyTabbedApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: DefaultTabController(
        length: 3,
        child: Scaffold(
          appBar: AppBar(
            title: const Text("My Profile"),
            bottom: const TabBar(
              tabs: [
                Tab(icon: Icon(Icons.person), text: "Intro"),
                Tab(icon: Icon(Icons.school), text: "Education"),
                Tab(icon: Icon(Icons.star), text: "Hobbies"),
              ],
            ),
          ),
          body: const TabBarView(
            children: [
              ProfileTab(),
              EducationTab(),
              HobbiesTab(),
            ],
          ),
        ),
      ),
    );
  }
}

class ProfileTab extends StatelessWidget {
  const ProfileTab({super.key});
  @override
  Widget build(BuildContext context) {
    return Center(
      child: RichText(
        textAlign: TextAlign.center,
        text: const TextSpan(
          style: TextStyle(color: Colors.black, fontSize: 16),
          children: [
            TextSpan(text: "Hello! I am "),
            TextSpan(
              text: "Muhammad Anas",
              style: TextStyle(fontWeight: FontWeight.bold),
            ),
            TextSpan(text: ", a BSCS student at "),
            TextSpan(
              text: "Bahria University.",
              style: TextStyle(fontWeight: FontWeight.bold),
            ),
          ],
        ),
      ),
    );
  }
}

class EducationTab extends StatelessWidget {
  const EducationTab({super.key});
  @override
  Widget build(BuildContext context) {
    return Center(
      child: RichText(
        text: const TextSpan(
          style: TextStyle(color: Colors.black, fontSize: 16),
          children: [
            TextSpan(text: "I have completed my education up to "),
            TextSpan(
              text: "6th semester",
              style: TextStyle(fontWeight: FontWeight.bold),
            ),
            TextSpan(text: " in Computer Science."),
          ],
        ),
      ),
    );
  }
}

class HobbiesTab extends StatelessWidget {
  const HobbiesTab({super.key});
  @override
  Widget build(BuildContext context) {
    return Center(
      child: RichText(
        text: const TextSpan(
          style: TextStyle(color: Colors.black, fontSize: 16),
          children: [
            TextSpan(text: "I enjoy "),
            TextSpan(
              text: "coding, learning new technologies, and gaming.",
              style: TextStyle(fontStyle: FontStyle.italic),
            ),
          ],
        ),
      ),
    );
  }
}
```

---

## 🖼️ Output:

* ✅ Dice image changes randomly on button click
* ✅ Tabbed interface with Introduction, Education, and Hobbies sections
* ✅ Formatted rich text using `TextSpan`
* ✅ Clean interface with icons and organized layout

---

## 📌 Conclusion

* Built interactive apps using **Flutter widgets** and **state management**
* Implemented **random behavior** and **tab navigation**
* Practiced using `TextSpan`, `Image.asset`, and user interface structuring

---

