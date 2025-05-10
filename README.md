# My prodject
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Одноэкранное приложение',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: HomeScreen(),
    );
  }
}

class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Приложение с карточками товаров'),
      ),
      body: SingleChildScrollView(
        child: Column(
          children: [
            ProductCard(
              imageUrl: 'https://via.placeholder.com/150',
              localImagePath: 'assets/local_image.png', // Убедитесь, что это изображение существует в папке assets
              title: 'Товар 1',
            ),
            ProductCard(
              imageUrl: 'https://via.placeholder.com/150',
              localImagePath: 'assets/local_image.png',
              title: 'Товар 2',
            ),
            ProductCard(
              imageUrl: 'https://via.placeholder.com/150',
              localImagePath: 'assets/local_image.png',
              title: 'Товар 3',
            ),
          ],
        ),
      ),
    );
  }
}

class ProductCard extends StatefulWidget {
  final String imageUrl;
  final String localImagePath;
  final String title;

  ProductCard({
    required this.imageUrl,
    required this.localImagePath,
    required this.title,
  });

  @override
  _ProductCardState createState() => _ProductCardState();
}

class _ProductCardState extends State<ProductCard> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Card(
      margin: EdgeInsets.all(10),
      child: Column(
        children: [
          Image.network(widget.imageUrl),
          Image.asset(widget.localImagePath, height: 100),
          Padding(
            padding: const EdgeInsets.all(8.0),
            child: Text(
              widget.title,
              style: TextStyle(fontSize: 20),
            ),
          ),
          Row(
            mainAxisAlignment: MainAxisAlignment.spaceAround,
            children: [
              Text('Количество: $_counter'),
              ElevatedButton(
                onPressed: _incrementCounter,
                child: Text('Добавить'),
              ),
            ],
          ),
        ],
      ),
    );
  }
}
