🧠 Ollama + Open WebUI Setup Guide (Linux / Windows / macOS)

A complete guide to run a local ChatGPT-like AI system using:

🧠 Ollama (local LLM runtime)
🌐 Open WebUI (ChatGPT-style interface)
🐳 Docker (for WebUI)
🌍 What you get

After setup you can:

Chat with AI locally in your browser
Run models like qwen2.5, llama3, mistral
Work offline after downloading models
Use a ChatGPT-like interface
🧰 Requirements (All systems)
Internet connection (first install only)
At least 6 GB RAM (recommended 8+ GB)
Docker (for WebUI)
Ollama (for AI models)
🐧 Linux (Ubuntu / Kali / Debian)
1. Install Ollama
curl -fsSL https://ollama.com/install.sh | sh

Enable service:

sudo systemctl enable ollama
sudo systemctl start ollama

Test:

curl http://127.0.0.1:11434/api/tags
2. Install AI models
ollama pull qwen2.5:3b-instruct
ollama pull llama3

Test:

ollama run qwen2.5:3b-instruct
3. Install Docker
curl -fsSL https://get.docker.com | sh
sudo systemctl enable docker
sudo systemctl start docker
4. Run Open WebUI
sudo docker run -d \
  --name open-webui \
  --restart unless-stopped \
  --network=host \
  -e WEBUI_AUTH=False \
  -e OLLAMA_BASE_URL=http://127.0.0.1:11434 \
  -v open-webui:/app/backend/data \
  ghcr.io/open-webui/open-webui:main
5. Open in browser
http://localhost:3000
🪟 Windows (Easy method)
1. Install Ollama

Download:

👉 https://ollama.com/download

Install normally.

2. Install models (PowerShell)
ollama pull qwen2.5:3b-instruct
ollama pull llama3

Test:

ollama run qwen2.5:3b-instruct
3. Install Docker Desktop

Download:

👉 https://www.docker.com/products/docker-desktop/

Enable WSL2 if asked.

4. Run Open WebUI (PowerShell)
docker run -d `
  --name open-webui `
  -p 3000:8080 `
  -e WEBUI_AUTH=False `
  -e OLLAMA_BASE_URL=http://host.docker.internal:11434 `
  -v open-webui:/app/backend/data `
  ghcr.io/open-webui/open-webui:main
5. Open browser
http://localhost:3000
🍎 macOS
1. Install Ollama

Download:

👉 https://ollama.com/download

Or via terminal:

curl -fsSL https://ollama.com/install.sh | sh
2. Install models
ollama pull qwen2.5:3b-instruct
ollama pull llama3
3. Install Docker Desktop

👉 https://www.docker.com/products/docker-desktop/

4. Run Open WebUI
docker run -d \
  --name open-webui \
  -p 3000:8080 \
  -e WEBUI_AUTH=False \
  -e OLLAMA_BASE_URL=http://host.docker.internal:11434 \
  -v open-webui:/app/backend/data \
  ghcr.io/open-webui/open-webui:main
5. Open browser
http://localhost:3000
🧠 How it works
Browser (WebUI)
   ↓
Open WebUI (Docker)
   ↓
Ollama API (11434)
   ↓
AI Models (qwen2.5 / llama3 / mistral)
⚙️ Troubleshooting
❌ No models shown

✔ Fix:

OLLAMA_BASE_URL=http://127.0.0.1:11434
❌ WebUI not opening

Try:

http://127.0.0.1:3000
❌ Docker issues (Linux)

Reset:

sudo docker rm -f open-webui
🚀 Optional models
ollama pull mistral
ollama pull gemma
ollama pull codellama
👤 Author

Made by Yahya 😎
