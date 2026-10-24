# Bash code snippets and blocks
A collection of code snippets for Bash scripting. 

## Guard Clauses
Defensive programming patterns used at the beginning of a script to fail fast, exit early, or skip execution if required conditions are not met.

### Environment & Privilege

#### Require root
Ensures script is run as root.
```bash
if [ "$EUID" -ne 0 ]; then
  echo "Error: This script must be run as root (or with sudo)." >&2
  exit 1
fi
```

#### Prevent root
Ensures script is not run as root.
```bash
if [ "$EUID" -eq 0 ]; then
  echo "Error: Do not run this script as root." >&2
  exit 1
fi
```

#### Dependency / Command availability check
Verifies required CLI utilities are installed
```bash
# Single command check.
if ! command -v jq &> /dev/null; then
  echo "Error: 'jq' is required but not installed." >&2
  exit 1
fi

# Multi-command loop check.
for cmd in git curl docker; do
    if ! command -v "$cmd" &> /dev/null; then
    echo "Error: Required command '$cmd' is not found in PATH." >&2
  fi
done
```

### Argument & Input

#### Required Number of Arguments

```bash
# Requires exactly 2 arguments.
if [[ $# -ne 2 ]]; then
  echo "Usage: $0 <source_dir> <target_dir>" >&2
  exit 1
fi

# Requires at least 1 argument.
if [[ $# -lt 1 ]]; then
  echo "Error: At least one argument is required." >&2
  exit 1
fi

#### Non-Empty Argument Check

```bash
if [[ -z "${1:-}" ]]; then
  echo "Error: Argument 1 cannot be empty." >&2
  exit 1
fi
```

#### Numeric Input Validation

```bash
local input_val="$1"
if ! [[ "$input_val" =~ ^[0-9]+$ ]]; then
  echo "Error: Parameter '$input_val' must be a positive integer." >&2
  exit 1
fi
```

## Variables Assignments

### Script root
Used for installation scripts or similar to define the script root for relative paths.
```bash
SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"
```
