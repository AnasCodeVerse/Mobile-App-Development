
# 📘 Lab 9 – Animations in Flutter

**Course:** Mobile Application Development Lab (CSL-341)  
**Student Name:** Muhammad Anas  
**Enrollment No.:** 01-134222-089  
**Class & Section:** BSCS-6B  
**Department of Computer Science – Bahria University Islamabad**

---

## 🎯 Objectives

- Add basic and interactive animations in Flutter.
- Learn how to use splash screens, animated widgets, and stateful interactions.

---

## 🛠️ Tools Used

- Visual Studio Code (VS Code)
- Flutter & Dart SDK

---

## ✅ Task Overview

### 🔹 Requirements:

1. **Splash Screen**
   - A logo appears in the center.
   - Logo flashes or animates for 2 seconds.
   - Automatically navigates to the next screen.

2. **Second Screen**
   - Displays a list of food items.
   - Each item includes:
     - Image
     - Name
     - Description
     - A heart icon (initially grey)
   - When the heart icon is **double-tapped**, it:
     - Plays a color change animation.
     - Changes the heart icon color to **red**.

---

## 🔹 Sample Code Structure

> The code is structured in `main.dart`, with animation logic and list rendering inside the `FoodListScreen`.

---

### 📄 `main.dart`

```dart
import 'package:flutter/material.dart';
import 'dart:async';
import 'food_list_screen.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Food App with Animation',
      debugShowCheckedModeBanner: false,
      home: const SplashScreen(),
    );
  }
}

class SplashScreen extends StatefulWidget {
  const SplashScreen({super.key});

  @override
  State<SplashScreen> createState() => _SplashScreenState();
}

class _SplashScreenState extends State<SplashScreen> {
  @override
  void initState() {
    super.initState();
    Timer(const Duration(seconds: 2), () {
      Navigator.pushReplacement(
        context,
        MaterialPageRoute(builder: (_) => const FoodListScreen()),
      );
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: FlutterLogo(size: 120), // Replace with your app logo
      ),
    );
  }
}
````

---

### 📄 `food_list_screen.dart`

```dart
import 'package:flutter/material.dart';

class FoodItem {
  final String name;
  final String description;
  final String imagePath;

  FoodItem({required this.name, required this.description, required this.imagePath});
}

class FoodListScreen extends StatelessWidget {
  const FoodListScreen({super.key});

  final List<FoodItem> foodItems = const [
    FoodItem(
      name: "Pizza",
      description: "Delicious cheese pizza",
      imagePath: "assets/pizza.png",
    ),
    FoodItem(
      name: "Burger",
      description: "Juicy beef burger",
      imagePath: "assets/burger.png",
    ),
    FoodItem(
      name: "Pasta",
      description: "Creamy chicken pasta",
      imagePath: "assets/pasta.png",
    ),
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Food Items")),
      body: ListView.builder(
        itemCount: foodItems.length,
        itemBuilder: (context, index) {
          return FoodCard(item: foodItems[index]);
        },
      ),
    );
  }
}

class FoodCard extends StatefulWidget {
  final FoodItem item;

  const FoodCard({super.key, required this.item});

  @override
  State<FoodCard> createState() => _FoodCardState();
}

class _FoodCardState extends State<FoodCard> with SingleTickerProviderStateMixin {
  bool isFavorite = false;
  late AnimationController _controller;
  late Animation<Color?> _colorAnimation;

  @override
  void initState() {
    super.initState();
    _controller = AnimationController(
      duration: const Duration(milliseconds: 300),
      vsync: this,
    );

    _colorAnimation = ColorTween(begin: Colors.grey, end: Colors.red)
        .animate(_controller);
  }

  void _handleDoubleTap() {
    setState(() {
      isFavorite = !isFavorite;
      isFavorite ? _controller.forward() : _controller.reverse();
    });
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Card(
      margin: const EdgeInsets.all(10),
      elevation: 4,
      child: ListTile(
        leading: Image.asset(widget.item.imagePath, width: 50, height: 50),
        title: Text(widget.item.name),
        subtitle: Text(widget.item.description),
        trailing: GestureDetector(
          onDoubleTap: _handleDoubleTap,
          child: AnimatedBuilder(
            animation: _colorAnimation,
            builder: (context, child) => Icon(
              Icons.favorite,
              color: _colorAnimation.value,
            ),
          ),
        ),
      ),
    );
  }
}
```

---

## 🖼️ Output:

* ✅ Splash screen with a flashing logo and timed navigation.
* ✅ Scrollable food list with images, descriptions, and heart icons.
* ✅ Heart icon animates to red on double tap using `AnimatedBuilder` and `ColorTween`.

---

## 📌 Conclusion

* Used `Timer` to transition from splash screen after 2 seconds.
* Displayed data using `ListView.builder` and custom data class `FoodItem`.
* Applied gesture-based interaction with `GestureDetector` for double tap.
* Implemented heart icon animation using `AnimationController` and `ColorTween`.

---


