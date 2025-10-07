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
Add the official MCP URL:
```
https://learn.microsoft.com/api/mcp
```

![Add MCP URL](https://github.com/user-attachments/assets/44fd6819-0aed-45c6-9fbc-ffcfcabd8ed1)

### Step 5: Configure Server Name
The server will generate a random name. You can change it if you want - I'll leave it as-is:

![Server Configuration](https://github.com/user-attachments/assets/b3a5fb69-aeb8-4bc7-9c50-4bf561cf0739)

### Step 6: Close Configuration
The configuration will appear, which you can close. 

👉 If you ever want to remove it, just remove the entire content of this file.

![Configuration Complete](https://github.com/user-attachments/assets/7228e6ef-baee-4b47-b610-d95bb7502b37)

## 📝 Configuring Chat Instructions

### Step 1: Add New Chat Window
Create a new chat window

![New Chat](https://github.com/user-attachments/assets/bec7cd4c-9403-4e27-83a1-b9ad01fa9f2b)

### Step 2: Open Settings
Click the gear icon in the top right corner

![Settings Icon](https://github.com/user-attachments/assets/a7c6ef44-a21a-49dc-8119-60b764a7c6f3)

### Step 3: Add New Instructions
Click "New Instructions"

![New Instructions](https://github.com/user-attachments/assets/eede8ddd-bda2-49e0-9e03-0e1ef42822c4)

### Step 4: Select User Data Folder
Choose "User Data Folder" (Recommended)

![User Data Folder](https://github.com/user-attachments/assets/2e3510cc-b739-49da-b00b-7e32fba0c8ad)

### Step 5: Give it a Name
Give it any name you want, then press ENTER

![Name Your Instructions](https://github.com/user-attachments/assets/86a28d36-8abe-498a-8c3c-f3d334144a3c)

### Step 6: Add Instruction Content
Your instruction should look something along these lines:

```markdown
---
applyTo: '**'
---
You have access to MCP tools called `microsoft_docs_search` and `microsoft_docs_fetch` - these tools allow you to search through and fetch Microsoft's latest official documentation, and that information might be more detailed or newer than what's in your training data set.

If a question includes Intune, config manager, Exchange, Teams, Outlook, and all other Microsoft products, services, or technology, you should leverage these tools to search for an answer and to fetch content for deep research.
```

![Instruction Content](https://github.com/user-attachments/assets/c1ad4f3b-75a5-4b5b-a2a4-f35d3c366cb1)

### Step 7: Save Instructions
Press `Ctrl` + `S` to save, then you can close this window.

If you get a message to allow sensitive files in the Copilot instruction, you can skip it since you just saved it above.

![Save Instructions](https://github.com/user-attachments/assets/902b3f03-deeb-48db-955c-0c89d384d6c9)

## 🧪 Time for Testing

For this example, I will prompt for:
```
I'm trying to add a bundle id to an app configuration profile policy in intune but I'm not sure on what format I should use
```

👉 if you have not configured your Copilot then this popup will come up, choose your sign-in Accordingly, Restart after its setup

<img width="374" height="450" alt="image" src="https://github.com/user-attachments/assets/c2930c45-beb4-4991-a5a9-b87fd59174ee" />

👉 A way to see if the MCP server is ready is by: `> MCP` List Servers > Right Click to the one created > then Choose your option accordingly

<img width="590" height="369" alt="image" src="https://github.com/user-attachments/assets/a80643b8-7d26-4694-a4ab-a2446e9341e3" />



If you did it correctly, you should see the reference from the `MCP Server` like so:

![Test Result](https://github.com/user-attachments/assets/944cdc5e-b52d-4d31-a435-48a52cf6bbdf)

* On regular search that did not have to do with our above instructions, it would not pick up any fetching:

![Regular Search](https://github.com/user-attachments/assets/a247f0bc-f0df-492d-aa49-a2b128c764f5)

## 📦 Repository

Find the official MCP server repository here: [Microsoft MCP Server](https://github.com/microsoftdocs/mcp)
