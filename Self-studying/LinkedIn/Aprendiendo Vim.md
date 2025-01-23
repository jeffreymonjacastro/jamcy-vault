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
#normal_mode
`:w` =  if the file doesn't exist, vim will create it
`:w <file_name.txt>` = will create a file with that name

# Edit a new file
#normal_mode
`:e <file_name>` = will open the file
+ Use tab to navigate between all the files

# What file do I am editing?
#normal_mode
`Ctrl + g` = Will indicate the name of the file you are editing 

# Motion Keys
#normal_mode
`h` = Left
`j` = Dow 
`k` = Up 
`l` = Right

> It can be combined with a numer before the key, which indicates how many positions you want to move
> 
> For example:
> `5l` = 5 characters to the right 

# Words, Sentences, Paragraphs
#normal_mode
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
#normal_mode 
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
#normal_mode 
`G` = Go to the end of the file
`gg` = Go to the beginning of the file
`Ctrl + F` = Move a page forward and mantain the cursor position
`Ctrl + B` = Move a page backward and mantain the cursor position

> You can also add numbers to move a specific amount of positions
> 
> For example:
> `2 Ctrl + F` = Move 2 pages forward

# Lines
#normal_mode 
`:<number_of_line> + Enter` = Move to a specific line mantaining cursor position
`<number_of_line>G` = Move to a specific line mantaining cursor position
`$` = Move to the end of the line
`0` = Move to the beginning of the line
`vim <filename> +<number_of_line>` = Open a file in a specific line

# Search actual word
#normal_mode 
`*` = Search for the next actual word
`#` = Search for the previous actual word

> You can still using this motions:
`n` = Move to the next occurence
`N` = Move to the previous occurence

# Deleting
#normal_mode 
The key `d` is used to delete, but it functions with a combination of keys.

`dw` (Delete Word) = Deletes the characters from the cursor to the end of the actual word
`d)` = Deletes the words from the cursor to the end of the actual sentence.
`dd` = Deletes the hole line 
`d/<RegEx> + Enter` = Deletes from the cursor to the first occurence of the RegEx

> `u` (Undo) = Undo as `Ctrl + Z`
# Copy & Paste
#normal_mode 
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
We can save specific text into vim registers. Vim has 52 registers in total (lower and upper case alphabet)

