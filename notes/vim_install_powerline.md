1. yaourt -S python-powerline-git

    or https://github.com/Lokaltog/powerline

    `./setup.py install --user` to install for current user only

2. add config to .vimrc

        set rtp+=/usr/lib/python3.4/site-packages/Powerline-beta-py3.4.egg/powerline/bindings/vim/

3. Add config to ~/.bashrc

        . /usr/lib/python3.4/site-packages/Powerline-beta-py3.4.egg/powerline/bindings/bash/powerline.sh

4. https://github.com/Lokaltog/powerline-fontpatcher

        ./scripts/powerline-fontpatcher /usr/share/fonts/TTF/Monaco_Linux.ttf
        cp Monaco\ for\ Powerline.ttf ../.fonts/
        fc-cache -vf ~/.fonts/

----------

Install on a server which you can only install in your home directory

ALL prefix can be set to ~/.local/ which is a local version of /usr/ and /usr/local/

1. install both python2 and python3 from source

        ./configure --prefix=...
        make && make install

    vim must be compiled with --enable-pythoninterp and set --with-python-config-dir with your local python config,
    while python3 is used to intall powerline, since python2 doesn't come with setuptools, but it only needs python2
    to run powerline correctly

2. compile vim7.4 with (no need to --enable-python3interp)

        LD_LIBRARY_PATH=/home/renqing.crs/python/lib/ PATH=/home/renqing.crs/python/bin/:$PATH ./configure --enable-pythoninterp --with-features=huge --with-python-config-dir=/home/renqing.crs/python/lib/python2.7/config/ --prefix /home/renqing.crs/vim/

3. install powerline with python3.4

        /home/renqing.crs/python/bin/python3 ./setup.py build
        /home/renqing.crs/python/bin/python3 ./setup.py install --user

4. modify .vimrc

        set rtp+=/home/renqing.crs/.local/lib/python3.4/site-packages/Powerline-beta-py3.4.egg/powerline/bindings/vim/

5. you may need to `cp ~/.local/bin/ ~/.local/lib/python3.4/site-packages/Powerline-beta-py3.4.egg/scripts`, otherwise bash can't work with powerline

----------

TROUBLESHOOTING

1. In case you found error

    ...
    bash: PROMPT_COMMAND: line 3: syntax error near unexpected token `;`
    ...

    SOLUTION:

    add `unset PROMPT_COMMAND` to the end of `~/.bash_profile`

