
# ⚠️ This section is used for archival purposes. We do not recommend using these scripts. ⚠️
*Please note to not update this section.*

**__Automatic Farmer Restart (WINDOWS ONLY)__**
If your CapsuleFarmer installation works properly when running the `CapsuleFarmerEvolved.exe `, you can utilize this script to automatically restart the Farmer if it crashes (due login failures & API crashes). 

You do not need need to modify anything. Download this file, and move it to the same directory as the `CapsuleFarmerEvolved.exe`. Close any instances of the Farmer and start the bat file. 

*If you get permission/security warnings, right click on the bat file, go to properties and enable execution.* 
Created by @RustyWalls#9782

```bat
@echo off
set crash=0
:1
echo Starting CapsuleFarmer.exe
CapsuleFarmerEvolved.exe
set /a crash=crash+1
echo Crash detected, Crash #%crash%
echo Waiting 5 seconds. Please Ctrl+C to cancel.
timeout /t 5
goto 1
```

**__Automatic Farmer Restart (LINUX ONLY)__**
This is the same tool as the Automatic Farmer Restart but only for __**Linux Operating Systems**__. :point_left::point_left:

:warning: This **LINUX** script assumes you are using `pipenv run python ./main.py` for running the farmer.
If you are using something else, please modify the command in the script as required. 

To run this script, download it and move it to the same directory as your Farmer installation, ensure you terminate any other processes related to the Farmer and start the file with `./restarter.sh`. Please note you might need to give 'run' permissions to the file by typing the command `sudo chmod 777 ./restarter.sh` (might vary depending on OS)

Created by @Matador#2997
```bash
#!/bin/bash

counter=0

while true; do
  pipenv run python ./main.py
  if [ $? -ne 0 ]; then
    ((counter++))
    echo "Your script crashed with exit code $?. Restarting... (crash count: $counter)" >&2
    sleep 1
  else
    break
  fi
done
```