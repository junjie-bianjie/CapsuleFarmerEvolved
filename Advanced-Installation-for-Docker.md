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