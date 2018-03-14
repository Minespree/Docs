# Connecting to MongoDB databases

To follow this manual you need to have installed Robo3T. If you haven't, please check the [Required Dependencies](DEPENDENCIES.md) document.

Once you open Robo3T you will be greeted with a "Connections" panel where you will have to create a connection. Please click the "Create" button and the select the following options on the "Connection" tab:

| Variable | Value             |
| -------- | ----------------- |
| Type     | Direct Connection |
| Name     | Minespree DEV01   |
| Address  | REDACTED          |

Now, switch to the authentication tab, and fill in the following details:

| Variable               | Value             |
| ---------------------- | ----------------- |
| Perform Authentication | (true)            |
| Database               | feather           |
| User Name              | (Read info below) |
| Password               | (Read info below) |
| Auth Mechanism         | SCRAM-SHA-1       |

Depending on whether you want to connect to the main network or the dev network MongoDB database, you will need a different pair of credentials. You can find both of them on the "Mongo Details" section on the `#important-files-and-data` channel on Discord. The `REDACTED` user is for the main network and the `REDACTED` user is for the dev network. Please name your connections properly to avoid changing/losing production data when trying to test something on the dev network.

We will now setup the SSH tunnel connection on the "SSH" tab:

| Variable        | Value                                                    |
| --------------- | -------------------------------------------------------- |
| Use SSH tunnel  | (true)                                                   |
| SSH Address     | REDACTED                                                 |
| SSH User Name:  | Your username                                            |
| SSH Auth Method | Private Key                                              |
| Private key     | Select your SSH private key                              |
| Passphrase      | If your SSH key has a passphrase, please fill it in here |

Remember that other services such as PlayPen need a manually setup SSH tunnel. You can learn more about how to set it up on the [Setting up SSH tunnels](SSH_TUNNELS.md) document. You can now click the "Test" button to ensure the connection is working and finally save it. Depending on whether you connected to the dev network or the production MongoDB database, you will see a different database name (`featherdev` is for the dev network and `feather` is for production).

## Helpful tips

* If you want to run a complex query to migrate some data, we recommend writing a `Migration` class on the [`Migrations`](https://github.com/Minespree/UpdateMongoClient) project on GitLab. You can check how this project works on its [README](https://github.com/Minespree/UpdateMongoClient/blob/master/README.md) file.
* If you're having issues when trying to connect to any MongoDB database, please check the SSH details are correct, you provided the right private key and all the addresses are right.
