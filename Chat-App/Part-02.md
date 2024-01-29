## Adding a remote db

- Firebase database
- Go to `NATIVE MODE`
- Go to rules
- Add the package `flutter pub add cloud_firestore`

```

 rules_version = '2';

service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}

```

## Sending data to firestore

- Main code

```dart

// Firebase Firestore
        FirebaseFirestore.instance
            .collection('users')
            .doc(userCredentials.user!.uid)
            .set({"username": "to be done", "email": _enteredEmail});

```

> 

<details>
  <summary>Code</summary>

```dart



```
  
</details>












<details>
  <summary>Code</summary>

```dart

```
  
</details>




v
