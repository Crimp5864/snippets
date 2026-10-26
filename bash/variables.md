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



Script root                                                                 
                                                                                
```bash                                                                         
SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"                  
```                                                                             
 
- Used for installation scripts or similar to define the script root for relative paths.
