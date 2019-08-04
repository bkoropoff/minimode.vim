# VIM minimodes

Inspired by hydra for Emacs, this allows creating transient "modes" with their
own key mappings.  When an unmapped key is pressed, the minimode is terminated
and the key performs its usual action.  While active, a help message showing
the mappings is displayed in the cmdline area.  Example:

```vim

" Cycle buffers with n/N
let buffermode = minimode#compile({
            \    'name': 'buffer cycle',
            \    'actions': {
            \        'n': 'normal! bn',
            \        'N': 'normal! bp'
            \})

" <Leader>bn and <Leader>bN enter minimode and execute n or N mapping
" respectively.  Further cycling can be done with just n or N.

nnoremap <silent> <Leader>bn :call minimode#run(buffermode)<cr>n
nnoremap <silent> <Leader>bN :call minimode#run(buffermode)<cr>N
```
