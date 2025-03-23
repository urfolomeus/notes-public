# Python Major Versions

There are two major versions of Python that you will come across: Python 2 and Python 3. To date I have never had to use Python 2 for anything. I believe that the main reason that it is still around is due to backward comatibility issues and the number of older projects running on that version. That said, if your machine comes with Python pre-installed, the chances are that the `python` command runs Python 2 and the `python3` command runs Python 3.

When we use a version manager such as pyenv or asdf to install Python versions on our machines, that version manager will usuall shim the `python` command to the current version that you are using, whatever that may be. In any case, you can find which version of Python is being used by each command using `which` to see which binary is being used and `python -V` to see which version of Python each is using:

```
❯ which python
/home/alangardner/.asdf/shims/python

❯ which python3
/home/alangardner/.asdf/shims/python3

❯ which python2
/usr/bin/python2

❯ python -V
Python 3.8.6

❯ python3 -V
Python 3.8.6

❯ python2 -V
Python 2.7.18
```
