---
name: repository-to-private
description: Change the current GitHub repository visibility to private
disable-model-invocation: true
allowed-tools: Bash(gh *)
---

# Make Repository Private

Get the current repository name and change its visibility to private.

Current repo: !`gh repo view --json nameWithOwner -q .nameWithOwner 2>/dev/null || echo "NOT_A_GITHUB_REPO"`

Run this command to make the repository private:

```bash
gh repo edit --visibility private --accept-visibility-change-consequences
```

After running, confirm success by showing the new visibility:

```bash
gh repo view --json visibility -q .visibility
```

Report the result to the user clearly, including the repository name and new visibility status.
