# lisp-extra-font-lock - Highlight bound variables and quoted exprs

*Author:* Anders Lindgren<br>
*Version:* 0.0.1<br>
*URL:* [https://github.com/Lindydancer/lisp-extra-font-lock](https://github.com/Lindydancer/lisp-extra-font-lock)<br>

This package highlight bound variables and quoted expressions in
lisp code.

The following screenshot demonstrates the highlighting effect of
this package:

![See doc/demo.png for screenshot](doc/demo.png)

## What is highlighted

* Parameters in functions and lambdas
* Variables bound by `let` and `dolist`. Global variables rebound
  by `let` is highlighted in a different color.
* Quoted expressions
* Backquoted expressions. However, subexpressions using the "," or
  ",@" are not highlighted. Also, the actual backquote and the
  comma operators are highlighted as a warning.

## Installation

Place this package in a directory in the load-path. To activate it,
use *customize* or place the following lines in a suitable init
file:

       (require 'lisp-extra-font-lock-mode)
       (lisp-extra-font-lock-global-mode 1)

## Customization

You can modify the following lists to add more functions that are
recognized:

* `lisp-extra-font-lock-let-functions` -- List of function with the
  same syntax as `let`.
* `lisp-extra-font-lock-defun-functions` -- List of function with
  the same syntax as `defun`.
* `lisp-extra-font-lock-lambda-functions` -- List of function with
  the same syntax as `lambda`.
* `lisp-extra-font-lock-dolist-functions` -- List of function with
  the same syntax as `dolist`.
* `lisp-extra-font-lock-bind-first-functions` -- List of function
  that bind their first argument, like `condition-case`.

The following faces are used when highlighting. You can either
redefine the face (e.g. using a theme), or you can rebind the
corresponding variable.

* Local variables are highlighted using the standard face
  `font-lock-variable-name-face`.
* Special (global) variables that are rebound by `let` are
  highlighted using the face bound to the variable
  `lisp-extra-font-lock-special-variable-name-face` (by default
  `lisp-extra-font-lock-special-variable-name`, which inherits from
  `font-lock-warning-face`.)
* Quoted expressions use the face bound to the variable
  `lisp-extra-font-lock-quoted-face` (by default
  `lisp-extra-font-lock-quoted`, which inherits from
  `font-lock-constant-face`.)
* The backquote and comma operators use the face bound to the
  variable `lisp-extra-font-lock-backquote-face` (by default
  `lisp-extra-font-lock-backquote`, which inherits from
  `font-lock-warning-face`.)

### Example

To set the face used to highlight quoted expressions to a gray
color, you can use:

        (custom-set-faces
          '(lisp-extra-font-lock-quoted ((t :foreground "grey50"))))


---
Converted from `lisp-extra-font-lock.el` by [*el2markdown*](https://github.com/Lindydancer/el2markdown).
