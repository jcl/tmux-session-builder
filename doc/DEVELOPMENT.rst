=======================
 DEVELOPMENT workspace
=======================


Test environment
================

Shell commands for test environment::

    # set-up:
    mkdir -p \
        ~/client-orgs/acme/acme-billing \
        ~/client-orgs/acme/acme-billing/billingservice-tracking \
        ~/client-orgs/acme/acme-planning \
        ~/client-orgs/acme/acme-knowledge \
        ~/client-orgs/acme/acme-webbrowserstart \
        ~/client-orgs/acme/gitclones/configuration-microsoft-365-mso
    # the following are for testing the vim command opening multiple files
    printf '%s\n' 'This is todo.rst' > ~/client-orgs/acme/acme-planning/todo.rst
    printf '%s\n' 'This is team-notes.rst' > ~/client-orgs/acme/acme-knowledge/team-notes.rst


    # teardown:
    rm -rf ~/client-orgs

Shell command for deleting *everything*::

    rm -rf ~/.tmux-session-builder ; rm -rf ~/client-orgs


Development TO-DO
=================


IDEAS
=====

* In ``bin/tmux-session-builder``:
  If ``$_tsb_use_template`` is not defined, fallback to using the session name
  as the template filename.

* Add support for `XDG Base Directory Specification` configuration directory:

  Rough draft for how the code should choose configuration directory:

    - If defined+exists+accessible, use:
      ``${XDG_CONFIG_HOME}/tmux-session-builder/``

    - Else, if exists+accessible, use:
      ``~/.config/tmux-session-builder/``

    - Else, if exists+accessible, use:
      ``~/.tmux-session-builder/``

  Related link dump:

      | https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
      | https://wiki.archlinux.org/title/XDG_Base_Directory
      | https://superuser.com/questions/365847/where-should-the-xdg-config-home-variable-be-defined/425712#425712
      | https://xdgbasedirectoryspecification.com/
      | https://unix.stackexchange.com/questions/537529/how-do-i-get-xdg-config-home-from-a-shell-script-command-line
      | https://www.ctrl.blog/entry/xdg-basedir-scripting.html

  This is the HN comment that made me add this idea:
  [April 2024] https://news.ycombinator.com/item?id=40086638

* Support custom Jinja-like variables, similar to ``{{ tmux_session_name }}``:

    - ``_tsb_variables`` is set in the sessionscript:
      set to a space separated list of Jinja-like variables to replace in the
      copied template file content.  Variables must only be lower-case ASCII
      alphabet letters and underscore.  Example: ``environment_instance`` will
      replace the string ``{{ environment_instance }}`` .

    - The string to replace a given Jinja-like variable with, is expected to
      be found in the variable ``_tsb_var_$VARIABLE``.  So the replacement for
      ``{{ environment_instance }}`` will be the contents of the sessionscript
      variable ``_tsb_var_environment_instance`` .

  Try to use ``eval`` to generate the variable name:
  https://unix.stackexchange.com/questions/41406/use-a-variable-reference-inside-another-variable

  Only activate this code path if ``_tsb_variables`` variable is defined.

* Add code that tests for dependencies (and for some, if we have the right
  ones/minimum versions)
