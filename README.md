# Install NodeJS, Yarn via Homebrew (managed by asdf-vm)

## Notice
> Thank you everyone. For became a stargazers.
>
> I had created this guideline for personal note purpose (first on [Gist](https://gist.github.com/nijicha/e5615548181676873118df79953cb709) and then this repository)
>
> Pull request is available. Please help me contribute this one 😂.

## Prerequisites
- [Homebrew](https://brew.sh/) should be installed (Command line tools for Xcode are included).

## Getting started

### Part A: Install asdf-vm (A parts from official [website](https://asdf-vm.com/guide/getting-started.html#_1-install-dependencies))

1. Install `asdf` via Homebrew. Current `asdf-vm` version is `0.10.0`
   ```shell
   brew install asdf
   
   brew install gpg gawk # These are `asdf-nodejs` plugin dependencies
   ``` 

2. Add following line to your profile. (`.profile` or `.zshrc` or `.zprofile`)

    ```shell
    # asdf
    [ -s "/$(brew --prefix asdf)/libexec/asdf.sh" ] && . $(brew --prefix asdf)/libexec/asdf.sh
    ```
    
3. Close and open your terminal again.
  Or Choose one from the following command once for reload your profile. (`.profile` or `.zshrc` or `.zprofile`)
  
    Example
      - `source ~/.profile`
      - `source ~/.zshrc`
      - `source ~/.zprofile`
      
4. Verify `asdf` is installed

    `asdf version`
    
5. Install asdf plugins

    ```shell
    asdf plugin add nodejs
    asdf plugin add yarn
    ```

6. Verify `asdf` and `plugins` are ready!

    ```shell
    ❯ asdf list

    nodejs
    No versions installed
    yarn
    No versions installed
    ```

### Part B: Install nodejs and yarn

> **NOTE**
>
> If you are matched to these condition below. [You must install NodeJS v16+ (LTS Gallium)](https://doesitarm.com/app/nodejs/)
>
> - Using Apple Silicon machine ✅
> - Installed `homebrew` on Native build (homebrew PATH: `/opt/homebrew`) ✅
>
> Alternatively, If your had configured your **SHELL** to support Homebrew native & Homebrew rosetta2 (e.g. script below like I did)
> You can install `v15` or lower via Homebrew rosetta2. But I prefer to use v16+ (LTS Gallium)

    ```bash
    # My .zprofile

    # Apple M1
    if [ "$(uname -m)" = "arm64" ]; then
      # Use arm64 brew, with fallback to x86 brew
      if [ -f /opt/homebrew/bin/brew ]; then
        export PATH="/usr/local/bin${PATH+:$PATH}";
        eval $(/opt/homebrew/bin/brew shellenv)
      fi
    else
      # Use x86 brew, with fallback to arm64 brew
      if [ -f /usr/local/bin/brew ]; then
        export PATH="/opt/homebrew/bin${PATH+:$PATH}";
        eval $(/usr/local/bin/brew shellenv)
      fi
    fi
    ```

1. Install `nodejs` and `yarn`

   Current LTS nodejs version is `16.14.x`, Codename: `Gallium`

    ```shell
    asdf install nodejs lts
    asdf install yarn latest
    ```

2. Set `nodejs` and `yarn` globally for your machine

    ```shell
    asdf global nodejs lts
    asdf global yarn latest
    ```

3. Verify they are installed

    ```shell
    ❯ node -v
    v16.14.2

    ❯ npm -v
    8.5.0

    ❯ npx -v
    8.5.0

    ❯ yarn -v
    1.22.18

    ❯ asdf list
    nodejs
    16.14.2
    lts
    yarn
    1.22.18

    ❯ asdf current
    nodejs          lts             /Users/nijicha/.tool-versions
    yarn            1.22.18         /Users/nijicha/.tool-versions
    ```

4. Enjoy! 🥳 ❤️

## Read more
- https://asdf-vm.com
- https://github.com/asdf-vm/asdf-nodejs
- https://github.com/twuni/asdf-yarn
