# Discord Movie Announcer Bot

A Discord bot that automatically announces and updates users about new movie releases using embedded messages.

## Features

- 🎥 Automatically announces new movie releases in your Discord server
- 🔄 Updates announcements when release dates change
- 👥 Tags members with a specific role for notifications
- 🤖 Slash commands to check for new movies, get status, and more
- 🎬 Search for movie information directly from Discord
- ⚙️ Configure the bot directly from Discord with slash commands

## Commands

- `/announce` - Immediately checks for and announces new movies
- `/help` - Shows the list of available commands
- `/status` - Shows the current bot status
- `/movie [title]` - Search for information about a specific movie
- `/random` - Get a random movie suggestion
- `/random [genre]` - Get a random movie from a specific genre
- `/random [year]` - Get a random movie from a specific year
- `/random [genre] [year]` - Get a random movie from a specific genre and year
- `/badges view` - View your earned achievement badges
- `/badges set [badge_id]` - Set your active badge to display
- `/configure` - Configure bot settings (Admin only)
- `/refresh feed` - Manually refresh the movie announcements feed (Moderator only)
- `/refresh frequency [minutes]` - Change announcement frequency (Moderator only)

## Quick Setup Guide

1. **Create a Discord Bot**:
   - Go to the [Discord Developer Portal](https://discord.com/developers/applications)
   - Create a new application
   - Go to the "Bot" tab and add a bot
   - Under "Privileged Gateway Intents", enable all intents:
     - Presence Intent
     - Server Members Intent
     - Message Content Intent
   - Copy your bot token for later use

2. **Invite the Bot to Your Server**:
   - In the Developer Portal, go to "OAuth2" → "URL Generator"
   - Select the scopes: `bot` and `applications.commands`
   - Bot permissions: `Administrator` (or select specific permissions)
   - Copy and visit the generated URL to invite the bot to your server

3. **Get a TMDB API Key**:
   - Create an account on [The Movie Database](https://www.themoviedb.org)
   - Go to your account settings → API → Request a new API key
   - Fill out the form and get your API key

4. **Configure the Bot**:
   - Set up the `config.json` file (see Configuration section below)
   - Run the bot: `node bot-start.js`
   - Alternatively, run `node deploy-commands.js` to register slash commands
   - Use the `/configure` command in Discord to set up the bot

5. **Use the Bot**:
   - The bot will automatically announce new movies
   - Use `/status` to check if everything is working
   - Use `/movie [title]` to search for movies
   - Use `/announce` to manually trigger announcements
   - Use `/refresh feed` to force refresh movie data (Moderator only)
   - Use `/refresh frequency 15` to change check interval to 15 minutes (Moderator only)

## In-Discord Setup with `/configure`

The easiest way to set up the bot is to use the `/configure` command in Discord:

1. Run the command `/configure`
2. Use the options to set:
   - `channel` - The announcement channel
   - `role` - The role to mention for announcements
   - `interval` - How often to check for new movies (in minutes)
   - `auto_announce` - Enable or disable automatic announcements

Only users with Administrator permissions can use this command.

## Configuration File

The bot can also be configured using the `config.json` file:

```
{
  "token": "DISCORD_TOKEN_PLACEHOLDER",
  "clientId": "YOUR_BOT_CLIENT_ID",
  "guildId": "YOUR_SERVER_ID",
  "tmdbApiKey": "TMDB_API_KEY_PLACEHOLDER",
  "roleId": "ROLE_ID_TO_MENTION",
  "announcementChannelId": "CHANNEL_ID_FOR_ANNOUNCEMENTS",
  "announcementChannelName": "announcements",
  "checkInterval": 10,
  "embedColor": "#0099ff",
  "autoAnnounce": true
}
```

You should replace the placeholder values with your actual Discord token and TMDB API key, or set the environment variables:
- `DISCORD_TOKEN` for your Discord bot token
- `TMDB_API_KEY` for your TMDB API key

## Troubleshooting

- **Bot doesn't respond**: Check that you've enabled the correct intents
- **Can't find role/channel**: Use the `/status` command to see what the bot detects
- **No announcements**: Make sure `autoAnnounce` is set to `true` and `checkInterval` is reasonable

## Deployment

For continuous operation, it's recommended to deploy the bot on a server or hosting platform.

## License

MIT