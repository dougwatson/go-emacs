Macs come with a version of emacs that is way too old (v22) and it won't work with the latest golang exiting modes.

You need to upgrade emacs before trying to get your go editor up and running.

brew cleanup
brew doctor
brew update
brew upgrade
brew install emacs

