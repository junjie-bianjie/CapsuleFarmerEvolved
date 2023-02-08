This guide is aimed to users that wish to run the CapsuleFarmerEvolved on an Synology Docker system. Please note that non-Windows users are not officially supported and may not receive support. For any issues that you may encounter, please open an issue on GitHub. If you are able to fix the issue yourself, please open a pull request instead!
By @Silver#0008

## Prerequisites 
Docker compatibility - 64 bit version of DSM

Notes: Works on DS220+ DSM 7.1.1-42962 
Please comment or leave a message on the discord server if your setup works too! 

## Step by step
1. Create a separate shared folder for your Docker files in your control panel. In this shared folder, create another directory where you will have your `config.yaml` file, setup your [configuration](Configuration) file.  
2. Open Docker and go to the registry to search for the Docker image `leagueofporo/capsulefarmer`. Download the image by right-clicking and selecting "download this image."
3. Once the image is downloaded, go to the containers and create a new container. In the network settings, select the bridge and click next.
4. It is recommended to leave the auto start option off until the setup is confirmed to be working.
5. Skip port settings
6. In the volume settings, `Add File` and add the `config.yaml` file and map the volume to the mount path to be exactly `/config/config.yaml`.It is not necessary to check the read-only option.
7. Once the container is created, it should be running and using some CPU and RAM. If it stops running, check the logs for any issues.
8. Re-enable auto-start for the container. 