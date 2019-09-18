# my-emacs

My Emacs

[emacs-tw/awesome-emacs](https://github.com/emacs-tw/awesome-emacs)

## MELPA

[MELPA: getting started](http://stable.melpa.org/#/getting-started)

`~/.emacs.d/init.el`

```el
(require 'package)
(let* ((no-ssl (and (memq system-type '(windows-nt ms-dos))
                    (not (gnutls-available-p))))
       (proto (if no-ssl "http" "https")))
  ;; Comment/uncomment these two lines to enable/disable MELPA and MELPA Stable as desired
  (add-to-list 'package-archives (cons "melpa" (concat proto "://melpa.org/packages/")) t)
  ;;(add-to-list 'package-archives (cons "melpa-stable" (concat proto "://stable.melpa.org/packages/")) t)
  (when (< emacs-major-version 24)
    ;; For important compatibility libraries like cl-lib
    (add-to-list 'package-archives (cons "gnu" (concat proto "://elpa.gnu.org/packages/")))))
(package-initialize)
```

`M-x package-list-packages`

## Theme

[emacs theme gallery](https://pawelbx.github.io/emacs-theme-gallery/)

1. `M-x package-list-packages`
1. `Control s: zenbrun-theme`. `C-s` 반복
1. `i`: 설치
1. `x`: 실행
1. `yes`

`init.el`에 자동시작 스크립트 추가

```el
(load-theme 'zenburn t)
```

## Dired

[DiredMode](https://www.emacswiki.org/emacs/DiredMode)

`C-x d` or `C-x 4 d`

## Wind Move

[Wind Move](https://www.emacswiki.org/emacs/WindMove)

`C-c` + `화살표 키`: 원하는 창으로 옮겨갈 수 있다.
`C-x o`를 대체한다.

```el
(when (fboundp 'windmove-default-keybindings)
  (windmove-default-keybindings))

(windmove-default-keybindings 'meta)

(global-set-key (kbd "C-c <left>")  'windmove-left)
(global-set-key (kbd "C-c <right>") 'windmove-right)
(global-set-key (kbd "C-c <up>")    'windmove-up)
(global-set-key (kbd "C-c <down>")  'windmove-down)
```

## Indentation

[Indentation Basics](https://www.emacswiki.org/emacs/IndentationBasics)

```el
(setq-default indent-tabs-mode nil)
(setq tab-width 2)
(defvaralias 'c-basic-offset 'tab-width)
(defvaralias 'cperl-indent-level 'tab-width)
```
