```markdown
# sudo for Termux

A powerful bash script that provides `sudo` functionality for Termux environment on Android devices.

> **Note**: This is an enhanced version with improved security, better error handling, and additional features.

## 📱 About Termux

Termux is an Android terminal emulator and Linux environment application that works directly with no rooting or setup required. However, to use `sudo`, you need root access.

## ⚠️ Important Note

This project is based on the original `termux-sudo` with significant improvements and enhancements for better reliability and security.

## 🛠 Requirements

- **Rooted Android device** with `su` binary installed
- **Termux** app installed from [F-Droid](https://f-droid.org/) or [Google Play](https://play.google.com/)
- **SU binary** (Magisk SU, SuperSU, or other root solution)

> 🔴 **SUDO WILL NOT WORK WITHOUT ROOT ACCESS AND SU BINARY**

## 📥 Installation

### Method 1: Direct Download & Install

1. **Download the script:**
   ```bash
   curl -L -o sudo https://raw.githubusercontent.com/Endjustice/deep-eating/main/sudo
```

1. Make it executable and install:
   ```bash
   chmod +x sudo
   cp sudo $PREFIX/bin/sudo
   ```

Method 2: Clone Repository

```bash
git clone https://github.com/Endjustice/deep-eating.git
cd deep-eating
cp sudo $PREFIX/bin/sudo
chmod 700 $PREFIX/bin/sudo
```

Install Dependencies

```bash
pkg update && pkg install ncurses-utils
```

✨ Enhanced Features

🎯 Core Functionality

· Automatic environment setup on first run
· Root home directory creation (~/.suroot) with proper permissions
· Custom .bashrc for root shell with correct environment variables
· Preserved command history for root sessions

🚀 New Improvements

· Advanced error handling with colored messages
· Comprehensive logging system for debugging
· Security enhancements with argument validation
· Timeout protection for long-running commands
· Better compatibility with various root methods (Magisk, SuperSU, etc.)

🎨 User Experience

· Enhanced colored output (configurable)
· Informative status messages
· Better command feedback
· Improved help system

🛠 Usage

Basic Commands

```bash
# Drop to root shell
sudo su

# Drop to login root shell (loads profile)
sudo su -

# Run single command as root
sudo apt update
sudo whoami

# Run complex commands
sudo bash -c 'echo "Running as root" && id'
```

Advanced Usage

```bash
# Validate root access
sudo -v

# Show configuration
sudo -l

# Show version information
sudo --version

# Show help
sudo --help
```

⚙️ Configuration

Toggle Colored Output

Edit the colored variable in the script:

```bash
colored=true  # Change to 'false' to disable colors
```

Logging

Logs are stored in:

```
/data/data/com.termux/files/usr/var/log/sudo.log
```

🔧 Technical Details

Environment Setup

The script automatically:

· Creates ~/.suroot directory for root home
· Sets up proper PATH and LD_LIBRARY_PATH
· Configures bash prompt and aliases
· Maintains separate command history

Supported SU Binaries

· Magisk SU (/magisk/.core/bin/su)
· System SU (/system/xbin/su)
· SuperSU (/su/bin/su)
· And other common locations

🐛 Troubleshooting

Common Issues

1. "su executable not found"
   · Ensure your device is properly rooted
   · Verify SU binary exists and is executable
2. "Permission denied"
   · Check if Termux has root access
   · Try su command manually first
3. "Command not found"
   · Verify the command exists in Termux environment
   · Check your PATH configuration

Debug Mode

Enable logging by setting LOG_ENABLED=true in the script for detailed debugging information.

📝 Examples in Scripts

```bash
#!/bin/bash
# Use sudo in shell scripts

if sudo -v; then
    sudo apt update
    sudo apt upgrade -y
else
    echo "Root access required!"
    exit 1
fi
```

🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

📄 License

This project is open source. Feel free to use and modify as needed.

⚠️ Disclaimer

Use this software at your own risk. The authors are not responsible for any damage caused to your device.

---

Enjoy the power of sudo on your Android device! 🎉
