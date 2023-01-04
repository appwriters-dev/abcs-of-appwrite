---
id: ls01-registering-user
title: Registering User
---

Appwrite provides [Account](https://appwrite.io/docs/client/account) service to manage user accounts and authentication on your applications. You use this ervice to register users to your application, authenticat users, and manage user profiles. Let's learn how to register user using the Account service.

## Registering Users

In any application, to authenticate users, you first need to register them. That will create a new account for your user. There are several ways you can register user in Appwrite. 

The easiest way to create an account is by using the `create` method. This method takes `email`, `password`, and optional `name` as input and creates a new account for your user.

```dart
final user = await account.create(
  email: 'user1@appwrite.io',
  password: 'password',
  name: 'User 1',
);
```

Usually in you application, you create a form to collect user's email, password and name. You can then use the form data to create a new account for your user. Let's see how we can do that in Flutter in the example below.

```dart
import 'package:flutter/material.dart';
import './my_appwrite_services.dart' as appwrite; // this is where you have setup Appwrite SDK and services

class SignUpForm extends StatefulWidget {
  @override
  _SignUpFormState createState() => _SignUpFormState();
}

class _SignUpFormState extends State<SignUpForm> {
  final _formKey = GlobalKey<FormState>();
  String _name;
  String _email;
  String _password;

  @override
  Widget build(BuildContext context) {
    return Form(
      key: _formKey,
      child: ListView(
        padding: const EdgeInsets.all(16.0),
        children: [
          TextFormField(
            decoration: const InputDecoration(
              hintText: 'Enter your name (Optional)',
            ),
            onSaved: (value) => _name = value,
          ),
          TextFormField(
            decoration: const InputDecoration(
              hintText: 'Enter your email',
            ),
            validator: (value) {
              if (value.isEmpty) {
                return 'Please enter your email';
              }
              return null;
            },
            onSaved: (value) => _email = value,
          ),
          TextFormField(
            obscureText: true,
            decoration: const InputDecoration(
              hintText: 'Enter your password',
            ),
            validator: (value) {
              if (value.isEmpty) {
                return 'Please enter your password';
              }
              return null;
            },
            onSaved: (value) => _password = value,
          ),
          Padding(
            padding: const EdgeInsets.symmetric(vertical: 16.0),
            child: ElevatedButton(
              onPressed: () async {
                if (_formKey.currentState.validate()) {
                  _formKey.currentState.save();
                  final user = await appwrite.account.create(
                    email: _email,
                    password: _password,
                    name: _name,
                  );
                }
              },
              child: Text('Sign Up'),
            ),
          ),
        ],
      ),
    );
  }
}
```

Registering user is the first step. In order to authenticate your user, you must create a session for your user. Let's learn how to do that in the next section.

