---
name: repository-to-public
description: Change the current GitHub repository visibility to public
disable-model-invocation: true
allowed-tools: Bash(gh *)
---

# Make Repository Public

Get the current repository name and change its visibility to public.

Current repo: !`gh repo view --json nameWithOwner -q .nameWithOwner 2>/dev/null || echo "NOT_A_GITHUB_REPO"`

Run this command to make the repository public:

```bash
gh repo edit --visibility public --accept-visibility-change-consequences
```

After running, confirm success by showing the new visibility:

```bash
gh repo view --json visibility -q .visibility
```

Report the result to the user clearly, including the repository name and new visibility status.
