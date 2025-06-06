# 🦙 LLaMA Interactive Web App with OpenWebUI

> 🚀 **Deploy your own AI-powered chat interface in minutes!** This project provides a complete Docker setup for running LLaMA models with OpenWebUI on DigitalOcean droplets.

## 🌟 Features

- 🤖 **LLaMA Models Integration** - Run powerful language models locally
- 🎨 **Beautiful Web Interface** - Clean and intuitive OpenWebUI design
- 🐳 **Docker Containerized** - Easy deployment and management
- ☁️ **Cloud Ready** - Optimized for DigitalOcean droplets
- 🔒 **Secure Configuration** - Environment-based secrets management
- ⚡ **Quick Setup** - Get running in under 5 minutes

## 📋 Prerequisites

Before you begin, ensure you have:

- 🖥️ A DigitalOcean droplet (minimum 4GB RAM recommended)
- 🐳 Docker and Docker Compose installed
- 🔑 Git installed on your system
- 🌐 Basic knowledge of terminal/command line

## 🚀 Quick Start Guide

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/Cristina-CI/gruppoc.git
cd gruppoc
```

### 2️⃣ Environment Configuration

Create your environment file for secure configuration:

```bash
cp .env.example .env
nano .env
```

Configure your `.env` file with the following variables:

```env
# OpenWebUI Configuration
WEBUI_SECRET_KEY=your-super-secret-key-here

# LLaMA Model Configuration
OLLAMA_BASE_URL=http://ollama:11434
DEFAULT_MODELS=llama2,codellama

# Security Settings
WEBUI_AUTH=true
ENABLE_SIGNUP=false

# Optional: Custom Settings
WEBUI_NAME="My AI Assistant"
DEFAULT_USER_ROLE=user
```

### 3️⃣ Launch the Application

Start all services with Docker Compose:

```bash
docker-compose up -d
```

Wait for the containers to initialize (this may take a few minutes on first run):

```bash
docker-compose logs -f
```

### 4️⃣ Access Your Web App

Once everything is running, access your application at:

```
https://gruppoc.cristina-capozziiorio.me/
```

## 🛠️ Advanced Configuration

### 📁 Project Structure

```
├── docker-compose.yml          # Main Docker configuration
├── .env.example               # Environment template
├── .env                       # Your environment variables (create this)
├── data/                      # Persistent data storage
│   ├── ollama/               # LLaMA models and data
│   └── open-webui/           # OpenWebUI data and configs
├── config/                    # Additional configurations
└── README.md                 # This file
```

### 🔧 Custom Model Installation

To add custom LLaMA models:

```bash
# Access the Ollama container
docker exec -it ollama-container ollama pull llama2:13b

# Or pull specific model variants
docker exec -it ollama-container ollama pull codellama:python
```

### 🔒 Security Best Practices

1. **Change default secrets** in your `.env` file
2. **Use strong passwords** for admin accounts
3. **Configure firewall** rules on your droplet
4. **Enable HTTPS** with reverse proxy (nginx/traefik)
5. **Regular backups** of your data directory

## 🐛 Troubleshooting

### Common Issues

**🚨 Port already in use**
```bash
# Check what's using the port
sudo lsof -i :3000
# Stop conflicting services
sudo systemctl stop apache2  # or nginx
```

**🚨 Container fails to start**
```bash
# Check container logs
docker-compose logs ollama
docker-compose logs open-webui
```

**🚨 Out of memory errors**
```bash
# Check system resources
free -h
df -h
# Consider upgrading your droplet size
```

### 📊 Monitoring

Monitor your application health:

```bash
# Check container status
docker-compose ps

# View resource usage
docker stats

# Check logs
docker-compose logs --tail=50
```

## 🔄 Updates and Maintenance

### Updating the Application

```bash
# Pull latest changes
git pull origin main

# Rebuild containers
docker-compose down
docker-compose up -d --build

# Clean up old images
docker system prune -f
```

## 📈 Performance Optimization

- 🚀 Use SSD storage for better I/O performance
- 💾 Allocate sufficient RAM (8GB+ recommended for larger models)
- 🌐 Use CDN for static assets in production
- ⚡ Enable GPU acceleration if available

## 🤝 Contributing

We welcome contributions! Here's how you can help:

1. 🍴 Fork the repository
2. 🌿 Create a feature branch (`git checkout -b feature/amazing-feature`)
3. 💾 Commit your changes (`git commit -m 'Add some amazing feature'`)
4. 📤 Push to the branch (`git push origin feature/amazing-feature`)
5. 🔄 Open a Pull Request

## 👥 Contributors


- 👨‍💻 **Cristina-CI**
- 👩‍💻 **Skitarrata**
- 👨‍💻 **gianmarcogg03**
- 👨‍💻 **RaffDeco**
- 👨‍💻 **SimoApo**



## 🎉 Acknowledgments

- 🦙 [Ollama](https://ollama.ai/) for the amazing LLaMA integration
- 🎨 [OpenWebUI](https://openwebui.com/) for the beautiful interface
- 🐳 [Docker](https://docker.com/) for containerization
- ☁️ [DigitalOcean](https://digitalocean.com/) for reliable hosting

---

<div align="center">

**⭐ If this project helped you, please give it a star! ⭐**

Made with ❤️ and lots of ☕

</div>
