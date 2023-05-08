`~/.gitconfig` 

[user]
name = Albert Chang
email = a89529294@hotmail.com
[core]
editor = code --wait
ignorecase = false
[init]
defaultBranch = main
[alias]
co = checkout
s = status
c = commit
sw = switch
b = branch
a = add
p = push
grepi = grep -i -n
lg = lg1
lg1 = lg1-specific --all
lg2 = lg2-specific --all
lg3 = lg3-specific --all

lg1-specific = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(auto)%d%C(reset)'

lg2-specific = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(auto)%d%C(reset)%n'' %C(white)%s%C(reset) %C(dim white)- %an%C(reset)'

lg3-specific = log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset) %C(bold cyan)(committed: %cD)%C(reset) %C(auto)%d%C(reset)%n'' %C(white)%s%C(reset)%n'' %C(dim white)- %an <%ae> %C(reset) %C(dim white)(committer: %cn <%ce>)%C(reset)'

aliases = config --get-regexp alias

[push]
default = simple