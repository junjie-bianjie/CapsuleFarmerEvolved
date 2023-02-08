This guide is aimed to users that wish to run the CapsuleFarmerEvolved on an Android device. Please note that non-Windows users are not officially supported and may not receive support. For any issues that you may encounter, please open an issue on GitHub. If you are able to fix the issue yourself, please open a pull request instead!

By @candsad#0337 and @Pengarrow#8873. Tested on Termux 0.118.0 with Android 11 and 13.


## Prerequisites
- Android 7.0 or newer.
- Latest Termux from F-droid (at the time of writting version 0.118.0 is the latest) [[Download here](https://f-droid.org/en/packages/com.termux/)].
- Python ≥ 3.10.1 (version 3.9 should work as well but is not officially supported) [`pkg install python`]
- pipenv (`pip install pipenv`)
- git (`pkg install git`)

To install the prerequisites, open Termux and run the commands above.
If asked, press `y` to confirm the installation.

## Installation

1. Open Termux.
2. Install the prerequisites (see above).
3. Clone the repository: `git clone https://github.com/LeagueOfPoro/CapsuleFarmerEvolved`
4. Move to the cloned directory: `cd CapsuleFarmerEvolved`
5. Install the Python virtual environment required: `pipenv install --python /data/data/com.termux/files/usr/bin/python`
6. Edit the configuration as the [configuration](Configuration) page describes. Use `nano config/config.json` to edit the file.
- Use arrow keys to move the cursor.
- Edit the values as required.
- When finished click `Ctrl + O` then enter to save.
- Use `Ctrl + X` to exit.
7. Run the tool with `pipenv run python ./src/main.py`

## Updating

Enter the directory where you cloned the application initially and run `git pull` to update the application.

## Allow Termux to run in the background

Go to your device status bar notifications, find Termux, press “Acquire wakelock”, which lets Termux run always so the program doesn’t get killed in the background.