# BBC micro:bit MicroPython Bakefile

Bakefile with scripts to make BBC micro:bit MicroPython development more effective. No special IDE or editor is needed. 
Only Bash and Python 3. 

Just write you code and let the bake to do the rest. 

## Installation

1. Clone this repo
2. Create Python virtualenv the way you prefer (optional)
3. `pip install -r requirements.txt`

Besides [bake-cli](https://github.com/kennethreitz/bake), `requirements.txt` contains several tools that can come in handy on they own (like `uflash` or `pyminifier`).  

## Usage

`bake minify <file>` minifies the Python source file

`bake compile <file>` minifies the Python source file and makes a hex file from it

`bake upload <file> [<file> [<file> ...]]` minifies and upload given Python files to micro:bit board filesystem

`bake flash <file>` minifies and hexifies the Python source file and uploads to micro:bit

`bake flash_clean` uploads pure micropython firmware

`bake flash_fast <file>` skips minification and uploads hexified Python source without creating a hex file

`bake clean` removes the `out/` folder with all minified python sources and hex files

All `flash` and `upload` commands check if micro:bit board is connected. If it is not available, they won't execute the upload.

All files created by scripts are stored in `out/` folder.

## hex firmware and `main.py`

There is a certain difference in the `bake upload` command and the `flash` commands.

The `flash` commands always upload a hex file with firmware containing a micropython interpreter.
Your program can be part of the firmware hex file.

The `upload` command stores given files to micro:bit filesystem without overwriting the firmware. 
Stored Python program can be split into multiple modules and Python import system works like in classic Python.

Whatever custom script is stored inside the hex file, it can be overridden by uploading file named `main.py` which is always executed instead of script in the firmware if it exists.

Look [here](https://microbit-micropython.readthedocs.io/en/v1.0.1/tutorials/storage.html#mainly-main-py) for more info.
