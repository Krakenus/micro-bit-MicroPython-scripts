# BBC micro:bit MicroPython scripts

Bash scripts to make BBC micro:bit MicroPython development more effective. No special IDE or editor is needed. 
Only Bash and Python 3. 

Just write you code and let the scripts to do the rest. 

## Installation

1. Clone this repo
2. Create Python virtualenv the way you prefer (optional)
3. `pip install -r requirements.txt`

`requirements.txt` contains several tools that can come in handy on they own (like `uflash` or `pyminifier`). 

[bake-cli](https://github.com/kennethreitz/bake) is also installed because it is used to execute scripts. 

## Usage

`bake minify <file>` minifies the Python source file

`bake compile <file>` minifies the Python source file and makes a hex file from it.

`bake upload <file>` minifies and hexifies the Python source file and uploads to your micro:bit board if it's connected

`bake upload_fast <file>` skips minification and uploads hexified Python source without creating a hex file

`bake clean` removes the `out/` folder with all minified python sources and hex files
