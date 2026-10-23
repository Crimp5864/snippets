# Bash code snippets and blocks

## Variables

### Script root
Used for installation scripts or similar to define the script root for relative paths.
```bash
SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"
```

## Guard Clauses

### Check for root
Require root
```bash
if [ "$EUID" -ne 0 ]; then
  echo "Error: This script must be run as root (or with sudo)." >&2
  exit 1
fi
```

Prevent root
```bash
if [ "$EUID" -eq 0 ]; then
  echo "Error: Do not run this script as root." >&2
  exit 1
fi
```
