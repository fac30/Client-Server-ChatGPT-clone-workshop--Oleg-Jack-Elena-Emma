# Client-Server-ChatGPT-clone-workshop--Oleg-Jack-Elena-Emma

## Re-engineered the app to use the client-server architecture for the improved security and scalability

<img width="1000" alt="Screenshot 2024-02-02 at 17 56 32" src="https://github.com/fac30/Client-Server-ChatGPT-clone-workshop--Oleg-Jack-Elena-Emma/assets/113034133/9fa2f5cf-b99f-49f9-a657-8fddc03b6a9a">

<br><br>

Re-engineering the app originally implememted as a front-end only here: https://github.com/fac30/Front-end-ChatGPT-clone-workshop--Oleg-Jack-Elena-Emma.git

In this project, functions of storage of the API Key, processing the the HTTP requests,  communicating with API and retrieving the results transfered to the backend **Node.js** server

<br>
---
<br>

Here's an overview of the **Node.js** script:

1. **Dependencies**: It uses several Node.js packages, including `dotenv` for managing environment variables, `express` for creating the server, `body-parser` for parsing request bodies, `node-fetch` for making HTTP requests, and `cors` to enable Cross-Origin Resource Sharing.

2. **Configuration**: The server loads environment variables from a `.env` file using `dotenv`. It sets up an Express app, uses `body-parser` and `cors`, and serves static files from the 'public' directory.

3. **API Key and Question History**: It retrieves the OpenAI API key from the environment variables and initializes `questionHistory` as an empty array.

4. **Endpoint `/api/chat`**: Listens for POST requests on the '/api/chat' endpoint. It expects a JSON payload containing a `conversation` property, which is an array of messages. The server then makes a request to the OpenAI GPT-3.5 API with the provided conversation and logs the request and response data.

5. **Handling OpenAI API Response**: If the API request is successful, it extracts the answer from the response and includes the `questionHistory` in the server response. If the API request fails, it logs an error and sends a 500 Internal Server Error response.

6. **Server Start**: Finally, the server listens on the specified port, and a message is logged indicating the server is running.

<br>
---
<br>

Here's a summary of how client-side interaction works:

1. **Client-Side (`index.html` and embedded JavaScript)**:
   - The user interacts with the chat interface in the browser.
   - The client-side JavaScript code maintains a local variable `questionHistory` to keep track of the conversation history within the user's browser.
   - When a user submits a question through the form, the client-side code sends this question, along with the current `questionHistory`, to the server for processing.

2. **Server-Side (`server.js`)**:
   - The server receives incoming requests to the `/api/chat` endpoint.
   - It extracts the conversation history (`conversation` array) from the request body.
   - The server makes a call to the OpenAI GPT-3.5 API using the provided conversation history.
   - The OpenAI API generates a response, and the server processes this response.
   - The server may log information, handle errors, and then constructs a response containing the answer from the OpenAI API and the `questionHistory`.

3. **Client-Side (Response Handling)**:
   - The client-side JavaScript code receives the response from the server.
   - It updates the `questionHistory` variable on the client side with the new question and answer from the user and OpenAI API.
   - It updates the displayed conversation history on the webpage.

The `questionHistory` on the client side is primarily used for maintaining context, providing a better user experience, and persisting the conversation across page reloads. It's not directly used on the server side for processing requests but is included in the request payload to provide context to the OpenAI GPT-3.5 API. The server then sends the updated `questionHistory` back to the client in the response.
