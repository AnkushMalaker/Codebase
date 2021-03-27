### Check keybinds

#### Default keybinds 

` :help index `

### To see commands that start with, say, g:  
`:help g`  

#### Other keybinds
` :verbose nmap / vmap / imap `

### File explorer
` :Sex / Vex / Ex / Tex `

S/V/T - horizontal/vertical/tab 
Note: Se/Ve/Te work too, but not nearly as funny

### Commenting and Uncommenting 

#### Uncomment

Visual block mode with `C-v`, select all lines, press x. Press . to repeat if comments start with // 

#### Comment 
Visual block mode with `C-v`, select all lines, press `shift-i`, type # or //.

### Check what has changed in file since last save
` :w !diff % - `

// diff checks the changes, % refers to current file, written to filename - using w
