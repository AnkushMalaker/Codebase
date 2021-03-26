### To save and run a C file with openmp tag from nvim 

" Keybind to run compile and run current file
nnoremap <F9> :w <CR> :!gcc "%:p" -o out -fopenmp && ./out <Enter>

Rename current variable
One common task is rename the variable name under cursor.

Use command ``:CocCommand document.renameCurrentWord`` to start cursors session with ranges contain current word.

Note: the word ranges are extracted from language server when possible, when language server not available, strict match of words in current buffer is used.



## Powerful substitutoin commands: 
For replacing a variable in the whole file:  
```:%s/```
then hit ^R^W or ^R^R to get the word under the cursor, then finish the replacement with
```
:%s/wordunderthecursor/&text to append/g
:%s/wordunderthecursor/text to prepend&/g
:%s/wordunderthecursor/text before & after/g
:%s/wordunderthecursor/text to replace/g
:%s/wordunderthecursor//g " delete the match
```  
Alternatively, you can use * or # to search for the word under the cursor (populating the search register), then use  

```:%s//replacement/g```  
(leaving the pattern blank to use the pre-populated search register)
Taken from (this)[https://www.reddit.com/r/vim/comments/cod91w/vim_feature_similar_to_ctrld_in_vscode/ewijq8o?utm_source=share&utm_medium=web2x&context=3] comment.  

Also apparently a lot of helpful stuff in  
```help: sub-replace-special```  

