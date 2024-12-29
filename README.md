# Express.js JSON Body Parsing Bug

This repository demonstrates a common issue in Express.js applications where JSON request bodies are not parsed correctly if the `Content-Type` header is missing or incorrect.  The server receives an empty `req.body` object, leading to unexpected behavior or errors in request handling.

## Bug Description

The `bug.js` file contains an Express.js application that attempts to parse JSON data from POST requests. However, if the client doesn't set the `Content-Type` header to `application/json`, or sets it to an incorrect value, the request body will be empty.

## Solution

The `bugSolution.js` file provides a corrected version that addresses the issue by explicitly checking and handling the `Content-Type` header.  If the header is missing or incorrect, it returns an appropriate error response.  Otherwise, it continues to parse and process the JSON body.

## How to Reproduce

1. Clone this repository.
2. Run `npm install` to install Express.js.
3. Run `node bug.js` to start the buggy server.
4. Send a POST request to `/data` using a tool like Postman or curl, *without* setting the `Content-Type` header or setting it to an incorrect value. Observe the empty `req.body` in the server's console log and the response.
5. Run `node bugSolution.js` to start the corrected server.
6. Repeat step 4. The server will now handle the missing or incorrect header appropriately.

## Lessons Learned

- Always validate and handle the `Content-Type` header in your Express.js applications when expecting JSON request bodies.
- Robust error handling should be implemented to gracefully manage situations where the request data is not in the expected format.