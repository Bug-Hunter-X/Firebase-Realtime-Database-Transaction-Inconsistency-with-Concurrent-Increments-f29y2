# Firebase Realtime Database Transaction Inconsistency

This repository demonstrates an uncommon bug in Firebase's Realtime Database related to transaction inconsistencies when multiple clients concurrently attempt to increment a counter.  The problem arises from race conditions and the potential for transactions to fail due to concurrent writes, leading to an incorrect counter value.

## Bug Description
When multiple clients run the provided code (bug.js), they each attempt to increment a counter in the Realtime Database using a transaction.  However, due to the concurrent nature of the operations, some increments might be lost, causing the final counter value to be lower than expected.

## Solution
The solution (bugSolution.js) utilizes a more robust approach by using server-side timestamps and atomic operations to ensure accurate counter updates regardless of concurrency. This eliminates the need for transactions and resolves the inconsistency issue.

## How to Reproduce
1. Clone this repository.
2. Create a Firebase project and configure the `firebase.json` file.
3. Set up a Realtime Database instance.
4. Open multiple instances of the `bug.js` file in your browser and observe the counter value.  You will likely see inconsistencies.
5. Open multiple instances of the `bugSolution.js` and see that the counter increments accurately.

## Note
The solution may require adjustments depending on your specific application and how you store data.