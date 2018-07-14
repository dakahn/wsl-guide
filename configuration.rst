Configuration
=============

Poor directory syntax highlighting in ``ls`` and ``la``
-------------------------------------------------------

There are a few ways to fix the obnoxious ``dir`` highlighting depending on your situation:


For Bash users (stock WSL install)
..................................

Add this line to the bottom of your ``.bashrc`` file::

``LS_COLORS=$LS_COLORS:'ow=1;34:' ; export LS_COLORS``

For ZSH/OhMyZsh users
......................

Add the following lines to the bottom of your ``.zshrc`` file::

    #Change ls colours
    LS_COLORS="ow=01;36;40" && export LS_COLORS

    #make cd use the ls colours
    zstyle ':completion:*' list-colors "${(@s.:.)LS_COLORS}"
    autoload -Uz compinit
    compinit

Big thanks go to `lloydstubber's great personal WSL setup guide <https://github.com/lloydstubber/my-wsl-setup>`_ for the code.


Hyper Terminal
--------------

`Hyper Terminal <https://github.com/zeit/hyper>`_ can fully replace the stock terminal for WSL and can improve your overall developer experience but you should tweak a few options in ``~/.hyper``. Notably these two::

    // The preferred shell since it's the default shell in your /etc/passwd file
    shell: wsl.exe,
    // But it's by default a login shell, so omit the --login flag
    shellArgs: [],