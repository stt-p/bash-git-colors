# Bash colored branch output

1. Update your ~/.bashrc file with
```
source ~/.bashrc_user
```
2. Put the `.bashrc` file from repo in your home folder `~/`

P.S. th content of the `.bashrc_user` is the following
```bash
# Start Git color
parse_git_branch() {
 git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
if [ "$color_prompt" = no ]; then
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w$(parse_git_branch)\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[01;31m\]$(parse_git_branch)\[\033[00m\]\$ '
fi
# End Git color
```
