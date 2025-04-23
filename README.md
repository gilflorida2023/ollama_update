# Ollama Model Update Script

## Overview

The `ollama_update` script is a Bash script designed to check and update all installed Ollama large language models (LLMs) to their latest versions. It automates the process of pulling the newest model versions from the Ollama repository.

## Prerequisites

- **Ollama**: Ensure the Ollama CLI is installed and configured on your system.
- **Bash**: The script runs in a Bash environment (Linux, macOS, or WSL on Windows).
- **Permissions**: The script must be executable. Run `chmod +x ollama_update` to grant execute permissions.

## Script Details

**File**: `ollama_update`

**Purpose**: Lists all installed Ollama models and pulls their latest versions.

**Code**:
```bash
#!/bin/bash
echo "Checking for updates for all installed Ollama models..."
ollama list | awk 'NR>1 {print $1}' | while read -r model; do
  echo "--- Pulling $model ---"
  ollama pull "$model"
  echo "--- Done with $model ---"
done
echo "All checks/updates complete."
