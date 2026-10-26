# Regex Expressions

Commonly used regex expressions

## Digits & Numbers

### Positive integers (Whole numbers only):

```bash
^[0-9]+$
```

- Use case: Validating that a user input or variable contains only numbers.

### Decimals/Floats:

```bash
^[0-9]+(\.[0-9]+)?$
```

- Use case: Checking for numbers that may include a decimal point.

## Networking & System Admin

### IPv4 Addresses:

```bash
^([0-9]{1,3}\.){3}[0-9]{1,3}$
```

- Use case: Basic validation for IP address strings.

### MAC Addresses:

```bash
^([0-9A-Fa-f]{2}[:-]){5}([0-9A-Fa-f]{2})$
```

- Use case: Matching hardware MAC addresses formatted with colons or hyphens.

## File & Code Patterns

### File Extensions:

```bash
\.sh$
```

- Use case: Check if a filename string ends with a specific extension.

### Git Commit Hashes:

```bash
^[0-9a-f]{7,40}$
```

- Use case: Validate short (7 character) or full-length hexadecimal commit hashes.

## Text & Data Formatting

### Email Addresses

```bash
^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
```

- Use case: Simple structural check for valid email formats.

### Blank or Whitespace-Only Lines:

```bash
^[[:space:]]+$
```

- Use case: Filter out empty lines when looping through configuration or log files.

### Example: How to Use Regex in a Bash Script:

To use a regex directly in Bash without calling external tools looks like `grep`, use the [[ ... =~ ... ]] conditional syntax:

```bash
#!/usr/bin/env bash

read -p 'Enter a number: ' input

if [[ "$input" =~ ^[0-9]+$ ]]; then
  echo 'Valid! You entered a positive integer.'
else
  echo 'Error: Not a valid integer.'
fi
```
