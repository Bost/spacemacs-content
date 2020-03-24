# Switch to Spacemacs develop branch
Until the release of Spacemacs 0.300 it is highly recommended to use the Spacemacs `develop` branch.

If you have installed the default Spacemacs `master` branch, follow these steps to switch smoothly to Spacemacs `develop` branch.

## Clean the Spacemacs install
If you made changes to the  `~/.spacemacs` file, them move the file or rename it. Otherwise delete the `~/.spacemacs` file.

Delete the `~/.emacs.d` directory or just the `~/emacs.d/elpa/` directory.

## Install the Spacemacs develop branch
Clone the Spacemacs develop branch

```shell
git clone -b develop https://github.com/syl20bnr/spacemacs ~/.emacs.d
```

Or just change the Git branch if you did not delete the `~/.emacs.d/` directory.

```shell
cd ~/.emacs.d/
git checkout -b develop
```

## Apply your customisations
If you have changes from the original Spacemacs install:

`SPC D f f` to open ediff with the new `~/.spacemacs` file and your backup file.

Copy changes to the new `~/.spacemacs`.

## Restart Spacemacs
`SPC q r` to restart Spacemacs and ensure that all packages downloaded successfully and are loaded in the correct order.
