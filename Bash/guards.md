# Guard Clauses

A collection of guard clauses. Defensive programming patterns used at the \
beginning of a script to fail fast, exit early, or skip execution if required \
conditions are not met.

## Environment & Privilege

Require root

```bash
# Require root.
if [ "$EUID" -ne 0 ]; then
  echo "Error: This script must be run as root (or with sudo)." >&2
  exit 1
fi
```

- Ensures script is run as root.

Prevent root

```bash
# Prevent root.
if [ "$EUID" -eq 0 ]; then
  echo "Error: Do not run this script as root." >&2
  exit 1
fi
```

- Ensures script is not run as root.

## Dependency / Command availability check

Verify required CLI utilities are installed.

```bash
# Verify single required command.
if ! command -v jq &> /dev/null; then
  echo "Error: 'jq' is required but not installed." >&2
  exit 1
fi
```

- Single command check.

```bash
# Require multiple required commands.
for cmd in git curl docker; do
    if ! command -v "$cmd" &> /dev/null; then
    echo "Error: Required command '$cmd' is not found in PATH." >&2
  fi
done
```

- Multi-command loop check.

### Argument & Input

Required number of arguments.

```bash
# Require specific number of arguments.
if [[ $# -ne 2 ]]; then
  echo "Usage: $0 <source_dir> <target_dir>" >&2
  exit 1
fi
```

- Requires exactly 2 arguments.

```bash
Requre one or more arguments.
if [[ $# -lt 1 ]]; then
  echo "Error: At least one argument is required." >&2
  exit 1
fi
```

- Requires at least 1 argument.

Non-Empty Argument Check.

```bash
# Check for empty argument.
if [[ -z "${1:-}" ]]; then
  echo "Error: Argument 1 cannot be empty." >&2
  exit 1
fi
```

- Ensures an argument is not empty.

Alphabetic Input Validation

```bash
# Validate alphabetic input.
local input_val="$1"
if ! [[ "$input_val" =~ ^[a-zA-Z]+$ ]]; then
  echo "Error: Parameter '$input_val' must only contain letters." >&2
  exit 1
fi
```

- Check that a variable or value is alphabetic only.

Numeric Input Validation

```bash
# Validate numeric input.
local input_val="$1"
if ! [[ "$input_val" =~ ^[0-9]+$ ]]; then
  echo "Error: Parameter '$input_val' must be a positive integer." >&2
  exit 1
fi
```

-Check that a variable or value is numeric only.

Alphanumeric Input Validation

```bash
# Validate alphanumeric input.
local input_val="$1"
if ! [[ "$input_val" =~ ^[a-zA-Z0-9]+$ ]]; then
  echo "Error: Parameter '$input_val' must only be alphanumeric." >&2
  exit 1
fi
```

- Check that a variable or value is alphanumeric only.

Word Input Validation

```bash
# Validate word input.
local input_val="$1"
if ! [[ "$input_val" =~ ^[a-zA-Z0-9_]+$ ]]; then
  echo "Error: Parameter '$input_val' must be a word only." >&2
  exit 1
fi
```

- Check that a variable or value is only a word only.

Word Input Validation

```bash
# Validate word input.
local input_val="$1"
if ! [[ "$input_val" =~ ^[a-zA-Z0-9_]+$ ]]; then
  echo "Error: Parameter '$input_val' must be a word only." >&2
  exit 1
fi
```

- Check that a variable or value is not alphabetic only.

## File System & Path

Directory Existence

```bash
# Early exit/return if directory does not exist.
if [[ ! -d "$TARGET_DIR" ]]; then
  echo "Error: Directory '$TARGET_DIR' does not exist." >&2
  exit 1
fi
```

- Ensures a target directory exitst before changing into or reading from it.

File Existence

```bash
# Early exit/return if file does not exist.
if [[ ! -f "$CONFIG_FILE" ]]; then
  echo "Error: Configuration file '$CONFIG_FILE' not found." >&2
  exit 1
fi

-  Guards scripts that require reading or modifying a specific file.
