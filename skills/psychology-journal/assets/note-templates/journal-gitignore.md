# Journal Git Exclusions

Create the journal's `.gitignore` with exactly these baseline entries:

```gitignore
.DS_Store
.env
.env.*
*.key
*.pem
*.tmp
*.bak
/private/
.psychology-companion.local.json
__pycache__/
```

Add another exclusion only when the user requests it or a new local data type
materially requires it. This file does not initialize Git.
