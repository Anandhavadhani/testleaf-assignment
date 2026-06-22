# QA Bot - Quick Start Guide

## ✅ Current Status
The QA Bot backend server is **RUNNING** on http://localhost:3000

---

## 🚀 To Start Using the Application

### Step 1: Configure API Key
Edit `backend/.env` and add your actual OpenAI API key:

```env
MODEL_PROVIDER=openai
OPENAI_API_KEY=sk-your-real-key-here
OPENAI_MODEL=gpt-4
TEMPERATURE=0.1
PORT=3000
```

Get your API key from: https://platform.openai.com/api-keys

### Step 2: Access the Frontend
1. Open your browser
2. Go to: **http://localhost:3000**
3. You should see the QA Bot UI

### Step 3: Upload & Query
1. **Upload Documents** (PDF, DOCX, CSV, or TXT)
2. **Enter Your Question**
3. **Select Answer Style** (default, detailed, concise, technical)
4. **Click Submit** and wait for the AI response

---

## 📝 API Examples

### Example 1: Query with Text
```bash
curl -X POST http://localhost:3000/api/search/document \
  -H "Content-Type: application/json" \
  -d '{
    "question": "What is the main topic?",
    "documentText": "This document discusses artificial intelligence and its applications in healthcare.",
    "promptType": "concise"
  }'
```

### Example 2: Health Check
```bash
curl http://localhost:3000/health
```

### Example 3: Upload File and Query
```bash
curl -X POST http://localhost:3000/api/search/upload \
  -F "files=@document.pdf" \
  -F "question=Summarize this document" \
  -F "promptType=detailed"
```

---

## 🔧 Available Prompt Types

| Type | Purpose | Best For |
|------|---------|----------|
| `default` | Structured answer with citations | General queries |
| `detailed` | Comprehensive analysis | Complex topics |
| `concise` | Brief 1-3 sentence answer | Quick lookups |
| `technical` | Precise technical answer | Technical docs |

---

## 📊 Server Information

**URL**: http://localhost:3000  
**Status**: ✅ Running  
**Terminal ID**: 2  
**Mode**: Development (auto-reload enabled)  

### Available Endpoints
- `GET /` - Frontend UI
- `GET /health` - Health check & model info
Note: Both `/api/search/*` and legacy `/search/*` endpoints are accepted by the server for compatibility. Use `/api/search/*` for new clients.

---

## ⚙️ Switching LLM Providers

### Use Anthropic (Claude)
```env
MODEL_PROVIDER=anthropic
ANTHROPIC_API_KEY=sk-ant-...
ANTHROPIC_MODEL=claude-3-5-sonnet-20241022
```

### Use Groq (Mixtral)
```env
MODEL_PROVIDER=groq
GROQ_API_KEY=gsk_...
GROQ_MODEL=mixtral-8x7b
```

Then restart the server for changes to take effect.

---

## 📁 Supported File Types

- **PDF** - `.pdf` - Up to 10MB
- **Word** - `.docx` - Up to 10MB
- **Spreadsheet** - `.csv` - Up to 10MB
- **Text** - `.txt` - Up to 10MB

---

## 🛑 Stopping the Server

In the terminal where the server is running, press `Ctrl+C` to stop.

To restart:
```bash
npm run dev
```

---

## 📚 Project Structure

```
qa-bot/
├── backend/               # Node.js + Express server
│   ├── src/              # TypeScript source code
│   ├── dist/             # Compiled JavaScript
│   └── .env              # Configuration file
│
├── frontend/             # HTML5 + Vanilla JS UI
│   └── public/
│       └── index.html    # Main interface
│
└── docs/                 # Documentation
    ├── ARCHITECTURE.md
    ├── API.md
    └── modules/          # Module documentation
```

---

## 🧪 Testing

### Verify Server is Running
```bash
node backend/tests/test-server.mjs
```

Should show: **✅ ALL INTEGRATION TESTS PASSED!**

### Test Specific Endpoint
```bash
curl http://localhost:3000/health
```

Response:
```json
{
  "status": "healthy",
  "timestamp": "2026-06-03T...",
  "model": {
    "provider": "openai",
    "model": "gpt-4",
    "temperature": 0.1
  }
}
```

---

## 💡 Tips

1. **Better Answers**: Provide clear, detailed questions
2. **Faster Processing**: Use "concise" for simple queries
3. **Complex Analysis**: Use "detailed" for nuanced topics
4. **API Testing**: Use "default" to start
5. **Multiple Files**: Upload multiple files at once; they'll be combined

---

## 🐛 Troubleshooting

### "API key not found"
- Edit `backend/.env`
- Add your real OpenAI API key
- Make sure no spaces around the key

### "File exceeds 10MB"
- The file is too large
- Try splitting into smaller files

### "Unsupported file type"
- Only PDF, DOCX, CSV, and TXT supported
- Convert your file to one of these formats

### Server won't start
- Check if port 3000 is already in use
- Change `PORT` in `.env` to another number (e.g., 3001)
- Restart the server

---

## 📞 Next Steps

1. ✅ **Server Running** - Currently active on port 3000
2. 📝 **Add API Key** - Configure `backend/.env`
3. 🌐 **Open Browser** - Visit http://localhost:3000
4. 📤 **Upload Document** - Test with a sample file
5. 💬 **Ask Question** - Get AI-powered answer

---

## 🎯 Summary

**QA Bot is ready to use!**

- Backend: ✅ Running
- Frontend: ✅ Ready
- All Endpoints: ✅ Functional
- Tests: ✅ Passing

Just add your API key and start querying!

---

**For full documentation**, see:
- `docs/ARCHITECTURE.md` - System design
- `docs/API.md` - Endpoint reference
- `SERVER_STATUS.md` - Current status
