A relatively simple integration of IMAP into [Capsule Farmer Evolved](https://github.com/LeagueOfPoro/CapsuleFarmerEvolved), to automate 2FA.

This is by no means currently built to accept all IMAP connections, and was designed to support most modern email providers. In the future this may potentially allow for all IMAP connections, regardless of security, but for the current build it only supports connections via SSL.

By `Skribb11es#0001`. Tested using Gmail.

# IMPORTANT!
Do note that by using automatic IMAP integration you are allowing the farmer to gain access to your email account for a brief period, this means that some emails, primarily if they are received during the time that the farmer is monitoring, will be "scanned". This means that the email will be marked as read, and the sender of the email processed. While this is as far as the farmer will go unless the email is from `noreply@mail.accounts.riotgames.com`, it does mean that you consent to give the farmer access to potentially private information.

Please understand that **NONE** of the information processed, during the period the farmer has access to your email, will be processed **anywhere** outside of **your computer**.

By `Skribb11es#0001`. Tested using Gmail.

# Setup
It is recommended that you use the [Config Helper](https://leagueofporo.com/confighelper.html), both for ease of use and because it makes configuring the farmer much easier to understand where and how to input the information.

Otherwise, we recommend using a dedicated text editor like [Notepad++](https://notepad-plus-plus.org/) or [Visual Studio Code](https://code.visualstudio.com/) in place of something like Notepad.

## How to find IMAP information
Almost every email provider has different policies when it comes to IMAP, for the sake of keeping this guide simple we are unable to list all the possible ways to set up IMAP for your email provider. However, if you need to locate this information, we highly recommend searching for "**[EMAIL PROVIDER HERE]** IMAP docs". This in almost all cases will provide you with official docs on how you can both enable and access IMAP in a different application, along with some more extensive configuration information.

As it stands, only Gmail is verified to work with the IMAP integration, if you encounter an issue with your particular email provider, please verify that the information you are inputting is correct and that you don't require any further security measures (in the case of Gmail you must use a dedicated App Password, and have 2FA enabled on your Google account). If you are still encountering an issue, please contact me `Skribb11es#0001` on Discord.

## Option 1 - Adding IMAP via Config Helper
You can use the config helper tool via the link provided [here](https://leagueofporo.com/confighelper.html), to create your config. Further information on how to locate the needed information can be found in the following steps below.

Assuming you have already made a config for your accounts and are looking to add automatic 2FA, it is recommended that you copy over all of the information for the accounts into the provided default fields (non-IMAP related fields), and then follow through with IMAP. For more information, please reference [App Configuration](Configuration).

1. Input your IMAP username and password into their respective fields `IMAP Username: (OPTIONAL)` and `IMAP Password: (OPTIONAL)`. If you are unsure what either of these may be, consult the documentation provided by your email service for IMAP logins. In most cases, it is your full email address + your account password (the password you use when you log in to your inbox). In the case of a more secure service like Gmail, it may be required for you to provide an App Password, instead of your default account password.

2. Locate the IMAP server for your email provider, this is usually located in the same docs as referenced above, and will be input into the `IMAP Server: (OPTIONAL)` field. Assuming the email provider you are using supports SSL connections this should be the end of your configuration.

3. Click **ADD ACCOUNT** once all the fields are filled out, and download or otherwise save the created config to the `config.yaml` file located in `./config/config.yaml`.

## Option 2 - Adding IMAP manually
If you are a more technical user, or just find it easier to add the necessary fields yourself you can do so by following the steps below.

1. Open `config.yaml` using your text editor of choice (ex. [Notepad++](https://notepad-plus-plus.org/))

2. Under each of the accounts you have set up add the following fields: 
```yaml
imapUsername: ""
imapPassword: ""
imapServer: ""
```
In total you should have something that resembles the following :
```yaml
accounts:
  accountname:
    username: ""
    password: ""
    imapUsername: ""
    imapPassword: ""
    imapServer: ""
```

3. Following the table below, fill out the new fields with their according information.

| Option | Description | Example | Default | Is required? |
| --- | --- | --- | --- | --- |
| `imapusername` | The specified username for logging in with IMAP according to the email provider's docs | thisisanexample@gmail.com | "" | Yes
| `imappassword` | The specified password for logging in with IMAP according to the email provider's docs | Password! | "" | Yes
| `imapserver` | The specified server to connect to according to the email provider's docs |imap.gmail.com | "" | Yes

Make sure to replace all variable values and to leave none blank, as this leaves potential for error, and the possibility that the farmer is not able to log into your IMAP account.

4. Save the config file and run the program.

# What to expect
Below is a list of possible outcomes when running the program after configuring IMAP. If you run into one of the listed errors, please consult the above guide again.
## Normal Operation
If you have properly configured all of the fields, the farmer will go ahead and log in to your Riot account via the specified username and password, at which point it will send a request to the specified IMAP server to log in. It will then wait until a new email is received, upon which it will check if the sender was `noreply@mail.accounts.riotgames.com`, and if it is then it will extract the 2FA code from the email's subject and store it. It will then close the IMAP session and log out, at which point it will then send the saved code to Riot's authentication servers, and log your account in. During this process, the status will only display `WAIT`. After the code has been fetched, the status will update to `LOGIN` and then `FETCHED 2FA CODE`, at which point it may stall for a little while it logs into the Riot servers. Once completed it will display `LIVE` next to the account name, and you should be fully up and running. 

## Failure to find 2FA code
In the case that a 2FA code was unable to be found by the farmer (this information is only displayed in the logs `./logs/capsulefarmer.log`), the farmer will retry after the allotted period, and attempt to find a 2FA code again. If you find that the farmer is consistently unable to find a 2FA code, please make sure that you are not blocking emails from Riot, and that you are using the correct email account for the specified Riot account. 


## Failure to log in 
If an error occurs logging into your email account via IMAP, the farmer will display `IMAP LOGIN FAILED` as the status, along with automatically stopping itself from ever retrying to log back into your Riot account, or email account, until you verify that your information is correct and restart the program. This is to insure that your account is not locked down due to multiple login requests without providing a 2FA code. 

