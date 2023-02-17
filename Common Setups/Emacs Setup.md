This is in case of "simple" Emacs setup where no requirement for an IDE like prelude exists.

## Backup Strategy

Paste the following into `~/.emacs.d/init.el`
```el
;; Put backup files neatly away                                                 
(let ((backup-dir "~/.emacs.d/backups")
      (auto-saves-dir "~/emacs.d/auto-saves/"))
  (dolist (dir (list backup-dir auto-saves-dir))
    (when (not (file-directory-p dir))
      (make-directory dir t)))
  (setq backup-directory-alist `(("." . ,backup-dir))
        auto-save-file-name-transforms `((".*" ,auto-saves-dir t))
        auto-save-list-file-prefix (concat auto-saves-dir ".saves-")
        tramp-backup-directory-alist `((".*" . ,backup-dir))
        tramp-auto-save-directory auto-saves-dir))

(setq backup-by-copying t    ; Don't delink hardlinks
      delete-old-versions t  ; Clean up the backups
      version-control t      ; Use version numbers on backups,
      kept-new-versions 5    ; keep some new versions
      kept-old-versions 2)   ; and some old ones, too
```
> Make sure to check the path(s) above

## Themeing

Check here for themes themselves: https://emacsthemes.com/
Here's a quick and dirty setup you can just add below the above config in `init.el`

```el
(require 'package)
(add-to-list 'package-archives
'("melpa" . "http://melpa.org/packages/") t)
(package-initialize)
(unless (package-installed-p 'use-package)
(package-refresh-contents)
(package-install 'use-package))
(use-package darcula-theme
:ensure t
:config
(set-frame-font "VictorMono-12")
(load-theme 'darcula t))
```

In the last 5 lines you see me setting a theme called [Darcula](https://emacsthemes.com/themes/darcula-theme.html)

I also set a font.

### Font list
To see a complete list of fonts, execute the following Lisp snippet by typing it into the *scratch* buffer and pressing C-x C-e at the end of the second line:

```el
(dolist (font (x-list-fonts "*"))
  (insert (format "%s\n" font)))
```

---
If you wanted to you could also add my full config

# Example Config
```el
;; Put backup files neatly away
(let ((backup-dir "~/.local/emacs-backups")
      (auto-saves-dir "~/.local/emacs-auto-saves/"))
  (dolist (dir (list backup-dir auto-saves-dir))
    (when (not (file-directory-p dir))
      (make-directory dir t)))
  (setq backup-directory-alist `(("." . ,backup-dir))
        auto-save-file-name-transforms `((".*" ,auto-saves-dir t))
        auto-save-list-file-prefix (concat auto-saves-dir ".saves-")
        tramp-backup-directory-alist `((".*" . ,backup-dir))
        tramp-auto-save-directory auto-saves-dir))

(setq backup-by-copying t    ; Don't delink hardlinks                           
      delete-old-versions t  ; Clean up the backups                             
      version-control t      ; Use version numbers on backups,                  
      kept-new-versions 5    ; keep some new versions                           
      kept-old-versions 2)   ; and some old ones, too     

; Setup Melpa as a package archive and enable the 'use-package' function
(require 'package)
(add-to-list 'package-archives
'("melpa" . "http://melpa.org/packages/") t)
(package-initialize)
(unless (package-installed-p 'use-package)
(package-refresh-contents)
(package-install 'use-package))

; Setup Darcula theme from melpa
(use-package darcula-theme
:ensure t
:config
(load-theme 'darcula t)
; and set a default font
(set-frame-font "Victor Mono-12"))

; Some user options for line numbers
(custom-set-variables
 '(display-line-numbers 'visual)
 '(package-selected-packages '(darcula-theme use-package)))

(custom-set-faces
 )
```