# Project 01 - Fully Local AI (OLLAMA + Open WebUI)
This project focuses on setting up a fully local AI environment using OLLAMA and Open WebUI, enabling secure and private AI interactions without relying on external servers. The setup is designed to harness the power of local GPUs, ensuring high performance and reduced latency for AI model inference.

  
  

## 1. Install WSL and Ubuntu (WSL for Windows)
```
wsl --install
```

## 2. Connect to a WSL Instance in a new window
```
wsl -d Ubuntu
```

## 3. Install Ollama
```
curl -fsSL https://ollama.com/install.sh | sh
```

https://ollama.com/download


## 4. Add a model to Ollama
```
ollama pull phi4
```

## 5. Run the Model
```
ollama run phi4
```

### 5.1. "Watch" GPU Performance in Linux Subsystem
```
nvidia-smi
```
```
watch -n 0.5 nvidia-smi
```

## 6. Download and Install Docker
### 6.1. Download Docker

```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

### 6.2. Install Docker
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## 7. Run Open WebUi Docker Container
```
sudo docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```
## 8. Check running Containers
```
sudo docker ps
```









