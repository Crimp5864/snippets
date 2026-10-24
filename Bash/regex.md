# Regex Expressions

Commonly used regex expressions

## Digits & Numbers

Positive integers (Whole numbers only):

```bash
^[0-9]+$
```

- Use case: Validating that a user input or variable contains only numbers.

Decimals/Floats:

```bash
^[0-9]+(\.[0-9]+)?$
```

- Use case: Checking for numbers that may include a decimal point.

## Networking & System Admin

IPv4 Addresses:

```bash
^([0-9]{1,3}\.){3}[0-9]{1,3}$
```

- Use case: Basic validation for IP address strings.

MAC Addresses:

```bash
^([0-9A-Fa-f]{2}[:-]{5}([0-9A-Fa-f]{2})$
```

- Use case: Matching hardware MAC addresses formatted with colons or hyphens.

