# Exit vim: `:qa!`
`:` = Prefix for entering command-line mode
`q` = Shortcut for quit command
`a` = All buffers
`!` = Force (even if there are files with not save changes)

# Vim Modes
Vim provides two main modes:
+ **Insert mode:** for writing text
+ **Normal mode:** for manipulating text
	+ Each key has a meaning related to text manipulation

# Insert mode
- It's only for writing text, no more
- Switch to insert mode: `i`
- Exit insert mode: `Esc` or `Ctrl + C`

# Save files
`:w` =  if the file doesn't exist, vim will create it
`:w <file_name.txt>` = will create a file with that name

# Edit a new file
`:e <file_name>` = will open the file
+ Use tab to navigate between all the files

# What file do I am editing?
`Ctrl + g` = Will indicate the name of the file you are editing 

# Motion Keys
`h` = Left
`j` = Dow 
`k` = Up 
`l` = Right

> It can be combined with a numer before the key, which indicates how many positions you want to move
> 
> For example:
> `5l` = 5 characters to the right 

# Words, Sentences, Paragraphs
## Words
`w` (Word) = Move to the beginning of the next word 
`e` (End) = Move to the end of the next word 
`b` (Back) = Move to the beguinning of the previous word (b for back)
`ge` = Move to the end of the previous word
## Sentences
A sentence is a sequence of words that end with a dot, exclamation or question mark followed by either the end of a line or a space or a tab. 
U can move using braces.

`)` = Move to the beginning of the next sentence
`(` = Move to the beginning of the previous sentence
## Paragraphs
A paragraph begins after an empty line and ends with an empty line
U can move using curly braces.

`}` = Move to the top empty line of the next paragraph 
`{` = Move to the top empty line of the previous paragrah 


>  It can also be combined with a numer before the key, which indicates how many positions you want to move
> 
> For example:
> `5w` = 5 words next 
> `3)` = 3 sentences next
> `2{` = 2 paragraphs previous

# Search with Regular Expressions
RegEx is a way to match text using more than words.

## Searching forward
`/<RegEx>` = For searching forward a specific kind of words that match the RegEx beginning on the position of the cursor

>**Examples:**
`/tra` = Search forward words that has "tra" in them (atTRActed)
`/ch.mb` = Search forward words that has "ch" + any character + "mb" (chamber) 

Press `enter` to search for first occurence
 `n` = Move to the next occurence
 `N` = Move to the previous occurence

## Searching backwards
`?<RegEx>` = For searching backwards a specific kind of words that match the RegEx beginning on the position of the cursor

Press `enter` to search for first occurence
 `n` = Move to the previous occurence
 `N` = Move to the next occurence

# Move around screen
`G` = Go to the end of the file
`gg` = Go to the beginning of the file
`Ctrl + F` = Move a page forward and mantain the cursor position
`Ctrl + B` = Move a page backward and mantain the cursor position

> You can also add numbers to move a specific amount of positions
> 
> For example:
> `2 Ctrl + F` = Move 2 pages forward

# Lines
`:<number_of_line> + Enter` = Move to a specific line mantaining cursor position
`<number_of_line>G` = Move to a specific line mantaining cursor position
`$` = Move to the end of the line
`0` = Move to the beginning of the line
`vim <filename> +<number_of_line>` = Open a file in a specific line

# Search actual word
`*` = Search for the next actual word
`#` = Search for the previous actual word

> You can still using this motions:
`n` = Move to the next occurence
`N` = Move to the previous occurence

# Deleting
The key `d` is used to delete, but it functions with a combination of keys.

`dw` (Delete Word) = Deletes the characters from the cursor to the end of the actual word
`d)` = Deletes the words from the cursor to the end of the actual sentence.
`dd` = Deletes the hole line 
`d/<RegEx> + Enter` = Deletes from the cursor to the first occurence of the RegEx

> `u` (Undo) = Undo as `Ctrl + Z`
# Copy & Paste
The copy key is `y` which stands for yank. `Ctrl + C` memories.

`yw` (Yank Word) = Copy from the cursor to the end of the actual word
`p` (Paste) = Paste as `Ctrl + V` right after the cursor is.
`P` = Paste right before the cursor is
`yy` = Copy the hole line

`x` = Delete the character under the cursor
`o` = Enters to insert mode creating a new line down
`O` = Enters to insert mode creating a new line up

# Change text
`cw` = Deletes from the cursor to the end of the word and switch to insert mode
`c)` = Deletes from the cursor to the end of the sentence and switch to insert mode
`c}` = Deletes from the cursor to the end of the paragraph and switch to insert mode
`c/<RegEx>` = Deletes from the cursor to the first occurence and switch to insert mode

# Visual mode
`v` = Normal visual mode
`Shift + v` = Line visual mode
`Ctrl + v` = Block visual mode

# Registers
- We can save specific text into vim registers.
- Registers are named storage areas in Vim. Some common types include:

| Register | Usage                                                                                         |
| -------- | --------------------------------------------------------------------------------------------- |
| `"`      | The unnamed register (default for most operations).                                           |
| `0`      | Stores the last text yanked (copied).                                                         |
| `1`-`9`  | Numbered registers: store deleted or changed text in a stack-like manner (`1` is the latest). |
| `a-z`    | Named registers: manually store and retrieve text.                                            |
| `+`      | System clipboard: for interaction with the OS clipboard.                                      |
| `%`      | Current file name.                                                                            |
| `/`      | Last search pattern.                                                                          |

`"ayy` = Copy whole line to register a
`"ap` = Paste the content in register a

# Replace text
`:s/you/they` = Replaces the first occurence of "you" with "they"
`:s/you/they/g` = Replaces all the occurences of "you" with "they"
`:s/you/they/gc` = Replaces all the occurences of "you" with "they" only if you confirm the change of each occurence

# Marks
- The key for creating marks is m (mark)
- You can create marks with all lower and upper case letters
	- Lowercase marks are stored in buffer
	- Uppercase marks are across (inaudible)

`ma` = Creates a mark in variable "a"
`'a` = Go to the mark "a"
`:marks` = View all marks

## Special Mark
`'.` = Go to the previous line modified

### **1. Marks Locales (Alcance dentro del archivo actual)**

| **Mark** | **Descripción**                                                                                                   |
| -------- | ----------------------------------------------------------------------------------------------------------------- |
| `a-z`    | Marks locales definidos por el usuario. Puedes establecerlos con `m<mark>` y saltar con `' <mark>` o `` `<mark>`. |
| `'`      | Última posición antes de un salto en el archivo. (`''` salta a esa posición).                                     |
| `.`      | Última posición donde se realizó un cambio.                                                                       |
| `^`      | Posición del cursor antes de entrar al modo de inserción.                                                         |
| `"`      | Última posición donde se dejó el cursor al salir de Vim.                                                          |
### **2. Marks Globales (Alcance entre archivos)**

| **Mark** | **Descripción**                                                                    |
| -------- | ---------------------------------------------------------------------------------- |
| `A-Z`    | Marks globales definidos por el usuario. Funcionan entre archivos abiertos en Vim. |
| `0-9`    | Posiciones en los archivos editados recientemente.                                 |
### **3. Marks Especiales**

| **Mark** | **Descripción**                                         |
| -------- | ------------------------------------------------------- |
| `[`      | Inicio del área más reciente seleccionada o modificada. |
| `]`      | Final del área más reciente seleccionada o modificada.  |
| `<`      | Inicio de la última selección visual.                   |
| `>`      | Final de la última selección visual.                    |
| `{`      | Inicio del bloque más reciente modificado.              |
| `}`      | Final del bloque más reciente modificado.               |
### **4. Uso de los Marks**

| **Comando**       | **Descripción**                                                             |
| ----------------- | --------------------------------------------------------------------------- |
| `m<mark>`         | Establece un mark en la posición actual del cursor.                         |
| `' <mark>`        | Salta a la línea del mark.                                                  |
| `` `<mark>`       | Salta a la posición exacta del mark (línea y columna).                      |
| `:marks`          | Lista todos los marks y sus posiciones.                                     |
| `delmarks <mark>` | Elimina un mark específico (por ejemplo, `delmarks a` elimina el mark `a`). |
| `delmarks!`       | Elimina todos los marks definidos por el usuario.                           |

# Jump through history
All the vim motions are storage in a jump history

`Ctrl + o` = Go to the previous jump
`Ctrl + i` = Go to the next jump
`:jumps` = View jumps historial

# Windows and buffers
+ A buffer is the content of the file being edited
+ It can be a new file, or a file that's already exists on a disk
+ All changes you do to buffer will only be written to disk if you save the buffer
+ A window is a view to a buffer
+ You can have several windows pointing to the same buffer in different places

`:split` = Opens a new window to the same buffer
`Ctrl + w + w` = Go to the next window
`Ctrl + w + c` = Close the current window
`:new <filename>` = Open a new file into a split window

- When you start vim with no filename it will open a window into a empty buffer

`:bd` (Buffer Delete) = Removes the current buffer  
`:e .` = Show a list of files from the current directory
+ You can search for filenames with `/`
+ Click `Enter` to start editing the file
`:ls` = View the list of buffers
`:bn` = Move to the next buffer
`:bp` = Move to the previous buffer
`:b <filename>|<number>`  = Move to specific buffer

# Read command
`:r <filename>` = Paste all the content of a file in the position of the cursor

# Configuration
My config file of nvim is in `C:\Users\jeffr\AppData\Local\nvim\init.lua`

`:set number` = Show numbers to the left
`:set nonu` = Hide numbers to the left
`:noremap <new_key> <previous_key>` = Add a key to behave as the previous key

# Abbreviations
`:abb <Abbreviation> <text>` = Will create an abbreviation instead of writing the text

> Example
> `:abb _j Jeffrey :D` = When writing \_j and space, it will appear the text

+ Use `Ctrl + v` to don't expand  the abbreviation
+ Better to use words that doesn't exist for abbreviations, as underscores at the beginning

# Add commands
`:! <command>` = To execute an external command 
+ Press `Enter` to go back to vim

`:com! <command_name> ! <command>` = Creates a new vim command that executes something
> Example
> `:com! Py ! python %` = Executes the current python file

+ The commands can be added to .vimrc config file.
+ You can do much more with commands. Write functions, accept arguments and more. With accommodation it is excellent.

# Various settings
`:help option-summary` = Summary of options that are available
`:close` = Close the window without exit vim
`:set` = View the current set option
`:set ignorecase` = Avoid case sensitive while searching
`:set hls` = Highligh occurences while searching
`:noh` = TUrn highlighting off
`:set incsearch` = Incremental search
`:set clopboard=unnamedplus` = Syncronize system clipboard
`:syntax on` = Syntax colors for programming languages
`:colorscheme delek` = Change syntax color to delek

+ You can save all this settings in vim config file

# Start vim with a command
To add commands when starting vim, is used `+`

`$ nvim <filename> +<number>` = Open the file in specific line
`$ nvim <filename> +/<RegEx>` = Open the file in the first occurence to RegEx pattern

>Example
>`$ nvim > +1d +wq ./conway.txt` = Deletes first line and saves the file

# Diff mode
Used to compare changes between different versions of the files

`$ nvim -d <filename1> <filename2>` = Opens the build-in-diff mode
`do` (Diff Obtain) = Select the change of the other file
`dp` (Diff Put) = Select the change of the current file

`:vert diffsplit <filename>` = Other way to enter to diff mode vertically in a current file with the filename 
`:se dip+=vertical` = Open vertical split automatically

# Zip files
`$ nvim <zip_file>` = Instead of unzip you can edit the files directly on vim

# Open files from name
`gf` (go to file) = Open the file with the name the cursor is in
`gF` = Open the file in the exact line number

+ Pressing `gf` into a url will fetch the content and show the html

# External commands
`:!date` = Shows current date
`:r !dir` = Paste all files in directory
`:%! jq .` = Runs jq to a json file to pretty view 

# Help system
`:help user`
`:Tutor`
[Vim adventures](https://vim-adventures.com)
[A Byte of Vim](https:((vim.swaroopch.com)
[VimGolf](http://www.vimgolf.com)


