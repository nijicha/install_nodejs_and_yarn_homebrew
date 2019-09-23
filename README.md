# Install NVM, NodeJS, Yarn via Homebrew

## Prerequisites
- [Homebrew](https://brew.sh/) should be installed (Command line tools for Xcode are included).

## Getting start

### Part A: Install NVM and NodeJS

1. Install `nvm` via Homebrew
    
    $ `brew install nvm`
    
2. Create system directory for nvm
    
    $ `mkdir ~/.nvm`
    
3. Add following line to your profile. (`.profile` or `.zshrc` or `.zprofile`)

    ```bash
      # NVM
      export NVM_DIR=~/.nvm
      source $(brew --prefix nvm)/nvm.sh
    ```
    
4. Close and open your terminal again.
  Or Choose one from the following command once for reload your profile. (`.profile` or `.zshrc` or `.zprofile`)
  
    Example
      - $ `source ~/.profile`
      - $ `source ~/.zshrc`
      - $ `source ~/.zprofile`
      
5. Verify `nvm` is installed

    $ `nvm --version`
    
6. Check all avaliable version by this command

    $ `nvm ls-remote`
    
7. Install NodeJS (_Recommended to install LTS version. Current LTS is Dubnium_)
    
    $ `nvm install --lts='Dubnium'`
    
8. Check installed NodeJS in your machine.

    $ `nvm ls`
    
9. Set global nodejs version to environment.
    
    $ `nvm use default`
    
See more about `nvm` : https://github.com/creationix/nvm

### Part B: Install Yarn

1. Install `yarn` via Homebrew and remove `node` dependencies from Homebrew
    
    $ `brew install yarn`

    $ `brew uninstall node --ignore-dependencies`
    
2. Checkout `node` in environment `$PATH` 

    $ `which node`
    
    It should be return => `/User/<your's-user-name>/.nvm/versions/node/<latest-node-lts-version>/bin/node`
    
3. Checkout `brew doctor` there should show message **WARNING missing yarn dependencies**
    
    $ `brew doctor`
    
4. Create symbol link from `nvm` for Homebrew. Pick a choice which suitable for you.

    a. This is for those who installed only one version via nvm

    $ `ln -s ~/.nvm/versions/node/ /usr/local/Cellar/`
    
    b. If you installed multiple node versions via `nvm`. You should create symbol link by current global version. Following this commands
    
    $ `nvm current` => v10.16.0 (Latest LTS: Dubnium) (This should be **Global** node version)
    
    $ `mkdir /usr/local/Cellar/node`
    
    $ `ln -s ~/.nvm/versions/node/<latest-node-lts-version>/ /usr/local/Cellar/node`
    
4. Checkout `brew doctor` again. There shouldn't have **WARNING** message.

    $ `brew doctor`
