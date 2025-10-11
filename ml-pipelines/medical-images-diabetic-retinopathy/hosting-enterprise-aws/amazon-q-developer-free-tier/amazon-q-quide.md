# Amazon Q Developer Guide: Free Tier with VS Code
Things are changing fast wtih Amazon Q Developer. This information was last verified on August 14, 2025. 

## Contents
- [Quick Start](#quick-start)
- [Best Practices](#best-practices)
- [Advanced Tps](#advanced-tips)
- [What Doesn't Work](#what-doesnt-work-save-your-time)

# Why Amazon Q?
Decided to try Amazon Q Developer Free Tier from VS Code IDE for several reasons:
1. I'm still on the waitlist for the new AWS IDE Kiro.
1. The Free Tier offers a fair amount of monthly usage for FREE.
1. Amazon Q Developer is developed by AWS and should have the most up-to-date info about AWS services and best practices which should yield the best advice for AWS architectures. 

## Quick Start
Use the latest AWS documentation to install the Amazon Q VS Code extension and authenticate. 

## Key Features of Amazon Q
1. Chats history is saved by default. This is especially handy if are interrupted or need to restart your IDE. 
1. A markdown file of your chat history is available.  Use the `Export` button at the top of the chat panel to download the .md file.
1. `@Pin Context` button is available in the chat box.
1. Rules to specify your project's needs can be added from the chat box by clicking `Rules`.

## Best Practices
These are some tips to get the best responses from Amazon Q. They are based on the AWS documentation, me prompting Q, and sleuthing around on my filesystem and using developer tools to understand what is happening behind the scenes. 

### For your repo 
1. Do not put anything sensitive in your repo
1. Have an up-to-date `.gitignore` file
1. Use Amazon Q Rules 

### When using the chat window
1. Set the context with each prompt with the `@` symbol
1. Use "Pin Context" for files that always need to be included
1. Keep an eye on the chat responses to verify the context is as expected

## Advanced Tips 
Bad news for the control freaks using Amazon Q Developer Free Tier inside VS Code. You won't have 100% control over the the context included with each prompt you send or the workspace indexing. 

### Controlling context 
Amazon Q automatically selects relevant files based on:
- Currently open files
- Recently modified files
- Files related to your question
- Project structure files (README, package.json, etc.)

Enabling the setting "Amazon Q: Workspace Index" and add @workspace to your question may update your workspace index. And Q should honor your existing `.gitignore` file, so files already excluded from git won't be indexed. 

### Amazon Q Rules
Files in `.amazonq/rules/` are automatically included in context and you can see this with responses in the chat panel.

### To Include a specific Directory (like docs/)
Try these approaches:
1. **Explicit reference**: Use `@docs` in your chat messages
2. **Open docs files**: Open files from docs/ in VS Code tabs
3. **Ask about docs**: "What's in my docs directory?" to trigger indexing

## What Doesn't Work (Save Your Time)
Sharing these to save other people time and share ideas for experimentation. 
1. Adjust settings `"amazonQ.workspaceIndexIgnoreFilePatterns": ["*.png"]` 
1. Use `.amazonqignore` file
1. `Developer: Reload Window`
1. Close and re-open VS Code to force re-indexing or use 
1. Removing .aws/amazonq/cache/cache to force a rebuild of the indexes

## Repo characteristics that may be unfamiliar to Q
This repo may not be the typical type of repo that Q is designed to work with. This repo is:
1. New with lots of adding and deleting of files. (Q seems to not realize when some files are deleted or added.)  
1. Smaller in size 
1. Starting with no code samples, just documentation 

## Future experiments
1. Toggle other settings to see if that gives more control ("Amazon Q: Share Content With AWS")
1. Try workspace indexing again when the workspace is larger. Wondering if Q is keeping things in memory since the repo is so small. 
1. Amazon Q Developer Pro offers more customizations. See AWS documentation for details. 
1. Explore the VS Code Output tab filtered to Amazon Q Logs