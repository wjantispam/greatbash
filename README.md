# greatbash
Probably most of these will work in the other shells, such as sh and zsh, but I have only test this in Bash.

Making most of Bash by learning some key ideas

## Edit long commands
The `man bash` page says:

    edit-and-execute-command (C-xC-e)
        Invoke  an  editor  on the current command line, and execute the
        result as shell commands. Bash attempts to invoke $VISUAL,
        $EDITOR, and emacs as the editor, in that order.
There are some warnings in *[here](https://unix.stackexchange.com/questions/85391/where-is-the-bash-feature-to-open-a-command-in-editor-documented)* says *Be very careful with this feature. If you cancel the edit, the original command line will be immediately executed. So if you are editing rm -rf / and invoke the editor and realize you are into something dangerous and thus cancel the edit, your rootfs will be deleted without further questions asked*, then it went one says *@marlar if your editor is vim, you can use `:cq`, it makes it exit with non-zero code, and prevents the command from execution*