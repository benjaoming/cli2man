README CLI2MAN
--------------

Cli2Man parses a program's --help option output and tries to put together a half-decent manpage. The author of this script was a user of help2man, which is more than a decade old and can still be recommended. But when it didn't work like the author wished and fixing the bugs in the PERL source code seemed impossible, because it was poorly documented code with mindblowing use of cryptic regex, the idea was to write a simple parser like docopt is parsing --help messages to generate CLI.

The author simply took the docopt source and started hacking and after a couple of hours everything started to work amazingly good. This speed of development was possible, because the docopt authors already had done the hard work of writing the parser.

Unfortunately the docopt parser isn't very permissive, but rather strict. For example the ArgumentParser of Python that the author was using produces slightly ""malformated"" --help pages and therefore Cli2Man has to introduce a lot of hacks to make foreign --help messages somehow work with the docopt parser.

As output format the choice was the mdoc macros for manpages, because the author had seen a nice presentation on their beauty just a couple of hours earlier. MDoc is more of a semantic format that's designed for manpages, while the man format that's the default on Linux distributions is more like a typesetting format. But this shouldn't be a problem, since usually all Linux distributions (groff is doing this work on Linux) should be able to handle manpages with mdoc macros fine. And on BSDs mdoc/mandoc is now the default. And should you still have a problem with the mdoc format, well, there's a converter from mdoc to man in mandoc (and probably also in groff).

INSTALLING
----------

- Get Cli2Man
- Extract
- run python setup.py install

HOW TO USE IT
-------------

Get mdoc output of any program with --help:
cli2man program

Write manpage to file:
cli2man program -o manpage

View temporary manpage:
cli2man program -m

View manpage just written to file:
cli2man program -m -o manpage

DEVELOPMENT / BUGS:
-------------------

Cli2Man is in very early development stages, and is basically docopt + a lot of dirty hacking. But you can generate manpages, if the input is compatible with docopt or if you're lucky enough. The chances aren't bad. But there are glitches. So don't get your hopes too high. The good news is that Cli2Man is written in python and to improving it should be possible rather fast. As said before, it was written in a couple of hours. 

What's not working right now is ordering sections. The --include option is not final, right now you can import MDoc formated files, but maybe we should allow Markdown or something like that.

The parser at the moment doesn't read the description from --help. Will be fixed soon, though.

Many missing features, like reading Copyright info and so on, but that's really high priority stuff.

You're welcome to contribute.


