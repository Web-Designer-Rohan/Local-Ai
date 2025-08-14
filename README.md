# 🚀 Ollama LLM + WebUI Setup Guide (Windows & Linux)

This guide will help you install and run **Ollama LLM** with a **WebUI** on both **Windows** (via WSL) and **Linux**.  

---

## 🖥️ 1. Install WSL (Windows Only)

```bash
wsl --install

Install Ubuntu 22.04 LTS specifically:

wsl --install -d Ubuntu-22.04


---

🐧 2. Install Ollama (Linux)

curl -fsSL https://ollama.com/install.sh | sh

Pull your desired Ollama model (replace <model-name>):

ollama pull <model-name>


---

🐋 3. Install Docker (Linux)

Add Docker’s official GPG key:

sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

Add Docker repository:

echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" \
| sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update

Install Docker:

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin


---

🌐 4. Run Open-WebUI with Docker

docker run -d --network host \
  -v open-webui:/app/backend/data \
  -e OLLAMA_BASE_URL=http://127.0.0.1:11434 \
  --name open-webui \
  --restart always \
  ghcr.io/open-webui/open-webui:main


---

🐍 5. Install Python & Dependencies

Install Python build tools:

sudo apt install -y make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev \
liblzma-dev python3-openssl git

Install Pyenv:

curl https://pyenv.run | bash

Set up environment variables:

export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

Reload shell:

source ~/.bashrc

Verify Pyenv installation:

pyenv -h

Install Python 3.10:

pyenv install 3.10
pyenv global 3.10


---

🎨 6. Install Stable Diffusion WebUI

Create project folder:

mkdir image && cd image

Download WebUI script:

wget -q https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh

Make script executable:

chmod +x webui.sh

Run WebUI:

./webui.sh

Run WebUI with API & listening enabled:

./webui.sh --listen --api


---

✅ You’re all set!
Now you can run Ollama LLM locally with a sleek WebUI and even integrate Stable Diffusion for AI image generation.

---

If you want, I can also make this **GitHub-ready with badges, collapsible sections, and a table of contents** so it looks *pro-level*. That would make your repo pop and look official.  

Do you want me to make that next?

