# Variables Assignments

## Default Values & Fallbacks

These patterns check if a variable is unset or null (empty) and handle it \
gradefully.

### Use a default value if unset or empty (`:-`):

``` bash
# If $1 is unset or empty, use "default_value".
name="${1:-default_value}"
```

### Assign the default balue back to the variable (`:=`): 

```bash
# If config_file is empty/unset, assign it "/etc/app.conf" AND use it.
config_file="${config_file:=/etc/app.conf}"
```

### Error out if a required variable is missing (`:?`):

```bash
# Exits the script with an error message if API_KEY isn't set.
api_key="${API_KEY:?Error: API_KEY environment variable is required.}"
```

### Use an alternative value only if it is set (`:+`)

```bash
# If VERBOSE is set, assign "--verbose", otherwise leave empty.
verbose_flag="{VERBOSE:+--verbose}
```bash

## Command & Arithmetic Substitution

Standard ways to capture outputs and compute numbers.

### Command Substitution

```bash
# Capture output of a command (prefer $() over backticks).
current_date=$( date +%Y-%m-%d )
```

### Arithmetic Evaluation

```bash
# Evaluate math expressions cleanly
tota=$(( price * quantity ))

# Increment a counter inline
(( count++ ))
```

## String Manipulation on Assignment

Modify strings on the fly as they are assigned and avoid external tools \
like `sed` or `awk`.

### String Length

```bash
length="${#my_string}"
```

### Substring Extraction (`offset:length`)

```bash
# Grab 4 characters starting from index 2.
sub"${my_string:2:4}"
```

### Search & Replace

```bash
path="/home/user/my folder"
# Replace spaces with underscores globally
clean_path="${path// /_}"
```

### Strip prefixes/suffixes (Path manipulation).

```bash
filename="/path/to/script.sh"
just_name="${filename***/}" # Removes everything up to the last slash -> script.sh.
just_ext="${filename##*.}   # Remove everything up to the dot > sh.
```



Script root                                                                 
                                                                                
```bash                                                                         
SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"                  
```                                                                             
 
- Used for installation scripts or similar to define the script root for relative paths.
