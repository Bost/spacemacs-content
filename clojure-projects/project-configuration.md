# Project level configuration
`.dir-locals.el` files provide project level configuration, configuring the default project type, build tool and other CIDER actions.

`SPC p e` to edit a `.dir-locals.el` file in the current project.  If a file does not yet exist for the current project, is created when the buffer is saved.

> #### Hint::Force loading the .dir-locals.el configuration
> If a `.dir-locals.el` file is created after a file from the project is open, then the variables will not be applied to that buffer.
>
> `SPC f A` to reload a file already open and apply the variables in the `.dir-locals.el` file.


## Example configurations
An example of setting the Clojure CLI tool as the default Clojure tool (rather than Leiningen or Boot). Also configuring several `deps.edn` aliases to be used when starting the REPL via Clojure CLI.

```elisp
((clojure-mode . ((cider-preferred-build-tool . clojure-cli)
                  (cider-clojure-cli-global-options . "-A:dev:test-path:spec-test"))))
```

An example of a ClojureScript project using figwheel-main, Clojure CLI and hiding the display banner in the REPL browser
```
((clojure-mode . ((cider-preferred-build-tool          . clojure-cli)
                  (cider-clojure-cli-global-options    . "-A:fig:dev")
                  (cider-default-cljs-repl             . figwheel-main)
                  (cider-figwheel-main-default-options . "dev")
                  (cider-repl-display-help-banner      . nil))))
```

## Common configurations
[CIDER documentation - basic configuration](https://docs.cider.mx/cider/) describes many of the configuration variables available.

Practicalli also create [a list of variables](/reference/cider/configuration-variables.md) extracted from the [clojure-emacs/cider](/reference/cider/configuration-variables.md) project.

`.dir-locals.el` is also useful for setting Projectile configuration, e.g. the project-type.  This is especially useful for [monorepo or nested projects](monorepo-nested-projects.md).

> #### Hint::Set as Global options
> The variables can also be added using `(setq )` to `dotspacemacs/user-config` section of `.spacemacs` to set a default variable for all projects.  The `.dir-locals.el` file will over-ride the global settings.
>
> `(setq (cider-preferred-build-tool 'clojure-cli))`


## Understanding the syntax
Elisp uses a two-element tuples called cons cells, create using the cons function, or with a dotted-pair notation.  This is loosely equivalent to key-value pairs in a Clojure hash-map.

cons cell example
```elisp
(cons "config-variable-name" "custom-value")
```

dotted-pair example
```elisp
'("config-variable-name" . "custom-value")
```

Multiple key-value pairs are defined as a collection of these cons cells in a list.

(("config-variable-name" . "custom-value")
 ("config-variable-name2" . "custom-value2"))

`.dir-locals.el` is a list of dotted-pairs for each major mode.  The value for the major mode is another list of dotted pairs which may contain one or more dotted-pairs.

((clojure-mode . ((config-var1 . "custom-value1")
                  (config-var2 . "custom-value2")))
 (org-mode . ((config-var3 . "custom-value3"))))

The configuration variables are set when a file is open in a specific Emacs major mode.

> #### Hint::Avoid using `nil` for major mode
> Avoid  using `nil` for the major mode as this will apply the variables in all buffers regardless of their major mode, potentially leading to conflicts.  Ensure that if `nil` is used that testing is done to ensure issues do not arise.


## Custom code
`eval` variable will evaluate custom code specified when a variable is used. For example, if using a new type of ClojureScript REPL that CIDER does not currently know, then custom elisp code can be added to make CIDER do the required actions.

```elisp
((cider-mode . ((eval . (cider-register-cljs-repl-type 'new-cljs-repl "(custom-elisp-function-for-new-cljs-repl)"))
                (cider-default-cljs-repl . new-cljs-repl))))
```


## References
* [CIDER list of configuration variables](/reference/cider/configuration-variables.md)
* [Emacs Wiki: per-directory local variables](https://www.gnu.org/software/emacs/manual/html_node/emacs/Directory-Variables.html)
* [Project level Emacs config with .dir-locals.el](https://lambdaisland.com/blog/2019-12-21-advent-of-parens-21-project-config-dir-locals) - lambdaisland

Also review directory variables in the Emacs the info pages

```elisp
(info "(emacs) Directory Variables").
```