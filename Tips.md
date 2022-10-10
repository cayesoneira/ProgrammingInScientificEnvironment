# Some programming tips.
- `docker run -e DISPLAY=192.168.62.21:0 -v gate:/gate -it --rm duartej/m1992-pyroot python` to open the interpreter. The important part is that we have to write our ip (we can see it in `ipconfig` command) with the ending in `:0`.
- All intructions after the last word in something like `docker run --rm -it duarte/m1992.pyroot/bin/bash` runs the instructions inside the container, apart from the instructions the own image has inside to run by default.
- 
