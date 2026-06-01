AIChat is a full-stack AI chatbot application built using **Spring Boot**, **Spring AI**, **Ollama**, and **React + Vite**.  
The backend connects with a locally running Ollama model and exposes an API that the frontend can use to send user prompts and display AI-generated responses.

## Tech Stack

### Backend
- Java 21
- Spring Boot
- Spring AI
- Ollama
- Maven

### Frontend
- React
- Vite
- JavaScript
- CSS

## Features

- AI chatbot interface
- Backend API for sending prompts to Ollama
- Integration with Spring AI `ChatClient`
- React-based frontend
- Local LLM support using Ollama
- Simple full-stack project structure

## Project Structure

```

AIChat/
├── AIChat/
│   ├── src/main/java/com/example/AIChat/
│   │   ├── AiChatApplication.java
│   │   └── OllamaController.java
│   │
│   ├── src/main/Frontend/frontend/
│   │   ├── src/
│   │   ├── public/
│   │   ├── package.json
│   │   └── vite.config.js
│   │
│   ├── pom.xml
│   └── mvnw

````

## API Endpoint

The backend exposes the following endpoint:

```http
GET /api/ollama/{message}
````

Example:

```http
http://localhost:8080/api/ollama/Hello
```

This sends the message to the Ollama model and returns the AI response.

## Prerequisites

Make sure you have installed:

* Java 21
* Maven
* Node.js
* npm
* Ollama

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Deepshikha-Mohanty/AIChat.git
cd AIChat/AIChat
```

### 2. Start Ollama

Install and run Ollama, then pull a model:

```bash
ollama pull llama3
ollama run llama3
```

### 3. Run Backend

```bash
./mvnw spring-boot:run
```

For Windows:

```bash
mvnw.cmd spring-boot:run
```

Backend will run on:

```http
http://localhost:8080
```

### 4. Run Frontend

```bash
cd src/main/Frontend/frontend
npm install
npm run dev
```

Frontend will run on:

```http
http://localhost:5173
```

## Backend Code Flow

1. User sends a message from the frontend.
2. The frontend calls the Spring Boot API.
3. `OllamaController` receives the message.
4. Spring AI `ChatClient` sends the prompt to Ollama.
5. Ollama generates a response.
6. The response is returned to the frontend.

## Main Backend Endpoint

```java
@GetMapping("/{message}")
public ResponseEntity getAnswer(@PathVariable String message) {
    ChatResponse chatResponse = chatClient
            .prompt(message)
            .call()
            .chatResponse();

    String response = chatResponse.getResult().getOutput().getText();
    return ResponseEntity.ok(response);
}
```

## Future Enhancements

* Add chat history
* Add database support
* Improve frontend UI
* Add loading animation
* Add model selection option
* Add authentication
* Deploy frontend and backend

## Author

**Deepshikha Mohanty**

GitHub: [Deepshikha-Mohanty](https://github.com/Deepshikha-Mohanty)

## License

This project is open-source and available for learning and development purposes.

```
```

Your repo currently has a Spring Boot project with a React/Vite frontend, and the backend uses Spring AI with Ollama through `/api/ollama/{message}`. ([GitHub][1])

[1]: https://github.com/Deepshikha-Mohanty/AIChat/tree/main/AIChat/src/main/Frontend/frontend "AIChat/AIChat/src/main/Frontend/frontend at main · Deepshikha-Mohanty/AIChat · GitHub"
