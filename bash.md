# Bash code snippets and blocks

## Variables

### Script root
Used for installation scripts or similar to define the script root for relative paths.
```bash
SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"
