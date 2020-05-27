# How to find process id in Linux

When looking at the running processes with `top` you see only the software
running (e.g. Python).

In order to get the full command given, like, for example
```bash
python file.py
```
run the command in the console
```bash
ps aux
```
It can be combined with `grep` to narrow down the search
```bash
ps aux | grep "file.py"
```