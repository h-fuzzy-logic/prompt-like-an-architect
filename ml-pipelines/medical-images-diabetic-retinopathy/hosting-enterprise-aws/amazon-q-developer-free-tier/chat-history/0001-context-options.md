
\> help me understand what workspace indexing options are available here in VS code when using the extension.  i&#39;d like to be able to specify which files are part of the context. for example, i&#39;d like to exclude the images/ directory but I&#39;d like to include the docs/ directory. 

when i&#39;ve seen the context listed in the chat window, only the rules files and two readme files are being referenced

---

Let me help you understand Amazon Q's workspace indexing options in VS Code. Here are the available methods to control what files are included in context:

## 1. .amazonqignore File (Exclusion Only)
Your current approach - excludes files from indexing:
```
# Exclude images directory
images/
*.png
*.jpg
```

## 2. VS Code Workspace Settings
Create `.vscode/settings.json` in your workspace:
```json
{
  "amazonQ.workspaceIndexIgnoreFilePatterns": [
    "images/**",
    "*.png",
    "node_modules/**"
  ]
}
```

## 3. Explicit File/Folder References
Use `@` syntax to explicitly include specific files or folders:
- `@docs` - Include entire docs directory
- `@README.md` - Include specific file
- `@workspace` - Include relevant workspace context

## 4. Amazon Q Rules (Auto-Included)
Files in `.amazonq/rules/` are automatically included in context - this explains why you see your s3-security.md rule file.

## 5. Smart Context Selection
Amazon Q automatically selects relevant files based on:
- Currently open files
- Recently modified files
- Files related to your question
- Project structure files (README, package.json, etc.)

## Why You're Only Seeing Rules + READMEs
This is Amazon Q's **smart context selection** - it's prioritizing:
- Rule files (always included)
- README files (project overview)
- Files relevant to your current question

## To Include docs/ Directory
Try these approaches:
1. **Explicit reference**: Use `@docs` in your chat messages
2. **Open docs files**: Open files from docs/ in VS Code tabs
3. **Ask about docs**: "What's in my docs directory?" to trigger indexing

The key insight: Amazon Q uses **selective context** rather than indexing everything. It chooses relevant files dynamically based on your questions and current work.