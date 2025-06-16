## Step 3: Solve issues with Agent Mode and GitHub MCP Server

Great work doing that research and finding a potential collaboration opportunity.
Not only did we find some new ideas to help organize extracurricular activities, but we did all that quickly too.

Plenty of time to focus on the fun stuff, like teaching our awesome students! 🌱

On that note, it seems the teachers have also been active.
Looks like they submitted some bugs and requests! Perfect! 🚀

Now, let's use our MCP server's tools and Copilot to do a bit of triage and get some work done.

### :keyboard: Activity: Easily implement an important issue

1. Ensure the **Copilot Chat** panel is open and **Agent** mode is selected. Verify the MCP server tools are also still available.

1. Ask Copilot about the open issues.

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > #codebase How many open issues are there?
   > ```

   > :placard: **Note:** In our tests, we found that Copilot sometimes gets confused about the repository owner here. We chose to add `#codebase` to reduce this ambiguity and make the lesson smoother.

1. Ask Copilot to summarize the important issues.

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Oh no. That's too many for me! Please get the list of issues,
   > review the descriptions and comments, and pick the top 3 most important.
   > ```

   <details>
   <summary> <b> 💡 Tip:</b> Pre-authorize tool usage</summary><br/>

   If Copilot uses a tool often, you can proactively grant permission for the rest of the conversation session.

   <img width="350" src="https://github.com/user-attachments/assets/d741191e-4d98-489d-92d2-f1069fd6c34e"/>

   </details>

1. Review the suggested issues. If Copilot didn't give a specific recommendation, try providing some feedback to narrow the results.

1. With the list narrowed, ask Copilot to implement an issue. **Mona won't grade if the changes work, just that an attempt was made.**

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > #codebase Let's do the first one. Follow these steps:
   > 1. Checkout a new local branch for making our changes.
   > 2. Make the changes then confirm with me that they look correct.
   > 3. Push the changes and start a pull request.
   > ```

   > ⚠️ **Warning:** Always verify the the actions Copilot is asking to perform, especially with the external abilities provided by an MCP server, which probably have no undo option.

1. Once the pull request is created, Mona will start checking your work. Give her a moment and keep watch of the comments. You will see her respond with progress info and the next step!

<details>
<summary>Having trouble?</summary><br/>

- If tools are not being requested, verify your MCP configuration is correct.
- If Copilot cannot retrieve results, verify you are using this Codespace's token or a Personal Access Token (PAT) with appropriate permissions. By default, the codespace token we are using only has access to this repository.

</details>
