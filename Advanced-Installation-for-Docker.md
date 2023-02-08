This guide is aimed to users that wish to run the CapsuleFarmerEvolved on an Android device. Please note that non-Windows users are not officially supported and may not receive support. For any issues that you may encounter, please open an issue on GitHub. If you are able to fix the issue yourself, please open a pull request instead!

## Prerequisites
Docker

## Docker Installation

Create a [`config.yaml`](https://github.com/LeagueOfPoro/CapsuleFarmerEvolved/wiki/Configuration) file in the folder you want your docker files to exist in.

Edit the `/path/to/config.yaml` to the absolute path to your [configuration](https://github.com/LeagueOfPoro/CapsuleFarmerEvolved/wiki/Configuration) file. 
Run the container in the background:
```
docker run -it --restart unless-stopped --name CapsuleFarmer -d -v /path/to/config.yaml:/config/config.yaml  leagueofporo/capsulefarmer:master
```

Attach to the container to check it by using `docker attach CapsuleFarmer`

## Building your own image locally
If you want to build the image locally:
1. Clone this repo and move to it's direcotry
2. Build the image: `docker build -t capsulefarmerevolved`.
3. Edit the `/path/to/config.yaml` to absolute path to your configuration file and run the container in the background:
```docker
docker run -it --restart unless-stopped -d -v /path/to/config.yaml:/config/config.yaml  capsulefarmerevolved
```