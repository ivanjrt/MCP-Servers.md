# Context: 
MCP Servers offer flexible configuration options at both the user and workspace levels. User-level settings automatically apply across all VS Code sessions, </br>
making this approach particularly practical for Users working with Microsoft technologies.  </br>
Additionally, you can establish MCP settings specific to workspaces utilizing Microsoft technologies while simultaneously configuring different MCP Servers for non-Microsoft workspace environments. </br> </br>

# Requirments:
* Install Visual Studio Code: https://code.visualstudio.com/  </br>
* Install this Extension: `GitHub Copilot` https://marketplace.visualstudio.com/items?itemName=GitHub.copilot </br>
<img width="836" height="316" alt="image" src="https://github.com/user-attachments/assets/65854041-0494-4b9e-baf3-84b4dc2c7971" /> </br>

* Grab the Official MCP URL from the doc: https://learn.microsoft.com/en-us/training/support/mcp-get-started  >
```
https://learn.microsoft.com/api/mcp
```

# Adding the Server in VSC:
At the top search for `VSC` Type `>MCP`  </br>
<img width="604" height="67" alt="image" src="https://github.com/user-attachments/assets/c0b3bf38-2c75-4c2b-a7c4-bb675628b98c" /> </br> </br>
Add New `server`: </br>
<img width="603" height="75" alt="image" src="https://github.com/user-attachments/assets/9652f5f2-0a14-4de3-8bd3-0d65e623a3af" /></br> </br>
Select `HTTP` </BR>
<img width="606" height="85" alt="image" src="https://github.com/user-attachments/assets/51431efc-f484-4ac1-aba7-6d5083b7baff" /> </BR> </br>
Add the MCP URL  </br>
<img width="599" height="104" alt="image" src="https://github.com/user-attachments/assets/44fd6819-0aed-45c6-9fbc-ffcfcabd8ed1" /> </br> </br>
It will generate a random name, and you can change it if you want. I'll leave it as-is: </br>
<img width="603" height="97" alt="image" src="https://github.com/user-attachments/assets/b3a5fb69-aeb8-4bc7-9c50-4bf561cf0739" /> </br> </br>
Then  its config will come up, which you can close (👉 if you ever want to remove it, just remove the entire content of this file) </br>
<img width="1019" height="264" alt="image" src="https://github.com/user-attachments/assets/7228e6ef-baee-4b47-b610-d95bb7502b37" /> </br> </br>

# Configuring Chat:
Add a new chat window: </br>
<img width="747" height="75" alt="image" src="https://github.com/user-attachments/assets/bec7cd4c-9403-4e27-83a1-b9ad01fa9f2b" /> </br> </br>
At the top right corner, click the gear icon: </br>
<img width="325" height="251" alt="image" src="https://github.com/user-attachments/assets/a7c6ef44-a21a-49dc-8119-60b764a7c6f3" /> </br> </br>
New Instructions: </br>
<img width="601" height="82" alt="image" src="https://github.com/user-attachments/assets/eede8ddd-bda2-49e0-9e03-0e1ef42822c4" /> </br> </br>
User Data Folder: (Recommended) </br>
<img width="606" height="61" alt="image" src="https://github.com/user-attachments/assets/2e3510cc-b739-49da-b00b-7e32fba0c8ad" /> </br> </br>
Give it any name you want, then ENTER: </br>
<img width="607" height="69" alt="image" src="https://github.com/user-attachments/assets/86a28d36-8abe-498a-8c3c-f3d334144a3c" /> </br> </br>
Your instruction should look something along these lines:
```
---
applyTo: '**'
---
You have access to MCP tools called `microsoft_docs_search` and `microsoft_docs_fetch` - these tools allow you to search through and fetch Microsoft's latest official documentation, and that information might be more detailed or newer than what's in your training data set.

If a question includes a Intune, config manager, Exchange, Teams, Outlook, and all other Microsoft products, services, or technology, you should leverage these tools to search for an answer and to fetch content for deep research.
```
<img width="1458" height="208" alt="image" src="https://github.com/user-attachments/assets/c1ad4f3b-75a5-4b5b-a2a4-f35d3c366cb1" /> </br>
then `ctrl` + `S` to save, you can now close this window. </br>
if you got a message to allow sensitive files in the Copilot instruction, you could skip, cause you just saved it above </br>
<img width="945" height="146" alt="image" src="https://github.com/user-attachments/assets/902b3f03-deeb-48db-955c-0c89d384d6c9" /> </br> </br>


# Time for testing:
For this example, I will prompt for: </br>
```
how to create and assign SCEP certificate profiles in Intune?
```
If you did it correctly then it, you should see the reference from the `MCP Server` like so:  </br>
<img width="1935" height="949" alt="image" src="https://github.com/user-attachments/assets/195f4bc5-4cd1-4b17-ba8b-a669068c011f" /> </br>

* On regular search that did not have to see with our above instructions, it would not pick up any fetching: </br>
<img width="960" height="187" alt="image" src="https://github.com/user-attachments/assets/a247f0bc-f0df-492d-aa49-a2b128c764f5" />




# Repo for server:
https://github.com/microsoftdocs/mcp



