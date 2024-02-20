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
