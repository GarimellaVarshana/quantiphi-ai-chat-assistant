# Nova AI Chat Assistant — Quantiphi Vibe Coding Project

A full-stack AI chat application built with React, Express, MongoDB, and the OpenAI API.

## Features
- User/assistant chat bubbles and streaming responses (Server-Sent Events)
- Saved conversation history in MongoDB Atlas
- Professional, Casual, and Concise response tones
- Regenerate the latest assistant response
- Export the current conversation as a `.txt` file
- Delete conversations
- Responsive desktop/mobile layout

## Requirements
- Node.js 18+
- MongoDB Atlas database (or local MongoDB)
- OpenAI API key with API access enabled

## Setup

1. Extract the project ZIP and open its folder in a terminal or VS Code.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Copy `.env.example` to `.env`.
4. Add your credentials to `.env`:
   ```env
   PORT=5000
   MONGODB_URI=your_mongodb_atlas_connection_string
   OPENAI_API_KEY=your_openai_api_key
   OPENAI_MODEL=gpt-4o-mini
   CLIENT_ORIGIN=http://localhost:5173
   ```
5. In MongoDB Atlas, create a database user, allow your development IP in Network Access, and copy the connection string. Replace the username/password placeholders. Do not commit `.env`.
6. Start both frontend and backend:
   ```bash
   npm run dev
   ```
7. Open the Vite URL printed in the terminal (normally `http://localhost:5173`).

## Production build
```bash
npm run build
npm start
```
The API runs on port 5000. For production hosting, deploy the frontend and backend with the same-origin `/api` routing or configure a reverse proxy and update the frontend API base URL.

## API endpoints
- `GET /api/health` — service status
- `GET /api/conversations` — recent conversations
- `POST /api/conversations` — create a conversation
- `GET /api/conversations/:id` — load a conversation
- `DELETE /api/conversations/:id` — delete a conversation
- `PATCH /api/conversations/:id/tone` — update tone
- `POST /api/chat/stream` — stream an AI response

## Important security notes
- Keep API keys only in the backend `.env`; never put secrets in React/Vite variables.
- Add authentication, per-user data ownership, rate limiting, and request logging before exposing this publicly.
- Restrict MongoDB network access and use a strong database password.
- The app currently assumes a single-user demo. Do not use it for private multi-user data without authentication and authorization.

## Vibe-coding demo checklist
1. Start the app and show the landing screen.
2. Send a prompt and demonstrate tokens streaming in.
3. Change tone to Casual or Concise and ask the same type of question.
4. Start another chat and show the history sidebar.
5. Reload the browser and open a saved chat to demonstrate MongoDB persistence.
6. Regenerate an answer and export a conversation.
7. Explain the flow: React UI → Express API → OpenAI streaming → MongoDB save → React renders tokens.
