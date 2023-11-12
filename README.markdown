Bookmarkdown
============

This is a fork of [Bookmarkdown](https://github.com/sll/bookmarkdown) made by [Steve Losh](https://stevelosh.com). 

Its purpose is to let publish book easier with Markdown file.

However this software was coded in 2000 and no longer maintained which means it supports Python2 only instead of Python3, so there are some tricks to get it running.

Install
-------

/usr/local/bin/python -m pip install baker
/usr/local/bin/python -m pip install jinja2
/usr/local/bin/python -m pip install Markdown
/usr/local/bin/python -m pip install pyquery=1.4.0

Then add the following lines into Markdown and put it after "import sys", or it will encounter "UnicodeDecodeError: 'ascii' codec can't decode byte 0xe6 in position 2: ordinal not in range(128). -- Note: Markdown only accepts unicode input!":

`vim ~/.local/lib64/python2.7/site-packages/markdown/core.py`

```text
reload(sys)
sys.setdefaultencoding('utf-8')
```

Structure
--------

Your book should have similar structure as below:

+chapters
++++chapter00.md
++++chapter01.md
+preface.md
+knowledgement.md
+config.py
+build.sh

Config.py
---------

title = 'book title'
author = 'the author name'
author_url = 'link'

Build.sh
--------

#!/usr/bin/env bash

set -e
python ../bookmarkdown/bookmarkdown/bookmarkdown build

Usage
-----

Put this software into the same directory with your book.
1. Build the html file by change to your book directory and type command `bash ./build.sh`, then the rendered file will be in the directory named build
2. Type command to run a simple server `python ../bookdown/bookdown/bookdown serve`
3. Fire a browser and type address http://127.0.0.1:8000
