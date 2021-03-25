### To save and run a C file with openmp tag from nvim 

" Keybind to run compile and run current file
nnoremap <F9> :w <CR> :!gcc "%:p" -o out -fopenmp && ./out <Enter>


