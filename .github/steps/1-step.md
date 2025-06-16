## Step 1: Introduction to MCP and environment setup

<img width="150" align="right" alt="copilot logo" src="https://github.com/user-attachments/assets/4d22496d-850b-4785-aafe-11cba03cd5f2" />

In the [Getting Started with GitHub Copilot](https://github.com/skills/getting-started-with-github-copilot) exercise, we were introduced to the Mergington High School's extracurricular activities website, which allowed students to sign up for events.

And now we have a problem... but.. it's a good one! More teachers are asking to use it! 🎉

Our fellow teachers have lots of ideas but we can't seem to keep up with all the requests! 😮 To fix this issue, lets give GitHub Copilot an upgrade by enabling Model Context Protocol (MCP). To be more specific, we will add the GitHub MCP server, which will enable a combined workflow of issue management and website upgrades. 🧑‍🚀

Let's get started!

### What is Model Context Protocol (MCP)?

[Model Context Protocol (MCP)](https://modelcontextprotocol.io/introduction) is often referred to as "USB-C for AI" - a universal connector that allows GitHub Copilot (and other AI tools) to seamlessly interact with other services.

Essentially, it is a way to describe the capabilities and requirements of a service, so AI tools can easily determine what methods to use and to accurately provide the parameters. An MCP server is providing that interface.

```mermaid
graph LR
    A[Developer] -->|Uses| B[GitHub Copilot]
    B -->|Unified API| MCP[Model Context Protocol]

    MCP <-->|Unique API| C[(GitHub)]
    MCP <-->|Unique API| D[(Slack)]
    MCP <-->|Unique API| E[(Figma)]

    style B fill:#4CAF50,stroke:#333,stroke-width:2px

    subgraph "Less Context Switching, More Coding"
        B
        MCP
        C
        D
        E

    end
```

### :keyboard: Activity: Get to know your environment

Before we dive into MCP, let's start up our development environment and refamiliarize ourself with the extracurricular activity application.

1. Right-click the below button to open the **Create Codespace** page in a new tab. Use the default configuration.

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

1. Validate the **Copilot Chat** and **Python** extensions are installed and enabled.

   <img width="300" alt="copilot extension for VS Code" src="https://github.com/user-attachments/assets/ef1ef984-17fc-4b20-a9a6-65a866def468" /><br/>
   <img width="300" alt="python extension for VS Code" src="https://github.com/user-attachments/assets/3040c0f5-1658-47e2-a439-20504a384f77" />

1. Verify our application runs before modification. In the left sidebar, select the **Run and Debug** tab and then press the **Start Debugging** icon.

   <details>
   <summary>📸 Show screenshot</summary><br/>

   <img width="300" alt="run and debug" src="https://github.com/user-attachments/assets/50b27f2a-5eab-4827-9343-ab5bce62357e" />

   </details>

   <details>
   <summary>🤷 Having trouble?</summary><br/>

   If the **Run and Debug** area is empty, try reloading VS Code: Open the command palette (`Ctrl`+`Shift`+`P`) and search for `Developer: Reload Window`.

   <img width="300" alt="empty run and debug panel" src="https://github.com/user-attachments/assets/0dbf1407-3a97-401a-a630-f462697082d6" />

   </details>

1. Use the **Ports** tab to find the webpage address, open it, and verify it is running.

   <details>
   <summary>📸 Show screenshot</summary><br/>

   <img width="350" alt="ports tab" src="https://github.com/user-attachments/assets/8d24d6b5-202d-4109-8174-2f0d1e4d8d44" />

   ![Screenshot of Mergington High School WebApp](https://github.com/user-attachments/assets/5cb88d53-d948-457e-9f4b-403d697fa93a)

   </details>

### :keyboard: Activity: Add the GitHub MCP server

1. Inside your codespace, open the **Copilot Chat** panel and verify **Agent** mode is selected.

   <img width="200" alt="image" src="https://github.com/user-attachments/assets/201e08ab-14a0-48bf-824e-ba4f8f43f8ab" />

   <details>
   <summary>Agent mode missing?</summary><br/>

   - Verify VS Code is at least `v1.99.0`.
   - Verify the Copilot extension is at least `v1.296.0`.
   - Check if Agent mode is enabled in your [user or workspace settings](https://code.visualstudio.com/docs/configure/settings#_workspace-settings).

      <img width="300" alt="image" src="https://github.com/user-attachments/assets/407a79dd-707e-471b-b56b-1938aece4ad8" />

   </details>

1. Inside your codespace, create a new file named `mcp.json` in the `.vscode` directory and paste the following contents:

   📄 **.vscode/mcp.json**

   ```json
   {
     "servers": {
       "github": {
         "command": "docker",
         "args": [
           "run",
           "-i",
           "--rm",
           "-e",
           "GITHUB_PERSONAL_ACCESS_TOKEN",
           "ghcr.io/github/github-mcp-server:v0.1.1"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:github_token}"
         }
       }
     },
     "inputs": [
       {
         "type": "promptString",
         "id": "github_token",
         "description": "GitHub Personal Access Token",
         "password": true
       }
     ]
   }
   ```

   > :placard: **Note:** Entering a hard-coded token is never recommended, you should use input variables or envFiles when an MCP server requires credentials.

1. Expand the VS Code terminal panel. Run the following command to view and **make a copy** of your codespace's GitHub Token.

   ```bash
      echo $GITHUB_TOKEN
   ```

   <details>
   <summary>Why do I need this?</summary><br/>

   The MCP server is a separate background process and needs credentials to perform operations. In this case, we use the temporary [codespace authorization](https://docs.github.com/en/enterprise-cloud@latest/codespaces/reference/security-in-github-codespaces#authentication) credential which becomes invalid when the codespace stops.

   </details>

1. In the `.vscode/mcp.json` file, click the **Start** button and provide the token. This has just informed GitHub Copilot of the MCP server's capabilities.

   ![image](https://github.com/user-attachments/assets/62ee9c06-e9d4-44e4-b6df-f93417474af2)

   ![image](https://github.com/user-attachments/assets/33195908-affe-488f-afef-e759498d1fe8)

1. In the Copilot side panel, click the **🛠️ Select Tools...** icon to show the additional capabilities.

   <img width="250" alt="image" src="https://github.com/user-attachments/assets/95af044c-3f26-4f5c-b933-7630db72eb67" />

   <img width="250" alt="image" src="https://github.com/user-attachments/assets/99178d1b-adbe-4cf4-ab9c-3a4d29918a13" />

1. **Commit** and **push** the `.vscode/mcp.json` file to the `main` branch.

   > 🪧 **Note:** Pushing directly to `main` is not a recommended practice. It is only to simplify this exercise.

1. Now that your MCP server configuration is pushed to GitHub, Mona should already be busy checking your work. Give her a moment and keep watch in the comments. You will see her respond with progress info and the next lesson.

> [!NOTE]
> The next steps will involve creating GitHub issues. If you would like to avoid notification emails, you can unwatch the repository.

<details>
<summary>Having trouble?</summary><br/>

Make sure:

- Your `.vscode/mcp.json` file is similar to the example provided.
- You pushed the changes to the `main` branch.

</details>
