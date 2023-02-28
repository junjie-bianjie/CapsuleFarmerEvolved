This guide is aimed at advanced users who want to install and run the CapsuleFarmerEvolved on Macos.
Please note that this guide is not complete and just test on apple Chip, so may not work for you computer.
For any issues that you may encounter, please open an issue on GitHub. If you are able to fix the issue yourself, please open a pull request instead!

## Prerequisites
- Python ≥ 3.10.1 (version 3.9 should work as well but is not officially supported)[download](https://www.python.org/downloads)
- pip (`curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && python3 get-pip.py`, `then export the pip to PATH`)
- pipenv (`pip install pipenv`)
- If you are in chinese Mainland Then Use (`pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pipenv`)
- git

## Running from the source code
1. Clone the application from GitHub - `git clone https://github.com/LeagueOfPoro/CapsuleFarmerEvolved.git`
2. Move to the directory -  `cd CapsuleFarmerEvolved`
3. Install the Python virtual environment - `pipenv install python3`
4. Edit the configuration as the [configuration](https://github.com/LeagueOfPoro/CapsuleFarmerEvolved/wiki/Configuration) page describes
5. Run the tool with `pipenv run python3 ./src/main.py`

## Updating
Enter the directory where you cloned the application initially and run `git pull` to update the application.

If you receive `Exception has occurred: ModuleNotFoundError`, run `pipenv install` to update dependencies.

