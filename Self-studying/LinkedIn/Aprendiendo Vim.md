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
> `5l` = 5 letters to the right 

# Words, Sentences, Paragraphs
#normal_mode
## Words
`w` = Move to the beginning of the next word (w for word)
`e` = Move to the end of the next word (e for end)
`b` = Move to the beguinning of the previous word (b for back)
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

# Regular Expressions
RegEx is a way to match text using more than words.

For searching a specific kind of words that match the RegEx, you can use slash `/`