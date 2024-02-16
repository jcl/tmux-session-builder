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

    find ~/bin -maxdepth 1 -not -type d -name ',*' -delete ; rm -rf ~/.tmux-session-builder ; rm -rf ~/client-orgs


Development TO-DO
=================


IDEAS
=====

* Add code that tests for dependencies (and for some, if we have the right
  ones/minimum versions)
