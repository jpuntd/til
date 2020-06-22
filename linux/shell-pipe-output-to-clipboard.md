# Pipe output of a command or file to clipboard
Today I learned oh-my-zsh has two functions, clipcopy and clippaste, that can do this for multiple platforms.

## clipcopy - Copy data to clipboard
 
    <command> | clipcopy    - copies stdin to clipboard
    clipcopy <file>         - copies a file's contents to clipboard

## clippaste - "Paste" data from clipboard to stdout 
   
    clippaste              - writes clipboard's contents to stdout  
    clippaste | <command>  - pastes contents and pipes it to another process
    clippaste > <file>     - paste contents to a file