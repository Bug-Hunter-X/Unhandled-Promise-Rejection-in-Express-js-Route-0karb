# Unhandled Promise Rejection in Express.js Route

This repository demonstrates a common error in Node.js Express.js applications: unhandled promise rejections within asynchronous route handlers.  The bug results in the server silently failing to respond correctly to client requests when errors occur during asynchronous operations.

The `bug.js` file shows the flawed code. The `bugSolution.js` file provides a corrected version with proper error handling.

## How to Reproduce

1. Clone this repository.
2. Navigate to the repository's directory.
3. Run `npm install express`
4. Run `node bug.js`
5. Make multiple requests to `http://localhost:3000/`.  Observe that roughly half of the requests will result in no response (the server will log the error, but will not send any response to the client). 
6. Repeat steps 4 and 5 with `node bugSolution.js`. Observe that the application sends appropriate error responses to the client.

## Solution

The solution involves using a `try...catch` block or a `.catch()` method to explicitly handle potential errors within asynchronous operations.  The corrected code provides a more robust and user-friendly experience by sending appropriate error responses to the client instead of silently failing.