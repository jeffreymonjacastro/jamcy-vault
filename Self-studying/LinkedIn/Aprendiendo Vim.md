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