# 🛡️ Kali MCP Server Setup Guide

> **Architecture Overview**: This guide walks you through setting up a Kali Linux machine that communicates with Claude via MCP (Model Context Protocol) through a Windows host running VS Code.

---

## 📋 Requirements

- Windows machine with VS Code installed
- Hyper-V or standalone Linux machine capability
- Administrative privileges on both systems
- Basic familiarity with Linux command line

---

## 🐉 Part 1: Setting Up Kali Linux

### 1.1 Download and Install Kali

We'll be using a pre-built Kali VM for Hyper-V:

**Download:** [Kali Virtual Machines](https://www.kali.org/get-kali/#kali-virtual-machines)

1. Download the latest Kali Hyper-V image
2. Extract the archive
3. Import the VM into Hyper-V
4. Start the virtual machine

> 💡 **Default Credentials**: The Hyper-V image uses `kali` / `kali` - **Change this immediately after first login!**

### 1.2 Update the System

Keep your Kali installation current with the latest packages:

```bash
sudo apt update && sudo apt upgrade -y
```

### 1.3 Install MCP Kali Server

Install the MCP server package:

```bash
sudo apt install mcp-kali-server
```

📚 **Documentation**: [MCP Kali Server on Kali Tools](https://www.kali.org/tools/mcp-kali-server/#mcp-server)

### 1.4 Download the Server Script

Grab the Python server script from the GitHub repository:

```bash
cd ~/Desktop
wget https://raw.githubusercontent.com/Wh0am123/MCP-Kali-Server/main/kali_server.py
```

**Repository**: [MCP-Kali-Server on GitHub](https://github.com/Wh0am123/MCP-Kali-Server)

### 1.5 Launch the Server

Start the MCP server:

```bash
python3 kali_server.py
```

✅ **Success Indicator**: You should see output confirming the server is running and listening on port 5000.

![Server Running](https://github.com/user-attachments/assets/aef74cc4-6f80-434b-8037-0197d0abe178)

### 1.6 Note Your IP Address

Find and record your Kali machine's IP address:

```bash
ip addr show
```

> ⚠️ **Important**: Ensure this IP is reachable from your Windows host. Test with `ping <KALI_IP>` from Windows.

### 1.7 Optional: Enable SSH

For easier remote management, enable SSH:

```bash
sudo systemctl enable ssh
sudo systemctl start ssh
```

---

## 🪟 Part 2: Setting Up the Windows Machine

### 2.1 Install Python Dependencies

Open **PowerShell or Command Prompt as Administrator** and install the required packages:

```powershell
pip install mcp fastmcp
pip install --user fastmcp
```

### 2.2 Download the Client Script

Download the MCP client script to your Windows machine:

**Script**: [mcp_server.py](https://github.com/Wh0am123/MCP-Kali-Server/blob/main/mcp_server.py)

For this guide, we'll save it to `C:\logs\mcp_server.py`

---

## 🔧 Part 3: Configuring VS Code

### 3.1 Open the Command Palette

In VS Code, press `Ctrl+Shift+P` and type `>MCP`

![Command Palette](https://github.com/user-attachments/assets/c0b3bf38-2c75-4c2b-a7c4-bb675628b98c)

### 3.2 Add a New MCP Server

Select **"Add New Server"** from the options

![Add New Server](https://github.com/user-attachments/assets/9652f5f2-0a14-4de3-8bd3-0d65e623a3af)

### 3.3 Choose HTTP Protocol

Select **HTTP** as the protocol type

![Select HTTP](https://github.com/user-attachments/assets/51431efc-f484-4ac1-aba7-6d5083b7baff)

### 3.4 Configure the MCP Server

VS Code will generate a configuration file. Update it with the following JSON (replace `<KALI_IP>` with your actual Kali IP address):

```json
{
    "mcpServers": {
        "kali_mcp": {
            "command": "python3",
            "args": [
                "C:/logs/mcp_server.py",
                "--server",
                "http://<KALI_IP>:5000/"
            ]
        }
    }
}
```

> 📝 **Example**: If your Kali IP is `10.10.10.209`, use `http://10.10.10.209:5000/`

![Server Configuration](https://github.com/user-attachments/assets/b3a5fb69-aeb8-4bc7-9c50-4bf561cf0739)

### 3.5 Add Custom Instructions

Configure Claude to recognize and use your Kali tools by adding custom instructions:

![Add Instructions Step 1](https://github.com/user-attachments/assets/8343b6f4-dc94-4410-8d89-90e7e78300ac)

![Add Instructions Step 2](https://github.com/user-attachments/assets/ff4be574-b92d-4b1c-97d7-61e7b9f3e31e)

![Add Instructions Step 3](https://github.com/user-attachments/assets/3fc6d1d9-c476-4d01-89a0-b21fb8b222de)

![Add Instructions Step 4](https://github.com/user-attachments/assets/d3dc052a-7b30-42d2-819c-2b1c87ae7cbb)

**Custom Instructions Template:**

```yaml
---
applyTo: '**'
---
You have access to MCP tools called `kali_mcp` - these tools allow you to interact with a Kali Linux operating system and execute security testing tools and commands.

When you receive questions involving penetration testing, security assessments, ethical hacking, or any security-related topics, leverage these tools to search for answers and perform deep research within the Kali Linux environment.

Always ensure you have proper authorization before conducting any security testing activities.
```

---

## 🚀 Part 4: Starting Your Security Testing Session

### 4.1 Launch the MCP Connection

Restart or reload VS Code to initialize the MCP connection.

![Starting Server](https://github.com/user-attachments/assets/ba050c6f-b97e-43bf-8e08-0e2178c07fc1)

### 4.2 Verify the Connection

Check that the connection is established:

![Connection Status](https://github.com/user-attachments/assets/92d6ba35-06d9-439d-9fd5-178b6012addb)

### 4.3 Begin Your Assessment

Now you can interact with Claude and leverage your Kali tools. Try a prompt like:

```
Can you please start doing a pentest on the CTF machine at IP: 10.10.215.202
```

> ⚠️ **Authorization Notice**: You may see a security prompt asking you to confirm tool execution. This is normal - review and approve the action.

![Authorization Prompt](https://github.com/user-attachments/assets/dff90faf-70e4-47e8-88c9-0790e97af25e)

### 4.4 Monitor Execution

If everything is configured correctly, you'll see:
- Commands executing in your Kali terminal
- Real-time results appearing in VS Code
- Claude analyzing and interpreting the output

![Successful Execution](https://github.com/user-attachments/assets/7b52d098-7e27-418d-8e85-ed5a267186ef)

---

## 🎯 Troubleshooting Tips

| Issue | Solution |
|-------|----------|
| Can't ping Kali IP | Check Hyper-V network settings, ensure both machines are on the same network |
| Connection refused | Verify `kali_server.py` is running and firewall allows port 5000 |
| Permission errors | Run commands with `sudo` when necessary |
| MCP tools not appearing | Restart VS Code and verify configuration file syntax |

---

## 🔐 Security Reminders

- ⚠️ **Always obtain proper authorization** before conducting any security assessments
- 🔒 Change default Kali credentials immediately
- 🛡️ Use this setup only in controlled, authorized environments
- 📝 Document all testing activities and findings
- 🚫 Never test systems you don't have explicit permission to assess

---

## 📚 Additional Resources

- [Kali Linux Documentation](https://www.kali.org/docs/)
- [MCP Protocol Specification](https://modelcontextprotocol.io/)
- [Ethical Hacking Guidelines](https://www.eccouncil.org/code-of-ethics/)

---

**Happy (Authorized) Hacking! 🎩✨**
