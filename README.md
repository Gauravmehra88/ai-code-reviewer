# AI Code Reviewer

An AI-powered code review system that analyzes source code and provides structured review feedback including best practices, performance improvements, error detection, and suggested fixes. The system uses a React-based frontend for interactive code editing and a Node.js backend that integrates with Google Gemini for AI-driven review generation.

---

## 📌 Key Features

- **Interactive Code Editor** with syntax highlighting
- **AI-Based Code Review** powered by Gemini (`gemini-2.0-flash`)
- **Structured Review Output** including:
  - Error detection
  - Best practice suggestions
  - Performance improvements
  - Security considerations
  - Refactoring recommendations
- **Markdown Rendering** for clean and readable feedback
- **Two-Pane Layout** (Editor → AI Review Output)
- **Simple REST API Integration**

---

## 🏗️ System Architecture

```
┌────────────────┐      POST /ai/get-review      ┌────────────────────┐
│    React UI     │ ───────────────────────────> │  Node.js + Express  │
│ (Code Editor)   │                               │   (API Backend)     │
└────────────────┘      Markdown Response         └────────────────────┘
                                   │
                                   │ Uses Google Gemini API
                                   ▼
                           ┌──────────────────────┐
                           │   Gemini AI Model    │
                           │  gemini-2.0-flash    │
                           └──────────────────────┘
```

---

## 🧰 Tech Stack

### **Frontend**
- React 19
- Vite 6
- Axios
- PrismJS + Highlight.js
- react-simple-code-editor
- react-markdown + rehype-highlight

### **Backend**
- Node.js
- Express.js
- CORS
- dotenv
- @google/generative-ai (Gemini API)

---

## 📁 Project Structure

```
AI-CODE-REVIEWER/
├── BackEnd
│   ├── src
│   │   ├── controllers
│   │   ├── routes
│   │   ├── services
│   │   └── app.js
│   ├── server.js
│   └── package.json
└── Frontend
    ├── src
    │   ├── App.jsx
    │   ├── main.jsx
    │   ├── index.css
    │   └── assets
    ├── index.html
    └── package.json
```

---

## 🚀 Local Setup & Installation

### **1. Clone the Repository**
```sh
git clone https://github.com/<your-username>/ai-code-reviewer.git
```

### **2. Backend Setup**
```sh
cd BackEnd
npm install
```

Create a `.env` file:

```
GOOGLE_GEMINI_KEY=YOUR_API_KEY
```

Start backend:

```sh
node server.js
```

> Backend runs on: `http://localhost:3000`

---

### **3. Frontend Setup**
```sh
cd Frontend
npm install
npm run dev
```

> Frontend runs on: `http://localhost:5173`

---

## 🌐 API Endpoint

### **POST** `/ai/get-review`

#### **Request Body**
```json
{
  "code": "console.log('Hello');"
}
```

#### **Successful Response**
Returns formatted markdown containing:
- Issues
- Best practices
- Suggested fixes
- Refactored code (optional)

Example:
```text
❌ Issue: Missing error handling
✔ Suggested Fix: Wrap in try/catch
```

---

## 🔒 Environment Variables

| Variable | Description |
|---------|-------------|
| `GOOGLE_GEMINI_KEY` | API key for Gemini |

---

## 🎯 Use Cases

- Developer code review workflow
- Learning platform for best coding practices
- AI-assisted debugging and refactoring
- Code quality scoring tools
- Secure backend prompt engineering systems

---

## 📌 Notes for Deployment

- Frontend should point to production backend URL
- Backend must protect Gemini API keys using `.env`
- Add build steps in CI/CD if required

---

## 🧑‍💻 Developer Notes

- Backend acts as a secure middleware between UI and Gemini
- No client-side API keys are exposed
- Review logic is modular under `services/ai.service.js`

---

## 📝 License

This project is licensed under the MIT License.

---

## 🤝 Contributions

Pull requests and feature discussions are welcome.

