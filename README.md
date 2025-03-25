#  System Insights Toolkit

## 🌟 Features
- **Neofetch**: Artistic, Colorful System Information
- **Htop**: High-Tech, Graph-Intensive Process Monitoring

## 🚀 Installation

### Prerequisites
- Linux (Ubuntu, Mint, Fedora, Arch)
- Bash
- Git

### Quick Setup
```bash
# Clone Repository
git clone https://github.com/aditya19200/system-insights-toolkit.git

# Navigate to Directory
cd system-insights-toolkit

# Install Dependencies
sudo ./install.sh
```

## 🎨 Neofetch Highlights
- Emoji-enhanced system information
- Vibrant color palette
- Artistic ASCII art
- Detailed hardware insights

### Sample Output
```
╭─────────────────────────────────────────╮
❖ System Insights ❖
🖥️  OS: Ubuntu 22.04 LTS
🧊 Kernel: 5.15.0-75-generic
⏰ Uptime: 3 days, 4 hours
...
╰─────────────────────────────────────────╯
```

## 💻 Htop Features
- High-contrast technical design
- Intensive process graphs
- Performance tracking
- Detailed system resource visualization

## 📊 Customization
- Modify `neofetch/config.conf` for display preferences
- Edit `htop/htoprc` for process view settings

## 🖼️ Screenshots
[Add screenshots demonstrating Neofetch and Htop outputs]

## 🤝 Contributing
Contributions are welcome! 
- Open issues for suggestions
- Submit pull requests for improvements



I'll also include an installation script:

<antArtifact identifier="install-script" type="application/vnd.ant.code" language="bash" title="System Insights Installation Script">
#!/bin/bash

# System Insights Toolkit Installer

# ANSI Color Codes
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
NC='\033[0m' # No Color

# Welcome Message
echo -e "${BLUE}🚀 System Insights Toolkit Installer ${NC}"
echo -e "${YELLOW}Preparing to set up advanced system monitoring...${NC}"

# Detect Linux Distribution
detect_distro() {
    if [ -f /etc/os-release ]; then
        . /etc/os-release
        DISTRO=$ID
    else
        echo -e "${RED}Unsupported distribution${NC}"
        exit 1
    fi
}

# Install Dependencies
install_deps() {
    echo -e "${YELLOW}Installing system dependencies...${NC}"
    
    case $DISTRO in
        ubuntu|debian|linuxmint)
            sudo apt-get update
            sudo apt-get install -y neofetch htop lm-sensors
            ;;
        fedora)
            sudo dnf install -y neofetch htop lm_sensors
            ;;
        arch)
            sudo pacman -S --noconfirm neofetch htop lm-sensors
            ;;
        *)
            echo -e "${RED}Unsupported distribution. Please install manually.${NC}"
            exit 1
            ;;
    esac
}

# Configure Neofetch
configure_neofetch() {
    echo -e "${YELLOW}Configuring Neofetch...${NC}"
    mkdir -p ~/.config/neofetch
    cp neofetch/config.conf ~/.config/neofetch/config.conf
}

# Configure Htop
configure_htop() {
    echo -e "${YELLOW}Configuring Htop...${NC}"
    mkdir -p ~/.config/htop
    cp htop/htoprc ~/.config/htop/htoprc
}

# Main Installation Process
main() {
    detect_distro
    install_deps
    configure_neofetch
    configure_htop
    
    echo -e "${GREEN}✨ Installation Complete! 🎉${NC}"
    echo -e "${BLUE}Run 'neofetch' or 'htop' to see your new configurations.${NC}"
}

# Execute Main Function
main
