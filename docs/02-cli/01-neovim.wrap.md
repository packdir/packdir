
ChatGPT:

Astronvim does not have a specific setting for line wrapping. It is influenced by the configuration of Neovim. 

To wrap long lines in Neovim, you can run the following command:

```vim
:set wrap
```

If you want to make this change permanent, add the above line to your Neovim configuration file (`init.vim`) which is usually located at `~/.config/nvim/`.

If you don't have any line number or line indicator to the left of your screen, you might also want to try:

```vim
:set linebreak
```

This command prevents the line from breaking in the middle of a word. It wraps the line at a space or a tab character instead. Add it in `init.vim` to make the change permanent. 

Please note that these are general Neovim configurations and should also work in astronvim. However, depending on your specific configuration and if you're using other plugins, these settings might behave differently.


