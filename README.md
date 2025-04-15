# pattern.py - a reimplementation of pattern\_create/pattern\_offset for Python 3
Metasploit comes with multiple very convenient scripts and utilities. Among
the most valuable for me are pattern_create and pattern_offset. I found it
increasingly annoying that both have a relatively long startup time.

So after I overheard one of my colleagues complaining about this as well,
I quickly hacked together a Python version that basically does the same.
## Usage
```
$ python3 pattern.py
Usage: python3 pattern.py (create | offset) <buflen> <value>
```
So, to create a 2048 byte pattern you run
```
$ python3 pattern.py create 2048
Aa0Aa1Aa2[...snip...]p7Cp8Cp9Cq0Cq1Cq
```
and it outputs a unique pattern of said length. To find an offset in the
buffer, let's say f9Cg, you run
```
$ python3 pattern.py offset 8192 f9Cg
1738
```
and the program returns the offset until the requested series. You can also
look for memory values. The values need to be little-endian and prefixed
with 0x:
```
$ python3 pattern.py offset 8192 0x67433966
1738
```
