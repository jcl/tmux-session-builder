======================
 tmux-session-builder
======================


This repository contains `tmux-session-builder`: A simple tmux_ session creator:

* Automates creation of tmux sessions, windows, panes, keyboard input, etc.
* Written in POSIX compliant shell (``/bin/sh``), utilizing dependencies:
  GNU coreutils (``cat``, ``date``, ``mktemp``, ``tee``), GNU sed (``sed``).

.. _tmux: https://github.com/tmux/tmux/wiki


How to use
==========

::

    # clone this repository to somewhere appropriate
    git clone https://github.com/jcl/tmux-session-builder.git

Per-user configuration::

    mkdir -p   ~/.tmux-session-builder/symlinks \
               ~/.tmux-session-builder/templates
    chmod 0700 ~/.tmux-session-builder/symlinks \
               ~/.tmux-session-builder/templates \
               ~/.tmux-session-builder

    # change your shell configuration file(s) (eg. ~/.bashrc) to include this
    # path in the PATH environment variable:
    #
    #     ~/.tmux-session-builder/symlinks
    #
    # can also be added to PATH of the currently running shell by executing:
    #
    #     export PATH="~/.tmux-session-builder/symlinks:$PATH"


    # the following commands sets up the included example templates and
    # session definitions:
    #
    # * templates: from below doc/examples/.tmux-session-builder/templates/
    # * sessions: hardcoded (for now) in bin/tmux-session-builder
    #
    # execute the following commands in the root of the cloned
    # tmux-session-builder.git directory:

    cp doc/examples/.tmux-session-builder/templates/manage ~/.tmux-session-builder/templates/
    ln -s -r -f bin/tmux-session-builder ~/.tmux-session-builder/symlinks/,manage

    cp doc/examples/.tmux-session-builder/templates/srv-all ~/.tmux-session-builder/templates/
    ln -s -r -f bin/tmux-session-builder ~/.tmux-session-builder/symlinks/,sshsessions
