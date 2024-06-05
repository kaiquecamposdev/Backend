# API Video Load 🎬

This project is a video AI completion application that empowers users to upload videos and generate AI-generated content based on the selected video. It offers functionalities such as selecting prompts, adjusting temperature, and handling API communication, streamlining the video content creation process. The core value proposition lies in augmenting video content creation by leveraging AI capabilities, saving users time and effort in generating engaging and creative content.

## Technologies Used 💻

- **Node.js:**  JavaScript runtime environment for server-side development.
- **Fastify:**  Fast and lightweight web framework for Node.js.
- **TypeScript:**  Statically typed language for JavaScript.
- **Vite:** Fast development server and build tool for frontend development.
- **Prisma:**  ORM for Node.js and TypeScript.
- **Ffmpeg:**  Command-line tool for video and audio processing.
- **OpenAI API:**  AI model for generating text and code.

## Installation 🚀

**1. Clone the api-videoload:**
   ```bash
   git clone https://github.com/kaiquecamposdev/api-videoload
   ```
   or
   ```bash
   gh repo clone kaiquecamposdev/api-videoload
   ```

**2. Install the dependencies:**
   ```bash
   cd api-videoload && npm install
   ```

**3. Configure the OpenAI API Key:**
  - Create a .env file in the root of your project.
  - Add the following line to your .env file, replacing YOUR_OPENAI_API_KEY with your actual OpenAI API key:
  ```env
  OPENAI_API_KEY=YOUR_OPENAI_API_KEY
  ```

**4. Populating the database:**
  ```bash
  npm run prisma seed
  ```

**5. Run application:**
  ```bash
  npm run dev
  ```
**6. Access the application at `http://localhost:8000`**

## Endpoints 🔗

### Video Controller

- **Upload a video:**

  ```bash
  Endpoint: /videos
  Method: POST
  Request Body: Multipart form data with a `file` field containing an MP3 file. 
  Response: 
    - 201 Created: Returns the created video object.
    - 400 Bad Request:  If the file is missing or has an invalid format. 
  Description: Uploads a video file. The request body must include a file field with an MP3 file.
  ```

- **Get all videos:**

  ```bash
  Endpoint: /videos
  Method: GET
  Response: 
    - 200 OK: Returns an array of video objects.
    - 404 Not Found: If no videos are found. 
  Description: Returns a list of all videos.
  ```

### Prompt Controller

- **Get all prompts:**

  ```bash
  Endpoint: /prompts
  Method: GET
  Response: 
    - 200 OK: Returns an array of prompt objects.
    - 404 Not Found: If no prompts are found. 
  Description: Returns a list of all available prompts.
  ```

### AI Completion Controller

- **Generate AI completion:**

  ```bash
  Endpoint: /ai/complete
  Method: POST
  Body:  
    {
      "videoId": "uuid", // UUID of the video
      "prompt": "Your prompt with {transcription} placeholder", // Prompt to use, using {transcription} as a placeholder for the video transcription
      "temperature": 0.5 // Temperature for the AI model (optional, defaults to 0.5)
    }
  Response: 
    - 200 OK: Streams the generated text content.
    - 400 Bad Request: If the videoId is invalid or if the video transcription is not yet generated. 
  Description: Generates AI-generated content based on a video transcription. The request body must include the videoId, a prompt, and an optional temperature value.
  ```

### Transcription Controller

- **Generate transcription:**

  ```bash
  Endpoint: /videos/:videoId/transcription
  Method: POST
  Body:  
    {
      "prompt": "Optional prompt for the transcription" 
    }
  Response: 
    - 201 Created: Returns the generated transcription.
    - 400 Bad Request: If the videoId is invalid. 
  Description: Generates a transcription for a video. The videoId must be provided in the URL, and the request body can optionally include a prompt.
  ```

## Contributing 🤝
Contributions to the project are welcome! Feel free to open issues or submit pull requests.

## License 📝
This project is licensed under the [MIT License](./LICENSE).

