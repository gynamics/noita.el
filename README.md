# noita.el

Key-oriented programming in Emacs.

![Screenshot](https://exiled-images.pages.dev/file/AgACAgUAAyEGAASL6SCLAAMbabFyMM0tYCu7J5UlOv1fSDJNDZMAAioQaxugDYlVW8p0yBRo9L0BAAMCAAN3AAM6BA.jpeg)

## About

In Emacs, sometimes I feel like keys are actual atoms for programming ... Just lack of some intuitative representaion. I mean, when you press `C-x (`, it is usually after something already happen, and without that you just can not press `C-x e` at ease.

So this idea born: an analytic continuation of keys. When text is lifted back to keys, it constructs a visual tree of macros.  This toy is mostly useless and full of unsatisfying facts when you want to put it into actual pratice (compared to existing `kmacro` system).

Inspired by [elmacro](https://github.com/Silex/elmacro) and [dmacro](https://github.com/emacs-jp/dmacro).

## Installation

``` emacs-lisp
;; Install from Github, for emacs-30+
(use-package noita :vc (:url "https://github.com/gynamics/noita.el"))
```

# Usage
Select the buffer you want to work on, then type `M-x n o i t a RET`, a new buffer should then be created. Then, all your input keys (local to your work buffer) will be recorded in this buffer.

Noita is designed to be buffer-local:
- Your selected work buffer is called image buffer. Image buffer has a minor mode `noita-minor-mode` enabled.
- The created new buffer recording keys is called control buffer. Control buffer has major mode `noita-mode` enabled.

You can explore key bindings in these two different modes with `C-h m` in these two buffers.

The main operation in control buffer is `noita-project`: press `C-c C-c` on an region or a line in control buffer, these keys will be send to window of image buffer. There is also a small set of editing functions in `noita-mode`, mostly started with `C-c` prefix.

Currently, each work buffer can only have one unique control buffer, each control buffer can only project to one unique image buffer. However, a control buffer can be made an image buffer recursively (not recommended).

# Customization
There are several custom variables for configuration, run `M-x customize-group RET noita RET` for customization.

# Development
There are several feature requests (FR) that are not implemented yet. I wrote them in comments but I am not sure if I will implement them in the future. After all, I expect there won't be a lot of people interested in this package.

If you have some good ideas, or found a bug, feel free to raise an issue! You can also find me at [EmacsChina](https://emacs-china.org/u/gynamics).
