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

## Review files recursively
I had to get a snapshot of the files under a directory with their file datetime and sizes. I didn't know `tree` 

    $ find /path/to/folder -type f -print0 | xargs -0 ls -l --time-style="+%F %T"
    OR
    man tree
           -D     Print  the  date  of the last modification time or if -c is used, the last status change time for the file
              listed.

    $ tree -Dh --timefmt '%F %T' maintainable-bash/
    maintainable-bash/
    ├── [4.0K 2022-03-14 23:09:55]  0_pre-requisites
    │   ├── [4.0K 2022-03-14 23:09:55]  1_tooling
    │   │   └── [ 193 2022-03-14 23:09:55]  notes.txt
    │   ├── [4.0K 2022-03-14 23:09:55]  2_simplifications
    │   │   ├── [4.0K 2022-03-14 23:09:55]  1_multi-line-text
    │   │   │   └── [ 583 2022-03-14 23:09:55]  multi-line.sh
    │   │   ├── [ 269 2022-03-14 23:09:55]  notes.txt
    │   │   └── [1.5K 2022-03-14 23:09:55]  simplifications.sh
    │   ├── [4.0K 2022-03-14 23:09:55]  3_dry-principle
    │   │   ├── [ 159 2022-03-14 23:09:55]  bad.sh
    │   │   ├── [ 981 2022-03-14 23:09:55]  calling-functions.sh
    │   │   ├── [ 266 2022-03-14 23:09:55]  good.sh
    │   │   └── [ 405 2022-03-14 23:09:55]  notes.txt

## Get the first n char or bytes of a file
    $ head -c 100 file  # returns the first 100 bytes in the file
    $ tail -c 100 file  # returns the last 100 bytes in the file
    man head
           -c, --bytes=[-]NUM
              print the first NUM bytes of each file; with the leading '-', print all but the last  NUM  bytes  of  each
              file

    
