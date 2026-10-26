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




Script root                                                                 
                                                                                
```bash                                                                         
SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"                  
```                                                                             
 
- Used for installation scripts or similar to define the script root for relative paths.
