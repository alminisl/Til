# Installing ZSH + Oh My Zsh on WSL

## Installing ZSH and Oh My ZSH

First step is to install zsh: 

    `sudo apt-get install zsh`

Second step is installin oh-my-zsh with: 

    `sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`


## Configuring zsh/oh-my-zsh

If ZSH is not the default shell, when you re-open the terminal add this snippet to the `~/.bashrc` to make `zsh` the default shell:

```bash
if test -t 1; then
    exec zsh
fi
```

Next up, configure the theme or specific settings in the `~/.zshrc`. For example I like to use the `agnoster` theme:

```
#Find this 
ZSH_THEME="robbyrussell"

# change into this
ZSH_THEME="agnoster"
```

More themes can be found here [zsh themes](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes) 

## Make sure npm/nvm/yarn works

Copy the `NVM_DIR` from `.bashrc` and add it to the `.zshrc` (or just copy paste the below code into the `.zshrc`) 

```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

export PATH="$HOME/.yarn/bin:$HOME/.config/yarn/global/node_modules/.bin:$PATH"
```

## Note: If this is the first time installing zsh

You probably do not have installed a powerline font. That means the you will get artifacts instead of the shiny lignatures which ZSH supports. To fix this do the following: 

`git clone https://github.com/powerline/fonts.git` 

Open an admin PowerShell, navigate to the root of the repo and run this:
`.\install.ps1`

Or Alternatively you can use `"Cascadia Code PL"` which you can easily install following the instructions on [Cascadia code](https://github.com/microsoft/cascadia-code)

In the end you have a nice and shiny Terminal: 

![](https://i.imgur.com/cpzinJh.png)
