# firestore-auth-tuts
first hand firestore auth tuts


```yml
service cloud.firestore {
  match /databases/{database}/documents {
    // match /{document=**} {
    //   allow read, write;
    // }
    
    // https://firebase.google.com/docs/firestore/security/rules-structure
    
    // match logged in user doc in users collection
    match /users/{userId} {
    	allow create: if request.auth.uid != null;
      allow read: if request.auth.uid == userId;
    }
    
    // match docs in the guides collection
    match /guides/{guideId} {
    	allow read: if request.auth.uid != null;
      allow write: if request.auth.token.admin == true;
    }
  }
}
```
