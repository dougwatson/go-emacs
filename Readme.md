Macs come with a version of emacs that is way too old (v22) and it won't work with the latest golang exiting modes.
emacs -version
GNU Emacs 22.1.1


You need to upgrade emacs before trying to get your go editor up and running.

brew cleanup
brew doctor
brew update
brew upgrade
brew install emacs

now link the emacs executable so it will be in your /usr/local/bin directory
ln -s /usr/local/Cellar/emacs/26.1_1/bin/emacs-26.1 /usr/local/bin/emacs

Now edit your ~/.profile to put /usr/local/bin in the start of your path
export PATH=/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/go/bin

now check the version:
emacs -version
GNU Emacs 26.1


Put this into ~/.emacs.d/.emacs and save it (From melpa instructions - http://ergoemacs.org/emacs/emacs_package_system.html):
```
;; load emacs 24's package system. Add MELPA repository.
(when (>= emacs-major-version 24)
  (require 'package)
  (add-to-list
   'package-archives
    '("melpa" . "https://stable.melpa.org/packages/") ; many packages won't show if using stable
   t))
```
Now when you start emacs you will have access to melpa via M-x install-package.
Run M-x package-list-packages
Then you might need to wait before go-mode will show up (search for it with ctrl-s)

Get the development tools like godoc:
go get -u golang.org/x/tools/cmd/...
