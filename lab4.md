

---

````markdown
# 📘 Lab 4 – Custom Widgets and Navigation in Flutter

**Course:** Mobile Application Development Lab (CSL-341)  
**Student Name:** Muhammad Anas  
**Enrollment No.:** 01-134222-089  
**Class & Section:** BSCS-6B  
**Department of Computer Science – Bahria University Islamabad**

---

## 🎯 Objective
To design different screens of a Flutter application using custom widgets and implement navigation between them.

---

## 🛠️ Tools Used
- Visual Studio Code (VS Code)
- Dart & Flutter SDK

---

## ✅ Task: Create a Multi-Screen Flutter App

### 🔹 Requirements:
1. Create multiple screens using separate Dart files.
2. Add buttons to navigate between screens.
3. Use custom widgets to make the UI reusable.
4. On one screen, show an image.
5. On another screen, build a form with validation.

---

## 🔹 Main Code Files

---

### 📄 `main.dart`

```dart
import 'package:flutter/material.dart';
import 'screens/home_screen.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Lab 4 Flutter App',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const HomeScreen(),
    );
  }
}
````

---

### 📄 `home_screen.dart`

```dart
import 'package:flutter/material.dart';
import 'screen1.dart';
import 'screen2.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Home Screen")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            CustomButton(
              text: "Go to Screen 1",
              onPressed: () {
                Navigator.push(
                  context,
                  MaterialPageRoute(builder: (context) => const Screen1()),
                );
              },
            ),
            const SizedBox(height: 20),
            CustomButton(
              text: "Go to Screen 2",
              onPressed: () {
                Navigator.push(
                  context,
                  MaterialPageRoute(builder: (context) => const Screen2()),
                );
              },
            ),
          ],
        ),
      ),
    );
  }
}

class CustomButton extends StatelessWidget {
  final String text;
  final VoidCallback onPressed;

  const CustomButton({super.key, required this.text, required this.onPressed});

  @override
  Widget build(BuildContext context) {
    return ElevatedButton(
      onPressed: onPressed,
      style: ElevatedButton.styleFrom(
        padding: const EdgeInsets.symmetric(horizontal: 30, vertical: 15),
      ),
      child: Text(text),
    );
  }
}
```

---

### 📄 `screen1.dart`

```dart
import 'package:flutter/material.dart';

class Screen1 extends StatelessWidget {
  const Screen1({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Screen 1")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Text(
              "Welcome to Screen 1",
              style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 20),
            Image.network(
              'https://source.unsplash.com/200x200/?nature',
              width: 200,
              height: 200,
              fit: BoxFit.cover,
            ),
          ],
        ),
      ),
    );
  }
}
```

---

### 📄 `screen2.dart` (With Form)

```dart
import 'package:flutter/material.dart';

class Screen2 extends StatefulWidget {
  const Screen2({super.key});

  @override
  _Screen2State createState() => _Screen2State();
}

class _Screen2State extends State<Screen2> {
  final _formKey = GlobalKey<FormState>();
  final TextEditingController nameController = TextEditingController();
  final TextEditingController emailController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Screen 2 - Form")),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Form(
          key: _formKey,
          child: Column(
            children: [
              TextFormField(
                controller: nameController,
                decoration: const InputDecoration(
                  labelText: "Enter your name",
                  border: OutlineInputBorder(),
                ),
                validator: (value) {
                  if (value == null || value.isEmpty) {
                    return "Name is required";
                  }
                  return null;
                },
              ),
              const SizedBox(height: 20),
              TextFormField(
                controller: emailController,
                decoration: const InputDecoration(
                  labelText: "Enter your email",
                  border: OutlineInputBorder(),
                ),
                validator: (value) {
                  if (value == null || value.isEmpty) {
                    return "Email is required";
                  }
                  return null;
                },
              ),
              const SizedBox(height: 20),
              ElevatedButton(
                onPressed: () {
                  if (_formKey.currentState!.validate()) {
                    ScaffoldMessenger.of(context).showSnackBar(
                      const SnackBar(content: Text("Form Submitted")),
                    );
                  }
                },
                child: const Text("Submit"),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

---

## ✅ Output

* ✅ Home screen with two buttons for navigation
* ✅ Screen 1 displays a bold welcome text and a nature image
* ✅ Screen 2 shows a form with fields for name and email, along with validation and success message

---

## 📌 Conclusion

* Built a Flutter app with multiple screens
* Implemented custom reusable widgets
* Used `Navigator.push()` to navigate between screens
* Added form with validation using `TextFormField`

---


