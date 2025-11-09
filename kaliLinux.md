**Workflow: Running Linux on an independent machine. I have a Windows Host that will do the talking to that machine via VSC**


**Requirements**:
# Setting up Kali
  
I'll use a VM on hyperV for kali: Download the latest version here: https://www.kali.org/get-kali/#kali-virtual-machines
* * Uncompress it, and open it with HypverV (_you should already know how to set up a HyperV Host otherwise ,use a full machine_)
    
Note: if the Kali hyper image is used, the creds are `kali/kali`. Change this afterwards

Update the machine:
```
sudo apt update and sudo apt upgrade -y
```

Installing the server: https://www.kali.org/tools/mcp-kali-server/#mcp-server
```
sudo apt install mcp-kali-server
```

Download the MCP server file on the machine: https://github.com/Wh0am123/MCP-Kali-Server/blob/main/kali_server.py
```
https://github.com/Wh0am123/MCP-Kali-Server/blob/main/kali_server.py
```
you can now open the terminal and run it by using
```
python3 kali_server.py
```
<img width="698" height="203" alt="image" src="https://github.com/user-attachments/assets/aef74cc4-6f80-434b-8037-0197d0abe178" />

Once you get this, you are good here just keep track on the internal IP, make sure this is pingable.
I'd suggest also installing and enabling the `SSH` server,

# Setting up the Windows Machine:
- Make sure Python and pip are installed, cause we need to install these under Admin:
```
pip install mcp, FastMCP 
pip install --user fastmcp
```
- Download this file https://github.com/Wh0am123/MCP-Kali-Server/blob/main/mcp_server.py https://github.com/Wh0am123/MCP-Kali-Server/tree/main
For testing purposes, I downloaded in the `C:\logs`


# Configuring VSC:
## ️ Adding the MCP Server in VS Code

### Step 1: Open Command Palette
Type `>MCP` in the command palette (search for `VSC` at the top)

![Command Palette](https://github.com/user-attachments/assets/c0b3bf38-2c75-4c2b-a7c4-bb675628b98c)

### Step 2: Add New Server
Click "Add New Server"

![Add New Server](https://github.com/user-attachments/assets/9652f5f2-0a14-4de3-8bd3-0d65e623a3af)

### Step 3: Select HTTP Protocol
Choose `HTTP` protocol

![Select HTTP](https://github.com/user-attachments/assets/51431efc-f484-4ac1-aba7-6d5083b7baff)

### Step 4: Add MCP URL
Add the official MCP URL: _change this accordingly_
```
LINUX_IP
```

### Step 5: Configure Server Name
The server will generate a random name. You can change it if you want - I'll leave it as-is:

![Server Configuration](https://github.com/user-attachments/assets/b3a5fb69-aeb8-4bc7-9c50-4bf561cf0739)

### Step 6: Close Configuration
Add this JSON to the file, and adjust the `path` and the `IP` accordingly
```json
{
    "mcpServers": {
        "kali_mcp": {
            "command": "python3",
            "args": [
                "c:/logs/mcp_server.py",
                "--server",
                "http://LINUX_IP:5000/"
            ]
        }
    }
}
```
Add instructions: 

<img width="222" height="211" alt="image" src="https://github.com/user-attachments/assets/8343b6f4-dc94-4410-8d89-90e7e78300ac" /> </br>

<img width="602" height="60" alt="image" src="https://github.com/user-attachments/assets/ff4be574-b92d-4b1c-97d7-61e7b9f3e31e" /> </br>

<img width="607" height="68" alt="image" src="https://github.com/user-attachments/assets/3fc6d1d9-c476-4d01-89a0-b21fb8b222de" /> </br>

<img width="605" height="63" alt="image" src="https://github.com/user-attachments/assets/d3dc052a-7b30-42d2-819c-2b1c87ae7cbb" /> </br>

```
---
applyTo: '**'
---
You have access to MCP tools called `kali_mcp` - these tools allow you to search and use an operating system called Kali Linux and run tools and commands available

When you receive a question that involves pentesting, hacking, or any other security-related topic, you should leverage these tools to search for an answer and to fetch content for deep research. in Kali Linux.
```


# Starting the server

<img width="405" height="378" alt="image" src="https://github.com/user-attachments/assets/ba050c6f-b97e-43bf-8e08-0e2178c07fc1" />

<img width="1123" height="141" alt="image" src="https://github.com/user-attachments/assets/92d6ba35-06d9-439d-9fd5-178b6012addb" />


- prompt: `Can you please start doing pentest on the CTF machine at IP: 10.10.215.202`

Note: You might receive a notification like this to proceed with the test:

<img width="461" height="230" alt="image" src="https://github.com/user-attachments/assets/dff90faf-70e4-47e8-88c9-0790e97af25e" />

if everything went `ok`, then now you should see the command running in the Kali box and the VSC


2<img width="1183" height="987" alt="image" src="https://github.com/user-attachments/assets/7b52d098-7e27-418d-8e85-ed5a267186ef" />


