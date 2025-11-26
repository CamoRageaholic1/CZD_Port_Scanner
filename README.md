# CZD Port Scanner

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Security](https://img.shields.io/badge/Security-Network%20Tools-red?style=for-the-badge)
![Maintained](https://img.shields.io/badge/Maintained-Yes-brightgreen?style=for-the-badge)

A modular, multithreaded Python port scanner supporting multiple scan types. Built for internal reconnaissance, firewall validation, and security audits.

## 🎯 Features

- ✅ **TCP Connect Scan** - Standard three-way handshake
- ✅ **TCP SYN Stealth Scan** - Half-open scanning using raw sockets
- ✅ **UDP Scan** - UDP port enumeration
- ✅ **Custom Port Ranges** - Flexible port specification (e.g., 22,80,443,8000-8010)
- ✅ **Multithreaded** - Fast parallel scanning
- ✅ **Automatic Logging** - Results saved to port_scanner.log
- ✅ **Modular Design** - Easy to extend and customize

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- Root/Administrator privileges (for SYN and UDP scans)
- Scapy library for raw packet manipulation

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/CamoRageaholic1/CZD_Port_Scanner.git
   cd CZD_Port_Scanner
   ```

2. **Install dependencies**
   ```bash
   pip3 install -r requirements.txt
   ```

### Basic Usage

```bash
# TCP Connect Scan
sudo python3 CZD_Port_Scanner.py --target 192.168.1.1 --ports 22,80,443 --scan tcp

# SYN Stealth Scan (requires root)
sudo python3 CZD_Port_Scanner.py --target 192.168.1.1 --ports 1-1024 --scan syn

# UDP Scan (requires root)
sudo python3 CZD_Port_Scanner.py --target 192.168.1.1 --ports 53,123,161,500 --scan udp
```

## 📖 Usage Guide

### Command-Line Options

```bash
sudo python3 CZD_Port_Scanner.py --target <ip_or_hostname> --ports <port_list> --scan <tcp|syn|udp>
```

**Parameters:**
- `--target` - Target IP address or hostname
- `--ports` - Ports to scan (comma-separated or ranges)
  - Examples: `22,80,443` or `1-1024` or `22,80,8000-8010`
- `--scan` - Scan type: `tcp`, `syn`, or `udp`

### Scan Types

#### TCP Connect Scan
Standard TCP connection - completes three-way handshake
- **Pros:** No special privileges required, most reliable
- **Cons:** Easily detected, logged by target systems

```bash
python3 CZD_Port_Scanner.py --target example.com --ports 80,443 --scan tcp
```

#### SYN Stealth Scan
Half-open scan - sends SYN packet without completing handshake
- **Pros:** Stealthier, less likely to be logged
- **Cons:** Requires root privileges, uses raw sockets

```bash
sudo python3 CZD_Port_Scanner.py --target 192.168.1.1 --ports 1-1000 --scan syn
```

#### UDP Scan
Scans UDP ports for services
- **Pros:** Finds UDP-only services (DNS, SNMP, etc.)
- **Cons:** Slower, less reliable, requires root privileges

```bash
sudo python3 CZD_Port_Scanner.py --target 192.168.1.1 --ports 53,161,500 --scan udp
```

## 📊 Output

All scan results are automatically logged to `port_scanner.log` with timestamps:

```
[2025-11-26 10:30:45] Target: 192.168.1.1
[2025-11-26 10:30:45] Port 22/tcp - OPEN
[2025-11-26 10:30:45] Port 80/tcp - OPEN
[2025-11-26 10:30:45] Port 443/tcp - OPEN
```

## ⚠️ Permissions & Requirements

### Root Access Required For:
- **SYN scans** - Raw socket creation
- **UDP scans** - Raw socket creation

### Running with Sudo

```bash
# Always use sudo for SYN and UDP scans
sudo python3 CZD_Port_Scanner.py --target 192.168.1.1 --ports 1-1024 --scan syn
```

## 🔒 Legal & Ethical Use

**⚠️ IMPORTANT DISCLAIMER:**

This tool is intended for:
- ✅ Authorized security testing
- ✅ Internal network audits
- ✅ Educational purposes
- ✅ Personal lab environments

**Unauthorized port scanning may violate:**
- Local, state, or federal laws
- Organizational security policies
- Terms of service agreements
- Computer fraud and abuse laws

**Always obtain explicit written permission before scanning systems you do not own.**

## 📁 Project Structure

```
CZD_Port_Scanner/
├── CZD_Port_Scanner.py     # Main scanner script
├── README.md               # This file
├── LICENSE                 # MIT License
├── requirements.txt        # Python dependencies
├── .gitignore             # Git ignore rules
└── port_scanner.log       # Auto-generated scan results
```

## 🛣️ Roadmap

Future enhancements planned:

- [ ] Export results to JSON/CSV formats
- [ ] Service banner grabbing
- [ ] CIDR/subnet scanning support
- [ ] Nmap XML output compatibility
- [ ] OSINT integration
- [ ] Web-based dashboard
- [ ] Scan scheduling and automation

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/enhancement`)
3. Commit changes (`git commit -m 'Add new feature'`)
4. Push to branch (`git push origin feature/enhancement`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📫 Support

- 🐛 **Bug Reports:** Open an issue on GitHub
- 💡 **Feature Requests:** Open an issue with the "enhancement" label
- 📧 **Contact:** For other inquiries, reach out via GitHub

## 🙏 Acknowledgments

Built as part of a cybersecurity utility suite showcasing hands-on Python and network enumeration expertise.

---

**Author:** David Osisek (CamoZeroDay)  
**Education:** MIT in IT Security, BS Software Development and Analysis

**Made with ❤️ for the cybersecurity community**
