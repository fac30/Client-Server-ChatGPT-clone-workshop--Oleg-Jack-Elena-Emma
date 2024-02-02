# Client-Server-ChatGPT-clone-workshop--Oleg-Jack-Elena-Emma

## Re-engineered the app to use the client-server architecture for the improved security and scalability

<img width="1000" alt="Screenshot 2024-02-02 at 17 56 32" src="https://github.com/fac30/Client-Server-ChatGPT-clone-workshop--Oleg-Jack-Elena-Emma/assets/113034133/9fa2f5cf-b99f-49f9-a657-8fddc03b6a9a">

<br><br>

Re-engineering the app originally implememted as a front-end only here: https://github.com/fac30/Front-end-ChatGPT-clone-workshop--Oleg-Jack-Elena-Emma.git

In this project, functions of storage of the API Key, processing the the HTTP requests,  communicating with API and retrieving the results transfered to the backend **Node.js** server

<br><br>

Here's an overview of the code:

1. **Dependencies**: It uses several Node.js packages, including `dotenv` for managing environment variables, `express` for creating the server, `body-parser` for parsing request bodies, `node-fetch` for making HTTP requests, and `cors` to enable Cross-Origin Resource Sharing.

2. **Configuration**: The server loads environment variables from a `.env` file using `dotenv`. It sets up an Express app, uses `body-parser` and `cors`, and serves static files from the 'public' directory.

3. **API Key and Question History**: It retrieves the OpenAI API key from the environment variables and initializes `questionHistory` as an empty array.

4. **Endpoint `/api/chat`**: Listens for POST requests on the '/api/chat' endpoint. It expects a JSON payload containing a `conversation` property, which is an array of messages. The server then makes a request to the OpenAI GPT-3.5 API with the provided conversation and logs the request and response data.

5. **Handling OpenAI API Response**: If the API request is successful, it extracts the answer from the response and includes the `questionHistory` in the server response. If the API request fails, it logs an error and sends a 500 Internal Server Error response.

6. **Server Start**: Finally, the server listens on the specified port, and a message is logged indicating the server is running.

