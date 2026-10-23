# Bash colors

Colors require either `\e` or `\033`, the former being the more bash specific option. <br>
Code structure is: `\e[<STYLE>;<COLOR>m<Text here>\e[0m` <br>
Escape prefix: `\e[` <br>
Separator: `;` (used to combine style + color) <br>
Terminator: `m` <br>
Reset Code: `\e[0m` (always include this at the end so colors don't bleed!)

## ANSI codes
#### Text Styles
| Code | Style | Description |
| --- | --- | --- |
| 0 | Reset/Normal | Restores default terminal colors and formatting |
| 1 | Bold/Bright | Increases line weight / brightens text |
| 2 | Dim/Faint | Reduces intensity / opacity of text |
| 3 | Italic | Slanted text (support varies by terminal emulator) |
| 4 | Underline | Adds a single underline |
| 5 | Blink (Slow) | Flashes text (generally discouraged) | 
| 7 | Reverse | Swaps foreground and background colors |
| 8 | Hidden/Conceal | Useful for passwords and hidden text |
| 9 | Strikethrough | Draws a line through text |

#### Foreground Colors
| Color | Standard | Bold/Bright |
| --- | --- | --- |
| Black | `\e[30m` | `\e[1;30m` or `\e[90m` |
| Red | `\e[31m` | `\e[1;31m` or `\e[91m` |
| Green | `\e[32m` | `\e[1;32m` or `\e[92m` |
| Yellow | `\e[33m` | `\e[1;33m` or `\e[93m` |
| Blue | `\e[34m` | `\e[1;34m` or `\e[94m` |
| Magenta | `\e[35m` | `\e[1;35m` or `\e[95m` |
| Cyan | `\e[36m` | `\e[1;36m` or `\e[96m` |
| White | `\e[37m` | `\e[1;37m` or `\e[97m` |
| Default | `\e[39m` |

#### Background Colors
| Color | Standard | High Intensity |
| --- | --- | --- |
| Black | `\e[40m` | `\e[100m` |
| Red | `\e[41m` | `\e[101m` |
| Green | `\e[42m` | `\e[102m` |
| Yellow | `\e[43m` | `\e[103m` |
| Blue | `\e[44m` | `\e[104m` |
| Magenta | `\e[45m` | `\e[105m` |
| Cyan | `\e[46m` | `\e[106m` |
| White | `\e[47m` | `\e[107m` |
| Default | `\e[49m` | |
