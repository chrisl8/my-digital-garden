---
{"created":"2024-12-13","time":"Friday, December 13th, 2024 @ 12:42:57pm","tags":["Linux"],"authors":["ChrisL8"],"dg-publish":true,"permalink":"/knowledge-base/last-character-of-pasted-text-uppercase/","dgPassFrontmatter":true}
---

*Note that I use `set -o vi` in my `.zshrc` file, which is apparently unusual, and probably part of the source of why this is hard for me to fix.*

When pasting into a PowerShell based terminal that is SSHed into an Oh My ZSH powered zsh Linux prompt, the last character of the pasted text is often converted to uppercase.

It is not consistent.

It most commonly happens if the previous line is empty, so do a couple of `Enter`'s before pasting to reproduce it.

 - This does **NOT** happen in `bash`
# Things that do NOT help
## unset zle_bracketed_paste
https://unix.stackexchange.com/questions/281316/pasting-text-in-zsh-in-vi-mode
Does not help, either on the command line or in `.zshrc`.

## Removing `safe-paste` plugin
https://unix.stackexchange.com/a/281371/517914
I literally use NO plugins for OhMyZsh!
https://askubuntu.com/questions/1310448/how-to-know-what-plugins-are-installed-in-my-oh-my-zsh
`plugins=()`
`echo $plugins`

## `printf '\e[?2004l'`
https://jdhao.github.io/2021/02/01/bracketed_paste_mode/
Paste this right into the terminal.

I swear it worked once, but now it doesn't, so no progress here either.

## `bindkey -e`
https://stackoverflow.com/a/78811755/4982408
This changes the paste from sometimes ending uppercase to sometimes ending in a `~` which is both easier to see and less annoying to fix. It also proves the problem.

Adding that to the end of `.zshrc` accomplishes the task permanently.

**However**, this also defeats using `vim` on the command line almost entirely, so it isn't a workable solution.
# Progress

None really, other than if I press `u` it will flip the case of the last pasted character, so I just get used to doing that.

