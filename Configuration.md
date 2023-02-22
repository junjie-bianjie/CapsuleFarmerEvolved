Before using the program, you need to configure it. The configuration file is located in the same folder as the executable. The file is called `config.yaml`. If it does not exist, the program will automatically create it and generate some dummy data. 

We recommend editing the file with a text editor like Notepad++ or Visual Studio Code. Notepad will work, but it is not recommended.

## Option 1 - Create a config file from a website

You can use our configuration helper tool located here: https://leagueofporo.com/confighelper.html. The website will generate the file as required by the program and you can download it. Extract the file into the same folder as the executable and rename it to `config.yaml` if it's not already. You can then run the program.

## Option 2 - Create a config file manually

If you want to create the file manually, you can do so by following the steps below:

1. Open the `config.yaml` file in a text editor (e.g. Notepad++) 

2. Delete the contents of the file

3. Copy the following code into the file: (make sure to keep the indentation)

```yaml
accounts:
  accountname:
    username: ""
    password: ""
```

4. Replace `accountname` with the display name you want to use for your accounts. It does not have to be the same as the username or the in-game name. 

4b. You can add as many accounts as you want. Simply copy the following code and paste it below the previous account:
```yaml
  accountname:
    username: ""
    password: ""
```

Make sure to replace `accountname` with a unique name for each account. Example of 3 accounts:
```yaml
accounts:
  account1:
    username: ""
    password: ""
  account2:
    username: ""
    password: ""
  account3:
    username: ""
    password: ""
```

5. Replace `username` and `password` with your username and password of each account you have added. Make sure to put the username and password inside the quotation marks. The username and password are the same as the ones you use to login to the Riot client and the lolesports website. If your username or password contains special characters, it is recommended to change them, if you are facing trouble logging in. Special characters that we know have no issues are: `!@#$%^&*`. 

6. Configure any other options as desired. You can find the full list of options below.

7. Save the file and run the program.


## Configuration options

The following options are available in the configuration file:

| Option | Description | Default | Is required? |
| --- | --- | --- | --- |
| `accounts` | A list of accounts to use. | n/a | Yes |
| `accounts.<accountname>.username` | The username of the account. | n/a | Yes |
| `accounts.<accountname>.password` | The password of the account. | n/a | Yes |
| `debug` | Whether to enable debug mode. Prints more information for troubleshooting in the console and log files. | `false` | No |
| `connectorDropsUrl` | Discord WebHook URL for drops and notifications | "" | No |
| `showHistoricalDrops` | Shows the total drops per account. | `true` | No |

The following options are planned for future releases (CURRENTLY UNSUPPORTED):
| Option | Description | Default | Is required? |
| --- | --- | --- | --- |
| `bestStreamsUrl` | URL to fetch the bestStreams file. | `""` | No |
| `connectorOnDrop` | Whether to enable drops and notifications | `true` | No |
| `connectorOnStart` | Send a webhook when the program starts | `false` | No |
| `connectorOnFault` | Send a webhook when the program stops | `false` | No |
| `notificationOnStart` | Whether to show a toast notification when the program starts and has logged into an account. | `false` | No |
| `notificationOn2FA` | Whether to show a toast notification when an account needs 2FA input. | `false` | No |
| `notificationOnDrop` | Whether to show a toast notification when a drop is found. | `false` | No |
| `notificationOnFault` | Whether to show a toast notification when the program stops. | `false` | No |
| `soundPath` | Path to the sound file to play.* | `""` | No |
| `soundOnStart` | Whether to play a sound when the program starts and has logged into an account.* | `false` | No |
| `soundOn2FA` | Whether to play a sound when an account needs 2FA input.* | `false` | No |
| `soundOnDrop` | Whether to play a sound when a drop is found.* | `false` | No |
| `soundOnFault` | Whether to play a sound when the program stops.* | `false` | No |

\* Sounds will only play if the `soundPath` option is set to a valid path to a sound file and the respective `notificationOnX` option is set to `true`.