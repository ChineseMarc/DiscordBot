# NdT3 Discord Bot

This is my first Discord bot made using [Discord.js](https://github.com/hydrabolt/discord.js).

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/a53801bdb675456da9c9e0f5794d26f5?branch=dev-branch)](https://www.codacy.com/app/NdT3Development/DiscordBot?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=NdT3Development/DiscordBot&amp;utm_campaign=Badge_Grade)

## It currently has these features:
  - Kicking users
  - Banning users
  - Ping command
  - Eval command
  - Purge
  - Say command (says what you tell it to say)
  - Stats
  - Stopping the bot using a command
  - Testing command (Testing, testing, 1 2 3)
  - Change settings command
  - Embed command (basic, using RichEmbed)
  - Deleted message logs
  - Invite link filter
  - Web Dashboard

## Planned features!

  - ~~Music commands~~ I have decided to completely remove the `play` command and remove all future plans for music features (Found issue in [#1](https://github.com/NdT3Development/DiscordBot/issues/1) and given reasons for this decision [here](https://github.com/NdT3Development/DiscordBot/projects/1#card-4201008))

### Installation
First of all, clone this repository.

This bot requires [Node.js](https://nodejs.org/) v8+ (and npm) to run.

Also, please make a channel for mod logs in your Discord server.

Once you have that done, edit the `config.js.example` file and then rename the file to `config.js`. Make sure the callback URL specified is in the format of `{{http|https}}{{domain_name}}/callback` (Examples: `https://dashoard.bot-website.com/callback` OR `http://dashboard.bot-website.com/callback` OR `http://localhost:33445/callback`). This should be the public URL (proxied URL (by something like Nginx) is recommended).

![Bot Application](https://i.imgur.com/sechKvg.png)

### Example Configuration

#### config.js

```javascript
var config = { // NOTE: DO NOT LEAVE ANYTHING BLANK
	// ALL settings are strings. Do NOT just use true or false, use these in strings such as "true" or "false". This is due to how some code works when changing the settings
  "ownerID": "123456789012345678", // Your ID here (or use `process.env.OWNERID`)
  "token": "Mxfxawx-token021kxxmkalpr-m", // Your bot token here (or use `process.env.TOKEN`)
	"status": "dnd", // Bot status [online/idle/invisible/dnd]
	"debug": "false", // This is used to output some debug info if needed. The token will be in the console and other information could be in the console
	"playingGame": "{{prefix}}help | {{guilds}} guilds", // The game you want the bot to play. {{prefix}} is replaced with the default prefix below and {{guilds}} is replaced with the guild count. Leave blank to disable
	"blockConfigEval": "true", // RECOMMENDED TO KEEP THIS SET TO "true"! This setting ensures that you cannot use the eval or exec commands if the eval/exec code contains 'config.js'
  "defaultSettings" : {
    "prefix": "&&&",
    "modLogChannel": "mod-log",
    "modRole": "Moderator",
    "adminRole": "Admin",
    "welcomeChannel": "general",
    "welcomeMessage": "Welcome {{user}}!",
    "welcomeEnabled": "false",
    "inviteFilterEnabled": "false",
    "inviteWhitelist": ["discord-testers", "discord-developers"], // This can be changed, these are just defaults as an example
    "facepalms": "false", // If enabled, the bot will reply with the facepalm emoji whenever a message contains 'facepalm'
    "swearFilter": "false",
    "swearWords": ["damn"], // An array of swear words. These should be lowercase. (of course, I have not included much for certain reasons...)
		"logDeletes": "true",
		"logNewMember": "true",
		"logMemberLeave": "true"
  },
    "dashboard" : {
    "oauthSecret": "0eFle4ArGsecret0sa", // The client secret from the Discord bot page, (you can also store this in an environmental variable)
    "secure": "true", // HTTPS: "true" for true, "false" for false
    "sessionSecret": "-crazyKeyboard-qwaszxerdfcvtyghbnuijkmopl", // Go crazy on the keyboard here, this is used as a session secret, (you can also store this in an environmental variable)
    "domain": "dashboard.bot-website.com", // Similar to the callbackURL above but this is without the protocol
    "port": "33445", // The port that it should run on
		"invitePerm": "470019271",
		"protectStats": "false" // Change this to "true" (with quotes) if you want to require logging in to view /stats
  }
};

module.exports = config;
```

In the config file above, the callbackURL would be set by the code to `https://dashboard.bot-website.com/callback`.

**It is recommended to run the dashboard with a proxy (like Nginx)**

#### Nginx Configuration

```
server {
    listen 80;

    server_name dashboard.bot-website.com;

    location / {
        proxy_pass http://127.0.0.1:33445;
    }
}
```

After that, you can install the dependencies and start the bot

**You can use the command line**
```sh
$ cd DiscordBot
$ npm install
$ npm start
```

**NOTE:** Running the bot with a process manager (like PM2) is recommended.

>This bot must be run on a Discord bot account. Do __NOT__ try to run this on a normal user account. This is against the Discord Terms of Service.

>Also, do __NOT__ play with the `eval` or `exex` command. You have been warned.

## Contributing

Want to contribute?

NdT3 Discord Bot is written in Discord.js. If you want to add a feature or work on the code, make a pull request and if your code is good enough, I will merge the changes.

## Credits

This bot based on AnIdiotsGuide's [example bot](https://github.com/An-Idiots-Guide/guidebot) with the dashboard being based on the one [here](https://idiots-dashboard.glitch.me/) and made using [Discord.js](https://github.com/hydrabolt/discord.js)

## Privacy Policy:

Please read the `PRIVACY.md` file. NOTE: This is for you to know what information the bot will be collecting. No information will be sent to me about the bot in any way.

## License

Please read the `LICENSE` file
