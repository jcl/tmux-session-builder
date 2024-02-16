======================
 tmux-session-builder
======================


This repository contains `tmux-session-builder`: A simple tmux_ session creator:

* Automates creation of tmux sessions, windows, panes, keyboard input, etc.
* Written in POSIX compliant shell (``/bin/sh``), utilizing dependencies:
    - GNU coreutils (``cat``, ``chmod``, ``cp``, ``date``, ``ln``, ``mkdir``,
      ``mktemp``, ``rm``, ``tee``)
    - GNU sed (``sed``)
    - tmux_

.. _tmux: https://github.com/tmux/tmux/wiki


How to use
==========

::

    # clone this repository to somewhere appropriate
    git clone https://github.com/jcl/tmux-session-builder.git

Per-user configuration::

    mkdir -p   ~/.tmux-session-builder/sessionscripts \
               ~/.tmux-session-builder/templates
    chmod 0700 ~/.tmux-session-builder/sessionscripts \
               ~/.tmux-session-builder/templates \
               ~/.tmux-session-builder

    # change your shell configuration file(s) (eg. ~/.profile , ~/.bashrc) to
    # include this path in the PATH environment variable:
    #
    #     ~/.tmux-session-builder/sessionscripts
    #
    # can also be added to PATH of the currently running shell by executing:
    #
    #     export PATH="~/.tmux-session-builder/sessionscripts:$PATH"


    # execute the following commands in the root of the cloned
    # tmux-session-builder.git directory:

    # create symlink to tmux-session-builder in well-known place:
    ln -s -f "$(realpath bin/tmux-session-builder)" ~/.tmux-session-builder/

    # the following commands sets up the included example templates and
    # sessionscripts:
    cp doc/examples/.tmux-session-builder/templates/manage ~/.tmux-session-builder/templates/
    cp doc/examples/.tmux-session-builder/sessionscripts/,manage ~/.tmux-session-builder/sessionscripts/

    cp doc/examples/.tmux-session-builder/templates/srv-all ~/.tmux-session-builder/templates/
    cp doc/examples/.tmux-session-builder/sessionscripts/,sshsessions ~/.tmux-session-builder/sessionscripts/

    chmod 0600 ~/.tmux-session-builder/templates/*
    chmod 0700 ~/.tmux-session-builder/sessionscripts/,*
