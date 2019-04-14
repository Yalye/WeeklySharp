
### Vim Tip
### comment
select lines, then `:norm i#` to comment  
select lines, then `:norm x` to uncomment  
uncomment: `ctrl + v` to enter VISUAL BLOCK mode, then go down to select all lines's `#`, press `x`  
comment: `ctrl + v` to enter VISUAL BLOCK mode, then go down to select all lines's start, `Shift i`, enter the INSERT mode, then press `#`. then `Esc`

### indent
use `>>` to indent, use `<<` to unindent  
`shift + >` to indent selection              
`shift + <` to unindent selection   
`>%` or `<%`: indent a curly-braces block (including the brace)  
`>iB` or `<iB`: indent a curly-braces block(within the block)  

### selection
gv select last selection  
:set paste        enable paste   
:set nopaste  