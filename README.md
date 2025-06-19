# 🛡️ Spam Fighter (LumaOne)

**AI-Powered Multi-Tenant Email Security and Intelligence Platform**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Node.js](https://img.shields.io/badge/Node.js-18+-green.svg)](https://nodejs.org/)

> **LumaOne** is a comprehensive email intelligence platform that helps users manage email overload, detect threats, and automate email management tasks using advanced AI classification and tenant-configurable LLM providers.

---

## 🎯 **Overview**

Spam Fighter provides intelligent email analysis for enterprise and individual users through:

- **🤖 Multi-LLM Support**: OpenAI, Azure OpenAI, Ollama, and custom endpoints
- **📧 Smart Classification**: Spam detection, category classification, phishing detection  
- **💬 AI Replies**: Generated response suggestions and auto-unsubscribe
- **🔄 Learning Loop**: Continuous improvement from user feedback
- **🏢 Multi-Tenant**: Isolated tenant data with custom LLM configurations
- **📊 Analytics**: Email trends, sender analysis, and digest generation
- **⚙️ Automation**: Custom rules and bulk actions

---

## 🏗️ **Architecture**

**Dual-API Design** for optimal separation of concerns:

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │    App API      │    │    AI API       │
│   (Next.js)     │◄──►│   (Fastify)     │◄──►│   (FastAPI)     │
│   Port: 3000    │    │   Port: 3001    │    │   Port: 8001    │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                               │
                       ┌───────▼────────┐
                       │   Supabase     │
                       │  (PostgreSQL)  │
                       └────────────────┘
```

### **Components**

| Component | Technology | Purpose |
|-----------|------------|---------|
| **Frontend** | Next.js + Mantine | User interface and dashboard |
| **App API** | Fastify + Supabase | Authentication, database, core logic |
| **AI API** | FastAPI + LLM Router | Email classification, smart replies |
| **Database** | Supabase (PostgreSQL) | Multi-tenant data with RLS |

---

## 🚀 **Quick Start**

### **Prerequisites**

- **Python 3.8+** with `uv` package manager
- **Node.js 18+** with `bun` package manager (preferred)
- **Supabase** project setup

### **1. Clone & Setup**

```bash
git clone <repository-url>
cd spam_fighter
```

### **2. Configure Environment**

```bash
# Copy environment templates
cp ai_api/.env.example ai_api/.env
cp app_api/.env.example app_api/.env
cp frontend/.env.example frontend/.env

# Edit each .env file with your configurations
```

### **3. Start Services**

**Terminal 1 - AI API:**
```bash
cd ai_api
uv venv && source .venv/bin/activate
uv pip install -r requirements.txt
python main.py
# ➜ http://localhost:8001
```

**Terminal 2 - App API:**
```bash
cd app_api
bun install  # or npm install
bun dev      # or npm run dev
# ➜ http://localhost:3001
```

**Terminal 3 - Frontend:**
```bash
cd frontend
bun install  # or npm install
bun dev      # or npm run dev
# ➜ http://localhost:3000
```

---

## 📁 **Project Structure**

```
spam_fighter/
├── 🤖 ai_api/              # FastAPI - AI/ML Processing
│   ├── main.py             # FastAPI application
│   ├── models.py           # Pydantic models
│   ├── config.py           # Configuration management
│   ├── services/           # LLM routing & services
│   └── README.md           # AI API documentation
├── ⚡ app_api/             # Fastify - Core Application  
│   ├── index.js            # Fastify application
│   ├── middleware/         # Authentication & middleware
│   └── README.md           # App API documentation
├── 🎨 frontend/            # Next.js - User Interface
│   ├── app/                # Next.js App Router
│   ├── components/         # React components
│   └── README.md           # Frontend documentation
├── 📚 docs/                # Comprehensive Documentation
│   ├── architecture.md     # System architecture
│   ├── phase_outline.md    # Development timeline
│   └── *.md                # Additional documentation
└── README.md               # This file
```

---

## 🛠️ **Development Phases**

### **Phase 1: Core Intelligence & Control** *(Weeks 1-4)*
- ✅ Auto-categorization (Marketing, Transactional, etc.)
- ✅ AI-generated smart replies  
- ✅ Phishing & malware detection

### **Phase 2: Behavior Insights & Digest** *(Weeks 5-8)*
- 📧 Email engagement history
- 📊 Bulk actions and digest generation
- 🚫 Smart block/allow lists

### **Phase 3: Long-Term Insights & Automation** *(Weeks 9-12)*
- 📈 Email overload dashboard
- 📋 Unsubscribe tracking
- ⚙️ Custom automation rules

**Total Timeline: 12-14 Weeks**

---

## 🔧 **Key Features**

### **🤖 LumaOne Core**
- Email ingestion + LLM classification engine
- Spam, malicious, unsubscribe intent detection

### **🧠 LumaOne Nexus** 
- AI coordination + routing logic
- Multi-agent inference, LLM selection per tenant

### **🛡️ LumaOne Shield**
- Threat detection: phishing, malware, spoofing
- Suspicious URL analysis

### **🔄 LumaOne Synapse**
- Feedback loop for learning from user input
- Model improvement from spam vs. unwanted classifications

### **🎯 LumaOne Triage**
- Intelligent categorization
- Bulk actions (archive, mark safe/spam, unsubscribe)

---

## 📖 **Documentation**

| Document | Description |
|----------|-------------|
| [`docs/architecture.md`](docs/architecture.md) | System architecture overview |
| [`docs/dual_api.md`](docs/dual_api.md) | Dual-API design details |
| [`docs/ai_flexability.md`](docs/ai_flexability.md) | Multi-LLM provider support |
| [`docs/phase_outline.md`](docs/phase_outline.md) | Development timeline |
| [`docs/stack.md`](docs/stack.md) | Technology stack details |
| [`ai_api/README.md`](ai_api/README.md) | AI API documentation |
| [`app_api/README.md`](app_api/README.md) | App API documentation |
| [`frontend/README.md`](frontend/README.md) | Frontend documentation |

---

## 🔐 **Environment Configuration**

### **Required Variables**

**AI API:**
```env
SUPABASE_URL=your_supabase_url
APP_API_SECRET=shared_secret
OPENAI_API_KEY=your_openai_key  # or other LLM provider
```

**App API:**
```env
SUPABASE_URL=your_supabase_url
SUPABASE_ANON_KEY=your_supabase_anon_key
MS_CLIENT_ID=your_microsoft_client_id
AI_API_URL=http://localhost:8001
```

**Frontend:**
```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
```

---

## 🧪 **Testing**

```bash
# AI API tests
cd ai_api && python -m pytest

# App API tests  
cd app_api && bun test

# Frontend tests
cd frontend && bun test
```

---

## 🚢 **Deployment**

### **Docker Compose** *(Recommended)*

```bash
docker-compose up -d
```

### **Individual Services**

- **AI API**: Deploy to any Python hosting (Railway, Fly.io, etc.)
- **App API**: Deploy to Node.js hosting (Vercel, Railway, etc.)  
- **Frontend**: Deploy to Vercel, Netlify, or static hosting
- **Database**: Use Supabase cloud or self-hosted PostgreSQL

---

## 🤝 **Contributing**

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📋 **Project Status**

- ✅ **Architecture Designed**: Complete technical specifications
- ✅ **APIs Scaffolded**: FastAPI (AI) + Fastify (App) with full structure
- ✅ **Database Schema**: Multi-tenant PostgreSQL design
- ✅ **Frontend Initialized**: Next.js + Mantine setup
- 🚧 **Phase 1 Development**: In Progress

---

## 📄 **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 📞 **Support**

For questions, issues, or contributions:

- 📧 **Issues**: GitHub Issues
- 📚 **Documentation**: [`/docs`](docs/) folder
- 💬 **Discussions**: GitHub Discussions

---

**Built with ❤️ for better email management** 