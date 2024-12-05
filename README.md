# This is a Clojure-friendly emacs config

If you're new to emacs, check out [this introductory tutorial](http://www.braveclojure.com/basic-emacs/)!

## Installing

1. Close Emacs.
2. Delete `~/.emacs` or `~/.emacs.d` if they exist. (Windows users, your
   emacs files will probably live in
   `C:\Users\your_user_name\AppData\Roaming\`. So, for example, you
   would delete `C:\Users\jason\AppData\Roaming\.emacs.d`.) This is
   where Emacs looks for configuration files, and deleting these files
   and directories will ensure that you start with a clean slate.
3. Clone this repository
   `git clone git@github.com:hkopp/emacs-for-clojure.git .emacs.d`

Then open Emacs.

## Upgrading

Before upgrading, ensure that your `.emacs.d` directory is under
version control so that you can always revert to a known good state.

To upgrade:

1. Edit `.emacs.d/init.el`, adding these lines after line 12:

   ```elisp
   (add-to-list 'package-archives
                '("melpa-stable" . "http://stable.melpa.org/packages/") t)
   
   (add-to-list 'package-pinned-packages '(cider . "melpa-stable") t)
   ```

2. Close Emacs.
3. Run `rm -Rf .emacs.d/elpa/cider-*`
4. Open Emacs. You'll probably see some errors and your theme won't
   load. That's ok.
5. In Emacs, run `M-x package-refresh-contents`.
6. In Emacs, run `M-x package-install cider`.
7. Close and re-open Emacs.

That should install the latest version. Enjoy!

## Organization

I've tried to separate everything logically and document the purpose
of every line. [`init.el`](./init.el) acts as a kind of table of
contents.

## Currently supported Languages in this config
- Clojure
- Python
- JS

## Common Errors
### Failed to verify signature archive-contents.sig
Fix with `gpg --homedir ~/emacs.d/elpa/gnupg --receive-keys <key-id>`
[ref](https://stackoverflow.com/questions/58202993/emacs-failed-to-verify-signature-archive-contents-sig)
