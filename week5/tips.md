
### install emacs
yum install emacs
C-x C-x: quit
C-x C-f: open or create

### why-can-rm-remove-read-only-files
All rm needs is write+execute permission on the parent directory. The permissions of the file itself are irrelevant.

### cd directory need x permission to directory
### create a file need w permission to directory
### chmod only granted to file's owner or root

### 8.8.8.8 google public dns
### 114.114.114.114 114dns

### vim delete blank lines
:g/^$/d            :g/^$/ match the black line using regex, d delete

### vim redo
`u`: undo
`ctrl+r`: redo
`earlier 9999d`: undo to the start
`later 9999d`: redo to the latest