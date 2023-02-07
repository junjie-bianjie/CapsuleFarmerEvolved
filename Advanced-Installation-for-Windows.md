⚠️ If you are looking for a quickstart guide, please see [Quickstart guide](Quickstart-guide-(Windows)). 
This guide is for advanced users who want to install CapsuleFarmerEvolved on Windows and compile it from source code.

## Prerequisites
- Windows 10 or 11 (Windows 8 is reported to work but is not supported)
- Python ≥ 3.10.1 (version 3.9 should work as well but is not officially supported)
- pipenv (`pip install pipenv`)
- pyinstaller (`pip install pyinstaller`) [optional, only if you want to compile the application yourself]
- git [optional, only if you want to run the application from source code]
- 7zip [optional, only if you want to compile the application from source code and zip the output files]

Please note that all of the above must be on your PATH. If they are not, add them to your PATH.
Refer to [this guide](https://www.architectryan.com/2018/03/17/add-to-the-path-on-windows-10/) for more information.

## Running from source code

1. Download and extract the latest source code available from the [Releases tab](https://github.com/LeagueOfPoro/CapsuleFarmerEvolved/releases/latest) ('Source code (zip)' file) or via `git clone https://github.com/LeagueOfPoro/CapsuleFarmerEvolved.git`
2. Generate the config files as required by the application - see [Configuration](Configuration) for details.
3. Run `pipenv install` to install the required dependencies.
4. Run `pipenv run python ./src/main.py` to start the application.

### Troubleshooting

#### `ModuleNotFoundError` errors
Did you run `pipenv install`? If not, run it and try again. (Step 3)

#### `pip not found` error
Did you install pipenv? If not, install it and try again. (As shown in the Prerequisites section)

#### `pipenv: command not found`
Did you install pipenv? If not, install it and try again. (As shown in the Prerequisites section)

Remember: If you have installed pipenv, make sure it is in your PATH. If it is not, add it to your PATH.
(See [this](https://stackoverflow.com/questions/44272416/pipenv-command-not-found) StackOverflow answer for more details)
You can also try `python -m pipenv <COMMAND>` instead, but this is not recommended.


## Compiling the application

If the application is running from the source code, you can also compile it into a single executable file using pyinstaller.

1. Run `pipenv install` to install the required dependencies.
2. If you have not already, generate the config files as required by the application - see [Configuration](Configuration) for details.
3. Open a terminal in the root directory of the project (you should see `src` and `config` directories if you type `dir`).
4. Run `setup/windows.bat` (CMD/PowerShell compatible)
5. The compiled executable will be in the `build` directory. You can quickly start it with `./build/CapsuleFarmerEvolved.exe`

## CLI
```
usage: CapsuleFarmerEvolved.exe [-h] [-c CONFIGPATH]

Farm Esports Capsules by watching all matches on lolesports.com.

options:
  -h, --help            show this help message and exit
  -c CONFIGPATH, --config CONFIGPATH
                        Path to a custom config file
```
```bash
capsulefarmerevolved.exe --config /path/to/config.yaml
```