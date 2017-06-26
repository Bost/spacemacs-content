# Helm narrowing & completion

[Helm](https://github.com/emacs-helm/helm) is an incremental completion and selection narrowing framework.  Its the central control tower of Spacemacs, it is used to manage buffers, projects, search results, configuration layers, toggles and more.

For example, Helm helps you navigate files and directory names, only showing the matching names to the pattern you type.  This minimises the need to type directory and file names in full.

If you have a rough idea of a command name, you can start to type it after `SPC SPC` or `M-x` and Helm will show you all the matching commands using fuzzy matching (matches anything that contains the pattern you have typed).

Once you have learnt the Spacemacs groupings for Helm its really fast to do anything, so take a look at the [Helm documentation wiki](https://github.com/emacs-helm/helm/wiki).

> ido mode is still available in Spacemacs but by default it is over-ridden by Helm.  You can enable ido using `dotspacemacs-use-ido t` in the `dotspacemacs/init` section of `.spacemacs`, however this only replaces a few commands.


