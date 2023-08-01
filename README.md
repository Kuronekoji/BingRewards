<h1 align="center">📊 Bing Rewards Automation 🤖 </h1>

<p align="center">An <i>awesome</i> Python script to automate bing searches, quizzes, polls, and more across multiple Bing Reward accounts.</p>

<p align="center"> 
        <img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54"/><img src="https://img.shields.io/badge/-selenium-%43B02A?style=for-the-badge&logo=selenium&logoColor=white"/><img src="https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white"/>
</p>

## Fork Updates 

After the repository was archived, webdriver-manager was updated, rendering this script temporarily useless. I fixed the issue for Chrome but haven't tested it with Edge and Firefox yet. If there's demand for those features in the future, I'll look into it. Enjoy the upcoming updates!

## Features

- Multiple Bing Rewards Accounts
- Multi-Threading (Optional)
- PC & Mobile Search Automation
- Bing Quiz, Poll, and Explore Automation
- Quests / Punchcard Automation
- 'More Activities' Automation
- Proxy Support
- Locked Account Handling
- Auto-Redemption
- Apprise Alerts
- Streak Notifications
- Suspended Account Notifications
- USD ($) & EURO (€) Currency Conversions (More coming)
- Semi-International Accommodations/Support
- Incorrect Account Credentials Detection
- Docker Support & DockerQuickstart.bat 
- Headless Option

## Installation
The bot can be run using Python or Docker.

### Python Script
Run locally:
1. Clone this repository, cd into it, and install dependancies:
```sh
   git clone https://github.com/Prem-ium/BingRewards.git
   cd BingRewards
   pip install -r requirements.txt
   ```
2. Rename `.env.example` to `.env` and configure your `.env` file (See below and example for options)
3. Run the script:
```sh
   python main.py
```
I personally use PM2 to run the python script. Download and read more at: [PM2](https://pm2.keymetrics.io)

To run the python script in PM2:

1. Do exactly as above but instead open a cmd where main.py is stored
2. Run the script through pm2 if you have installed it correctly:
```pm2 start main.py
```
3. Run the logs command to see the script output:
```pm2 logs
```
4. If you would like to stop the script run:
```pm2 stop main.py
```

### Docker Container
View on [Docker Hub](https://hub.docker.com/repository/docker/nelsondane/bing-rewards)
1. Download and install Docker on your system
2. Configure your `.env` file (See below and example for options)
3. To start the bot using our prebuilt images:
 ```sh
   docker run -it --env-file ./.env --restart unless-stopped --name bing-rewards nelsondane/bing-rewards:<tag>
   ```
   To build the image yourself, cd into the repository and run:
   ```sh
   docker build -t bing-rewards .
   ```
   Then start the bot with:
   ```sh
   docker run -it --env-file ./.env --restart unless-stopped --name bing-rewards bing-rewards
   ```
   Both methods will create a new container called `bing-rewards`. Make sure you have the correct path to your `.env` file you created.

4. Let the bot log in and begin working. DO NOT PRESS `CTRL-c`. This will kill the container and the bot. To exit the logs view, press `CTRL-p` then `CTRL-q`. This will exit the logs view but let the bot keep running.

You can also open `DockerQuickstart.bat` in a text editor, edit the exisitng path in the file with your own of the BingRewards folder directory and run it to quickly stop and start docker container instances. 

## Environment Variables:

To run this project, you will need to add the following environment variables to your `.env` file. Refer to `.env.example` for further clarification.

### Required Variables:

| Variable  | Description                                                                                                                     |
|-----------|---------------------------------------------------------------------------------------------------------------------------------|
| `LOGIN`   | A string of Bing Rewards login information. Email and Password are separated using a colon and accounts are separated using commas. Check `.env.example` for an example. |
| `URL`     | Sign in link obtained through https://bing.com/                                                                                 |

### Optional Variables:

| Variable              | Description                                                                                                                     |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------|
| `HANDLE_DRIVER`       | Boolean (True/False) variable based on whether a user wants webdriver to be installed for them. Defaultly set to True.           |
| `BROWSER`             | `chrome`, `edge`, or `firefox` -- Browser you'd like to use the bot with. In experimental mode. `HANDLE_DRIVER` must be set to True to use. Defaults to `chrome`. |
| `HEADLESS`            | True or False -- Whether the program should run headless or not. Defaults to False.                                            |
| `MULTITHREADING`      | 'True' or 'False' -- Whether the program should run multiple threads to run all accounts at once or not. Defaults to False.     |
| `DELAY_SEARCH`        | Integer value of how long the program should wait between making searches.                                                       |
| `APPRISE_ALERTS`      | Notifications and Alerts. See .env example for more details.                                                                    |
| `KEEP_ALIVE`          | True or False -- Whether you wish to use Flask Threading or not.                                                                |
| `AUTO_REDEEM`         | Handle auto redemption of rewards (checks goal). Amazon is chosen as default.                                                   |
| `SHOPPING`            | True or False -- Attempts to complete a new shopping quiz (Experimental).                                                      |
| `GOAL`                | Selecting goal reward, defaults to Amazon.                                                                                      |
| `AUTOMATE_PUNCHCARD`  | True or False -- Whether bot should automate punchcards.                                                                        |
| `SKIP_MOVIES_AND_TV_PUNCHCARD` | True or False -- Whether the bot should skip the punchcard for Movies and TV shows.                                         |
| `CURRENCY`            | Currency Symbol or Name, currently only supported by USD($), EURO(€) and INR(₹). Defaults to USD.                             |
| `BOT_NAME`            | Bot name, helpful for multiple instances of the bot running with proxy.                                                        |
| `TZ`                  | Your desired Time-Zone. Should be formatted from the [IANA TZ Database](https://www.iana.org/time-zones). Defaults to `America/New York`. |
| `TIMER`               | True or False -- Whether you wish for the program to only run between certain time period.                                      |
| `START_TIME`          | 24 hour format hour you would like to start the program, if timer is enabled. Defaults to 4, 4 AM.                              |
| `END_TIME`            | 24 hour format hour you would like to start the program, if timer is enabled. Defaults to 19, 7 PM.                             |
| `POINTS_PER_SEARCH`   | Amount of points per search rewards in your country. Used to calculate the number of searches needed for maximum points. Defaults to 5. |
| `WANTED_IPV4`         | Your desired external IPv4 address. Set this if you want the bot to not run if your IPv4 address is different than this.         |
| `WANTED_IPV6`         | Your desired external IPv6 address. Set this if you want the bot to not run if your IPv6 address is different than this.         |
| `PROXY`               | Configure a HTTP(S) or SOCKS5 proxy through which all of the bot's traffic will go. Should be in a URI format (e.g., https://1.2.3.4:5678). |
| `DEBUGGING`           | True or False -- Whether you wish to log the bot's error and stacktrace. Defaults to False.                                    |
| `DAILY_SETS`          | True or False -- Whether you wish to complete daily sets, this feature is unavailable in a few markets like India. Defaults to True. |

## Earning Potential:
The following is a conservatively prediction of potential points/earnings per month using this bot w/ lvl 2 account:

PC Searches: (150 * 30) = 4500

Mobile Searches: (100 * 30) = 3000

Edge Bonus: (20*30) = 600

Daily Sets: (30*30) = 900


This adds up to 9000 points, conservatively (not accounting for streak bonuses or more activities which usually net very high, random amount of points), which ends up being a minimum of $6.92/per month per account on level 2. $41.52/ per month with an instance of 6 conncurrent level 2 reward accounts.

ONLY USE 5 ACCOUNTS PER IP

## License & Contributing

This repository is using the [MIT](https://choosealicense.com/licenses/mit/) license.

If you are a developer who wishes to contribute to this repository, please make a pull-request and request a review when ready for a review. [A special thanks to all those who have contributed to this project.](https://github.com/Prem-ium/BingRewards/graphs/contributors)

## Notes:

- This bot uses the new $1.00 = 1300 points conversion rate, which is standard for most US based Bing accounts. Older Bing Reward accounts may have the old conversion rate of $1.00 = 1050 points. As well as €1.00 = 1500 points conversion rate for Euro based Bing Reward accounts.
- As always, use this bot at your own risk. No developer or contributor to this repository is responsible for any financial or account suspension you may suffer.
