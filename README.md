# Flutter-1
Practical no.1a
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

String savedUser = "";
String savedPass = "";

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: RegisterPage(),
      debugShowCheckedModeBanner: false,
    );
  }
}

class RegisterPage extends StatelessWidget {

  TextEditingController user = TextEditingController();
  TextEditingController pass = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Register")),

      body: Padding(
        padding: EdgeInsets.all(20),

        child: Column(
          children: [

            TextField(
              controller: user,
              decoration: InputDecoration(labelText: "Username"),
            ),

            TextField(
              controller: pass,
              obscureText: true,
              decoration: InputDecoration(labelText: "Password"),
            ),

            SizedBox(height: 20),

            ElevatedButton(
              child: Text("Register"),
              onPressed: () {

                savedUser = user.text;
                savedPass = pass.text;

                Navigator.push(
                  context,
                  MaterialPageRoute(builder: (context) => LoginPage()),
                );
              },
            )
          ],
        ),
      ),
    );
  }
}

class LoginPage extends StatelessWidget {

  TextEditingController user = TextEditingController();
  TextEditingController pass = TextEditingController();

  @override
  Widget build(BuildContext context) {

    return Scaffold(
      appBar: AppBar(title: Text("Login")),

      body: Padding(
        padding: EdgeInsets.all(20),

        child: Column(
          children: [

            TextField(
              controller: user,
              decoration: InputDecoration(labelText: "Username"),
            ),

            TextField(
              controller: pass,
              obscureText: true,
              decoration: InputDecoration(labelText: "Password"),
            ),

            SizedBox(height: 20),

            ElevatedButton(
              child: Text("Login"),
              onPressed: () {

                if (user.text == savedUser && pass.text == savedPass) {
                  ScaffoldMessenger.of(context).showSnackBar(
                    SnackBar(content: Text("Login Successful")),
                  );
                } else {
                  ScaffoldMessenger.of(context).showSnackBar(
                    SnackBar(content: Text("Wrong Username or Password")),
                  );
                }

              },
            )

          ],
        ),
      ),
    );
  }
}
