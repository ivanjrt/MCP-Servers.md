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
