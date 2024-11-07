# Go ChatGPT API Client

A simple Go client for interacting with the OpenAI ChatGPT API. This client allows you to send a chat conversation as input and receive responses from the ChatGPT API.

## Features

- Sends requests to the OpenAI ChatGPT API to interact with the model.
- Supports setting up a conversation with multiple messages.
- Lightweight and uses Go’s standard library.

## Requirements

- Go 1.16 or higher
- An OpenAI API key

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/SosoTaE/go-chatgpt-client.git
   cd go-chatgpt-client
   ```

2. **Set up your API key**:  
   Replace `apiKey := "sk-proj-XXXX..."` in `main()` with your actual OpenAI API key.

## Usage

### Running the Example

The example in `main.go` demonstrates how to create a simple conversation with the ChatGPT model.

1. **Initialize a ChatGPT instance**:
   ```go
   chatGPT := NewChatGPT("your-openai-api-key")
   ```

2. **Create a chat request**:
   ```go
   requestBody := ChatRequest{
       Model: "gpt-3.5-turbo", // or "gpt-4" if using the GPT-4 model
       Messages: []Message{
           {Role: "system", Content: "You are ChatGPT, a helpful assistant."},
           {Role: "user", Content: "Hello, how are you?"},
       },
   }
   ```

3. **Send the request and receive the response**:
   ```go
   chatResponse, err := chatGPT.Request(requestBody)
   if err != nil {
       panic(err)
   }
   fmt.Println(chatResponse.Choices[0].Message.Content)
   ```

### Example Output

When you run the example code, the output might look like:
```
Hello! I'm here to help you. How can I assist you today?
```

## Code Structure

- **Message struct**: Represents a single message in the chat conversation, with a role (`"system"`, `"user"`, or `"assistant"`) and content.
- **ChatRequest struct**: Defines the request payload to send to the ChatGPT API.
- **ChatResponse struct**: Defines the structure for parsing the ChatGPT API's response.
- **ChatGPT struct**: Contains the API key and URL required for sending requests to the ChatGPT API.
- **NewChatGPT(apiKey string)**: Constructor function to create a `ChatGPT` instance with the provided API key.
- **Request(request ChatRequest)**: Sends a request to the ChatGPT API and returns the `ChatResponse` with the assistant's reply.

## Error Handling

If the request fails or if the response cannot be parsed, the `Request` function returns an error.

## License

This project is licensed under the MIT License.

## Contributing

Feel free to submit issues, fork the repository, and make a pull request if you'd like to contribute!

---

