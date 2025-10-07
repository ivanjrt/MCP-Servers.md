## ️ Adding the n8n Server in VS Code
# Source: https://github.com/czlonkowski/n8n-mcp
# Requirement:
- Install nodeJS, msi > https://nodejs.org/en/download
- Make sure you have configured your github account

<img width="656" height="164" alt="image" src="https://github.com/user-attachments/assets/b6ed9d2c-703e-4e5e-a730-af9349885c07" />

- Add typical settings, unless you otherwise know

<img width="612" height="480" alt="image" src="https://github.com/user-attachments/assets/5d8d64b7-bc1c-47fc-93d8-dee03c8c2676" />

<img width="614" height="483" alt="image" src="https://github.com/user-attachments/assets/3c4d661d-28aa-4313-99c5-0e9ea57c1065" />

_incl the PowerShell section, time to brew some 🍵_

Install the - Node Package Execute `npx` by 
```
npm install -g npx
```


### Step 1: Open Command Palette
Type `>MCP` in the command palette (search for `VSC` at the top)

![Command Palette](https://github.com/user-attachments/assets/c0b3bf38-2c75-4c2b-a7c4-bb675628b98c)

### Step 2: Add New Server
Click "Add New Server"

![Add New Server](https://github.com/user-attachments/assets/9652f5f2-0a14-4de3-8bd3-0d65e623a3af)

### Step 3: Adding server
<img width="752" height="119" alt="image" src="https://github.com/user-attachments/assets/85ae9573-70f6-40f9-8ac8-8c6e8df2c8da" />

### Step 4: NPM Package
<img width="751" height="250" alt="image" src="https://github.com/user-attachments/assets/d5c24161-55d7-4756-93c9-d9d26383cd26" />

### Step 5: Enter the package name `n8n`
<img width="757" height="125" alt="image" src="https://github.com/user-attachments/assets/8398f7e7-e0f2-4885-87c6-842d8e77801e" />

<img width="765" height="150" alt="image" src="https://github.com/user-attachments/assets/2425b8aa-ca99-4e41-835b-95f3729018ae" />

### Step 6: give it a name:
<img width="755" height="116" alt="image" src="https://github.com/user-attachments/assets/f192d4c9-e76d-46bc-b629-b6da0e162b4b" />

If you did it correctly, then you should see this sample configuration:
<img width="1217" height="560" alt="image" src="https://github.com/user-attachments/assets/971c69a9-a024-46f8-b8cf-43a3141da83f" />

### Configuring the settings for the server ###
We need to adjust this code to it.
```json
{
  "mcpServers": {
    "n8n-mcp": {
      "command": "npx",
      "args": ["n8n-mcp"],
      "env": {
        "MCP_MODE": "stdio",
        "LOG_LEVEL": "error",
        "DISABLE_CONSOLE_OUTPUT": "true"
      }
    }
  }
}
```
At the end, it will look like so: -_make sure you save the file_

<img width="672" height="540" alt="image" src="https://github.com/user-attachments/assets/e9cd3ad0-6758-4fc5-90e6-cb0d371b9109" />

If you did it correctly, you can now start the server by going to: `>mcp` `List Servers` -Select the n8n server just created -_right click_  > Start


<img width="1193" height="320" alt="image" src="https://github.com/user-attachments/assets/d73403b1-108e-4962-ae5c-75231a6757d3" />

<img width="768" height="133" alt="image" src="https://github.com/user-attachments/assets/96e0f0b7-c034-439b-8146-652c3ff2e328" />

<img width="771" height="196" alt="image" src="https://github.com/user-attachments/assets/b6d474d2-39b3-4c2f-bbfc-03863fa575b7" />

If you did that correctly, then you can see the discovered tools from the repo. 

<img width="1144" height="317" alt="image" src="https://github.com/user-attachments/assets/764c1a03-f3fb-4b8e-b8c8-f53f2c425a66" />



