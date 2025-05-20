
# 📘 Lab 7 – Introduction to Gestures in Flutter

**Course:** Mobile Application Development Lab (CSL-341)  
**Student Name:** Muhammad Anas  
**Enrollment No.:** 01-134222-089  
**Class & Section:** BSCS-6B  
**Department of Computer Science – Bahria University Islamabad**

---

## 🎯 Objectives

- Implement gesture handling in Flutter applications.
- Learn how to use tap and long-press interactions to navigate between screens.
- Build a multi-screen app using `GestureDetector` and `Navigator`.

---

## 🛠️ Tools Used

- Visual Studio Code (VS Code)
- Dart & Flutter SDK

---

## ✅ Task Overview

### 🔹 Application Requirements:

1. **First Screen (Splash Screen)**
   - Displays a logo.
   - Double-tapping the logo navigates to the second screen.

2. **Second Screen**
   - AppBar with your name as the title.
   - Contains **three tabs**:
     - **Tab 1**: Info about yourself
     - **Tab 2**: Info about your hometown
     - **Tab 3**: Info about your student life at Bahria University
   - Long-pressing on any tab content navigates to the third screen.

3. **Third Screen**
   - Displays brief info.
   - Long-pressing on the brief info expands it into detailed information.

---

## 🔹 Sample Code Structure

> You can break this into files like `main.dart`, `screen1.dart`, `screen2.dart`, and `screen3.dart`.

---

### 📄 `main.dart`

```dart
import 'package:flutter/material.dart';
import 'screen1.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Lab 7 Gesture App',
      home: const SplashScreen(),
    );
  }
}
````

---

### 📄 `screen1.dart` (Splash Screen)

```dart
import 'package:flutter/material.dart';
import 'screen2.dart';

class SplashScreen extends StatelessWidget {
  const SplashScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: GestureDetector(
          onDoubleTap: () {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => const SecondScreen()),
            );
          },
          child: Image.asset('assets/logo.png', height: 150),
        ),
      ),
    );
  }
}
```

---

### 📄 `screen2.dart` (Tabbed Info Screen)

```dart
import 'package:flutter/material.dart';
import 'screen3.dart';

class SecondScreen extends StatelessWidget {
  const SecondScreen({super.key});

  void _navigateToDetails(BuildContext context) {
    Navigator.push(
      context,
      MaterialPageRoute(builder: (context) => const ThirdScreen()),
    );
  }

  @override
  Widget build(BuildContext context) {
    return DefaultTabController(
      length: 3,
      child: Scaffold(
        appBar: AppBar(
          title: const Text('Muhammad Anas'),
          bottom: const TabBar(
            tabs: [
              Tab(icon: Icon(Icons.person), text: "Me"),
              Tab(icon: Icon(Icons.location_city), text: "Hometown"),
              Tab(icon: Icon(Icons.school), text: "Student Life"),
            ],
          ),
        ),
        body: TabBarView(
          children: [
            _buildTabContent(context, "I am a dedicated and passionate CS student."),
            _buildTabContent(context, "I come from Islamabad, a peaceful and green city."),
            _buildTabContent(context, "Studying at Bahria has been a journey of growth."),
          ],
        ),
      ),
    );
  }

  Widget _buildTabContent(BuildContext context, String text) {
    return GestureDetector(
      onLongPress: () => _navigateToDetails(context),
      child: Center(
        child: Padding(
          padding: const EdgeInsets.all(16.0),
          child: Text(text, style: const TextStyle(fontSize: 18)),
        ),
      ),
    );
  }
}
```

---

### 📄 `screen3.dart` (Detailed Info Screen)

```dart
import 'package:flutter/material.dart';

class ThirdScreen extends StatefulWidget {
  const ThirdScreen({super.key});

  @override
  State<ThirdScreen> createState() => _ThirdScreenState();
}

class _ThirdScreenState extends State<ThirdScreen> {
  bool _showFullText = false;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Detailed Info")),
      body: Center(
        child: GestureDetector(
          onLongPress: () {
            setState(() {
              _showFullText = true;
            });
          },
          child: Padding(
            padding: const EdgeInsets.all(16.0),
            child: Text(
              _showFullText
                  ? "I am Muhammad Anas, a 6th-semester BSCS student at Bahria University. I love learning about AI, working on real-world projects, and challenging myself with new technology. Hailing from Islamabad, I appreciate balance between nature and technology."
                  : "Long press to view more...",
              style: const TextStyle(fontSize: 16),
              textAlign: TextAlign.center,
            ),
          ),
        ),
      ),
    );
  }
}
```

---

## 🖼️ Output

* ✅ Splash screen with double-tap navigation
* ✅ Tab layout with gesture-controlled navigation
* ✅ Long-press reveals new screens and content

---

## 📌 Conclusion

* Applied `GestureDetector` for `onDoubleTap` and `onLongPress`
* Created multi-screen interaction using `Navigator`
* Improved user interaction through gesture-based navigation
* Used tabs and clean UI to structure the app

---

