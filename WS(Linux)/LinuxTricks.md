# Linux tricks that I keep forgetting

### Checking file size
`du` - Used to check file size  
Can give 
-h for human readable format,  
-s for excluding subdirectories,  
--max-depth=<int> to specify how deep to look.  
-c to give a total of all indivisual folders shown.
Example:  
``sudo du -h --max-depth=1 /var`  
or,  
`sudo du -shc /var/*`  

