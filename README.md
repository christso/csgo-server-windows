# Guide for Hosting a CS:GO Dedicated Server on Windows

## Instructions

Download [csgosl - a CSGO GUI frontend for Windows/Linux](https://github.com/lenosisnickerboa/csgosl/releases).

Extract the zip file into your C drive.

Run csgosl.bat to start the CSGO GUI.

Click on `Install server`. This will download the files for running the CSGO server. After installation is complete, click on Restart Server.

Refer to the [wiki](https://github.com/lenosisnickerboa/csgosl/wiki) on how to configure after installation.

Create your Steam Token in [Steam Game Server Account Management](https://steamcommunity.com/dev/managegameservers).

![game-server-token](/images/game-server-token.png)

If you get a "limited user account" error, you may need to add $5 to your steam wallet and wait a couple of days.

In your router, add port forwarding protocol TCP/UDP and 27015 to the LAN IP address of your service. You may need to reboot your router.

In your server app, go to the Steam tab. Enter your username and steam ID. You can get your steam ID using [Steam Finder](www.steamidfinder.com).

In the Server tab:
* enable rcon and set a password.
* untick lanonly
* leave the port as 27015 so it is the same as router

Here are some optional settings I use:
* Run > gamemodetype = Deathmatch Team vs Team
* Run > players = 32
* Run > bots = 0

If you connect via the external IP address, your client needs to be connected to a different network from your LAN.

## Troubleshooting

**I cannot connect to the server via external IP address**:

Try to connect to the server using the LAN IP address. If that works, then it's a problem with your firewall or router. Try disabling your firewall. If that works, then you should add a rule to allow srcds access. When you first start the server, Windows should automatically ask you whether to add the firewall configuration. If you clicked Yes, then the firewall rule should already be added.

If it's not a firewall problem, then check that you are connecting via another ISP.

Otherwise, you can use an online port scanner tool such as [yougetsignal's open-ports](https://www.yougetsignal.com/tools/open-ports/) to check your port is opened. The port should be closed when the CSGO server is not running, and it should be open once the CSGO server is running.

**I start the server, but it unexpectedly quits at the end**

The server (srcds.exe) will close if the Steam Token is invalid or expired. You may need to create a new token in [Steam Game Server Account Management](https://steamcommunity.com/dev/managegameservers).