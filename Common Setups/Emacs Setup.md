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
(set-frame-font "Liberation Mono-12")
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
(let ((backup-dir "~/.emacs.d/backups")
      (auto-saves-dir "~/.emacs.d/auto-saves/"))               ;; Put backup files neatly away
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

(defalias 'yes-or-no-p 'y-or-n-p)                             ;; Make sure we only have to answer with y or n
(setq-default save-place-mode 1)                              ;; Set emacs to remember last editing positions
(setq save-place-file "~/.emacs.d/saveplace")                 ;; And where to place the marker-file
(setq inhibit-startup-screen t)                               ;; prevent normal start behavior
(add-to-list 'default-frame-alist '(fullscreen . maximized))  ;; Maximise(if we can) the window initially

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
(load-theme 'darcula t)                ;; load the theme
(set-frame-font "Liberation Mono-12")  ;; and set a default font
)

; Some user options for line numbers
(custom-set-variables
 ;; custom-set-variables was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 '(display-line-numbers 'visual) ;; This sets relative line numbers
 '(package-selected-packages
   '(helpful magithub magit darcula-theme use-package)))  ;; Install some needed packages

(custom-set-faces
 ;; custom-set-faces was added by Custom.
 ;; If you edit it by hand, you could mess it up, so be careful.
 ;; Your init file should contain only one such instance.
 ;; If there is more than one, they won't work right.
 )
```