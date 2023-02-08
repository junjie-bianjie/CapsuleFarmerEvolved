This guide is aimed at advanced users who want to install and run the CapsuleFarmerEvolved on Linux.
Please note that this guide is not complete and may not work for you due to how many Linux flavours there are out there. 
Please also note that non-Windows users are not officially supported and may not receive support. For any issues that you may encounter, please open an issue on GitHub. If you are able to fix the issue yourself, please open a pull request instead! 

## Prerequisites
- Python ≥ 3.10.1 (version 3.9 should work as well but is not officially supported)
- pipenv (`pip install pipenv`)
- git

## Running from the source code
1. Clone the application from GitHub - `git clone https://github.com/LeagueOfPoro/CapsuleFarmerEvolved.git`
2. Move to the directory -  `cd CapsuleFarmerEvolved`
3. Install the Python virtual environment - `pipenv install`
4. Edit the configuration as the [configuration](https://github.com/LeagueOfPoro/CapsuleFarmerEvolved/wiki/Configuration) page describes
5. Run the tool with `pipenv run python ./main.py`

## Updating
Enter the directory where you cloned the application initially and run `git pull` to update the application.

## Running as a service

### Systemd
1. Create a new service file in `/etc/systemd/system/capsulefarmerevolved.service` with the following contents:
```
[Unit]
Description=CapsuleFarmerEvolved
After=network.target

[Service]
ExecStart=/usr/bin/python3 /path/to/CapsuleFarmerEvolved/main.py
WorkingDirectory=/path/to/CapsuleFarmerEvolved
StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=CapsuleFarmerEvolved
User=root
Group=root
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```
2. Run `systemctl daemon-reload` to reload the systemd daemon
3. Run `systemctl start capsulefarmerevolved` to start the service
4. Run `systemctl enable capsulefarmerevolved` to enable the service on boot

