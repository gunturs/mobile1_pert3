## Mobile 1 Pertemuan4: Navigator
Navigator merupakan cara untuk berpindah dari satu page ke page lain, ada bebrapa cara yang bisa digunakan yaitu

>## Cara 1: Dengan Menggunakan Route
Metode navigator ini dengan menentukan route masing-masing page pada bagian materialApp dan kemudian dapat setiap halaman yang akan dituju akan panggil sesuai nama route.
dengan metode ini  jumlah halaman tidak terbatas.
langsung saja dipraktekan dengan membuat 2 buah class yaitu

Class: Halutama
```dart
class Halutama extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return new Scaffold(
      appBar: AppBar(
        leading:IconButton(color:Colors.white,icon: Icon(IconData(59530, fontFamily: 'MaterialIcons')),onPressed:null,),
        title: Text('Home'),
      ),
      body: new Center(
        child: new Container(
          child: new IconButton(
            icon: Icon(IconData(58128, fontFamily: 'MaterialIcons'),size:30.00,color:Colors.orangeAccent),
            onPressed: () {   },
          ),
        ),
      ),
    );
  }
}

```


Class:Haldua
```dart
class Haldua extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return new Scaffold(
      appBar: AppBar(
        title: Text('Navigasi'),
      ),
      body: new Center(
        child: new Container(
          child: new IconButton(
            icon: Icon(Icons.place, size: 40.0),
            onPressed: null,
          ),
        ),
      ),
    );
  }
}
```

dalam class Halutama terdapat sebuah Iconbutton yang nantinya bertujuan sebagai triger untuk menuju halaman selanjutnya,, jika diclick maka even onPressed yany terdapat pada tombol akan mengakses route dari class yang dituju dalam contoh, setelah duah class tersebut di buat maka kita atur route nya pada maerialApp seperti progra dibawah ini.

```dart

void main() {
  runApp(new MaterialApp(
    debugShowCheckedModeBanner: false,
    home: new Halutama(),
    
    title: 'Navigasi',
    
    //Atur route
    routes: <String, WidgetBuilder>{
      '/Halutama': (BuildContext context) => new Halutama(),
      '/Haldua': (BuildContext context) => new Haldua(),
    },
  ));
}
```
pada program diatas telah disetting bahwa untuk class pertama diberi root '/Halutama' dan class kedua '/Haldua, selanjutnya tinggal tambahkan pemanggil pada masing masing tombol dalam class
Class hal utama
```dart
onPressed: () {
              Navigator.pushNamed(context, '/Haldua');
            },

```
menggunakan metode dengan route ini dapat menjalankan navigasi lebih dari dua page

>## Cara 2: a new screen and back
Penggunaan metode ini hanya berlaku untuk sekali perpindahan Page lalu kembali

Contoh:
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    debugShowCheckedModeBanner:false,
    home: FirstRoute(),
  ));
}

class FirstRoute extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Halaman Pertama'),
      ),
      body: Center(
        child: RaisedButton(
          child: Text('Open route'),
          onPressed: () {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => SecondRoute()),
            );
          },
        ),
      ),
    );
  }
}

class SecondRoute extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("Halaman Kedua"),
      ),
      body: Center(
        child: RaisedButton(
          onPressed: () {
            Navigator.pop(context);
          },
          child: Text('Go back!'),
        ),
      ),
    );
  }
}
```
