## Step 2: Agent Mode and an MCP Server for GitHub

Great work! You just connected your first MCP server to GitHub Copilot! 🎉

🚨 It seems the teachers keep submitting bugs and requests! So many good ideas! We should probably look into them and start researching for other upgrades.

Fortunately, with an MCP server for GitHub, triaging these and even doing some research to get ahead should be pretty quick! 🕵️

### How do we use an MCP server's tools?

Good news! The same way you would normally interact with Copilot, natural language. Just keep in mind the available capabilities and any permission restrictions from your token.

So, with the MCP Server available, we can now ask Copilot things beyond just our code. Here are some ideas to imagine the possibilities:

For example:

- Searching issues considering description, comments, and likes.
- To open, update, or close issues on another repository.
- Comparing repositories.
- Learning about other authors you are working with.
- Retrieve an issue, make changes on a branch, and start a pull request.

Isn't that cool?! Now let's do it! 👩‍🚀

### :keyboard: Activity: Quickly find and save ideas

1. Close any open files inside your codespace. This will help reduce unnecessary context.

1. Ensure the **Copilot Chat** panel is open and **Agent** mode is selected. Verify the MCP server tools are also still available.

1. Ask Copilot to search GitHub for projects similar to this one.

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Are there any other repositories for organizing extra curricular activities?
   > ```

1. When an MCP tool is required, Copilot will ask for permission. **Verify the request** and modify if necessary, then click **Continue**.

   <img width="250" alt="request permission dialog" src="https://github.com/user-attachments/assets/229473af-c206-47a4-b356-943b9c9bd946" />

1. Ask Copilot to describe one of the projects. Explore until you find something you like.

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Please look at the code for the 3rd option and give me a detailed description of the features.
   > ```

1. Use Copilot to compare and generate ideas for enhancements.

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Please compare these features to our project. Which would be new?
   > ```

1. Nice! Let's have Copilot create issues to save these ideas.

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > I like it. Let's create issues for these.
   > ```

1. Copilot will ask for permission to create issues on your repository. Click **Continue** for each new issue. Reminder: **verify the request** before running.

   <img width="250" alt="request permission dialog" src="https://github.com/user-attachments/assets/52635294-950a-4168-b71e-498eb769f3af" />

1. Since we are done researching, let's finish this chat session to clear the context. At the top of the **Copilot Chat** panel, click the **New Chat** icon (plus sign).

1. With the new issues created, Mona should already be busy checking your work. Give her a moment and keep watch in the comments. You will see her respond with progress info and the next lesson.


> [!NOTE]
> The Model Context Protocol (MCP) landscape is quickly evolving. Many servers, including the [Official GitHub MCP server](https://github.com/github/github-mcp-server) are in active development and do not have full parity with their stable APIs.
