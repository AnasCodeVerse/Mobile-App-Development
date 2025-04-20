# 📘 Lab 3 – Creating Simple Flutter Application

**Course:** Mobile Application Development Lab (CSL-341)  
**Student Name:** Muhammad Anas  
**Enrollment No.:** 01-134222-089  
**Class & Section:** BSCS-6B  
**Department of Computer Science – Bahria University Islamabad**

---

## 🎯 Objectives:
- Creating simple Flutter applications using Visual Studio Code.

## 🛠️ Tools Used:
- Visual Studio Code (VS Code)

---

## ✅ Task 1: App with Basic UI

### Requirements:
- Background color: White
- AppBar with blueAccent background color
- AppBar title in white color

---

## ✅ Task 2: Self Introduction in the App

### Requirements:
- One paragraph introducing yourself
- Your name should be **bold**
- Your qualities should be *italic*
- Paragraph must be **centered on the screen**

---

## ✅ Task 3: Add a Star Icon

### Requirements:
- Add a yellow star icon below the paragraph

---

## 🔹 Complete Flutter Code:

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        backgroundColor: Colors.white, // Background color white
        appBar: AppBar(
          title: Text(
            'Introduction App',
            style: TextStyle(color: Colors.white), // Title in white color
          ),
          backgroundColor: Colors.blueAccent, // AppBar background color
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              // Introduction Paragraph
              Padding(
                padding: EdgeInsets.all(16.0),
                child: RichText(
                  textAlign: TextAlign.center,
                  text: TextSpan(
                    style: TextStyle(color: Colors.black, fontSize: 18),
                    children: [
                      TextSpan(text: "My name is "),
                      TextSpan(
                        text: "Muhammad Anas",
                        style: TextStyle(fontWeight: FontWeight.bold),
                      ),
                      TextSpan(text: ", a Computer Science student at "),
                      TextSpan(
                        text: "Bahria University",
                        style: TextStyle(fontWeight: FontWeight.bold),
                      ),
                      TextSpan(
                        text:
                            ". I am passionate about coding, problem-solving, and leadership.\n\n",
                      ),
                      TextSpan(text: "In my free time, I enjoy "),
                      TextSpan(
                        text:
                            "learning new technologies and applying them in real-world projects",
                        style: TextStyle(
                          fontStyle: FontStyle.italic,
                        ),
                      ),
                    ],
                  ),
                ),
              ),

              // Star Icon
              Icon(
                Icons.star,
                size: 40,
                color: Colors.yellow,
              ),
            ],
          ),
        ),
      ),
    );
  }
}
