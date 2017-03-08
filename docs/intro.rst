Quick start
===========

Install
-------

::

    sudo pip install envie


Configuration
-------------

::

    envie config

For details, see :doc:`config`.

After envie is configured, source your ``.bashrc``, or start a fresh shell:

.. code-block:: bash

    . ~/.bashrc


Start with ``envie help``
-------------------------

::

    Your virtual environments wrangler. Holds no assumptions on virtual env dir
    location in relation to code, but works best if they're near (nested or in level).

    Usage:
        envie {create [ENV] | remove | list [DIR] | find [DIR] | go [KEYWORDS] |
               python [SCRIPT] | run CMD | index | config}
        envie SCRIPT
        envie [KEYWORDS]

    Commands:
        python SCRIPT  run Python SCRIPT in the closest environment
        run CMD        execute CMD in the closest environment. CMD can be a
                       script file, command, builtin, alias, or a function.
        index          (re-)index virtualenvs under /home/stevie
        config         interactively configure Envie
        help           this help

        create [ENV]   create a new virtual environment (alias for mkenv)
        tmp, temporary create a throw-away env in /tmp (alias for mkenv -t)
        install        create env and install all detected requirements.txt (mkenv -a)
        remove         destroy the active environment (alias for rmenv)

        list [DIR]     list virtual envs under DIR (alias for lsenv)
        find [DIR]     like 'list', but also look above, until env found (alias for lsupenv)
        go [KEYWORDS]  interactively activate the closest environment (alias for chenv)
                       (adaptively select the most relevant virtual env for list of KEYWORDS)

    The second form is a shorthand for executing python scripts in the closest 
    virtual environment, without the need for a manual env activation. It's convenient
    for hash bangs:
        #!/usr/bin/env envie
        # Python script here will be executed in the closest virtual env

    The third form is basically an alias for 'chenv -1 -v'. It activates the closest
    environment (relative to cwd, filtered by KEYWORDS), but only if it's unambiguous.

    For more details on a command, see its help with '-h', e.g. 'envie find -h'.

    Examples:
        envie python               # run interactive Python shell in the closest env
        envie manage.py shell      # run Django shell in the project env (auto activate)
        envie run /path/to/exec    # execute an executable in the closest env
        envie go my cool project   # activate the env with words my,cool,project in its path

        mkenv -ta && ./setup.py test && rmenv -f     # run tests in a throw-away env (with reqs)
        envie tmp -a && ./setup.py test && envie remove -f   # more verbose version of the above
