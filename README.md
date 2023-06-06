# Firestore Session Storage

This package implements the `SessionStorage` interface to work with Firestore database.

```js
import {initializeApp, cert} from 'firebase-admin/app'
import {getFirestore} from 'firebase-admin/firestore'
import {shopifyApp} from '@shopify/shopify-app-express';
import {FirestoreSessionStorage} from '@shopify/shopify-app-session-storage-memory';

/* Initialize firestore */
const firebaseApp = initializeApp({
  credential: cert('/path/to/service-account.json'),
})
const firestore = getFirestore(firebaseApp)

// ---------------------------

/* Pass the reference */
const shopify = shopifyApp({
  sessionStorage: new FirestoreSessionStorage({
    firestore: firestore, // this is required
    // collection: 'shopify_sessions' // optional - defaults to `shopify_sessions`
  }),
  // ...
});
```
