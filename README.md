# DisLink
DisLink is a powerful Discord bot extension that creates global server hubs where multiple servers can share messages in a common chat space. Unlike traditional channel connections, DisLink allows servers to join themed hubs where all messages are shared among all participating servers.
> 💡 **Built for the Zygnal Ecosystem — to download and use this extension, you must be part of the Zygnal Ecosystem.**  
> This extension (cog) is part of the **Zygnal Ecosystem** and is only available through its supported platforms.  
> You can use it with:  
> - The **[Discord Bot Framework](https://github.com/TheHolyOneZ/discord-bot-framework)** — ideal for developers who want full control and flexibility *(includes an integrated extension marketplace)*, or  
> - The **[ZygnalBot](https://zygnalbot.de)** — a prebuilt, plug-and-play Discord bot *(also includes an integrated extension marketplace)*.  
>
> Browse and install extensions at [zygnalbot.com/extension](https://zygnalbot.com/extension).  
> For help or community discussions, join us on Discord: [discord.gg/sgZnXca5ts](https://discord.gg/sgZnXca5ts)
# DisLink - Global Server Hub Extension

## Overview

DisLink is a powerful Discord bot extension that creates global server hubs where multiple servers can share messages in a common chat space. Unlike traditional channel connections, DisLink allows servers to join themed hubs where all messages are shared among all participating servers.

## Features

- **Global Server Hubs**: Create public or private hubs that multiple servers can join
- **Custom Server Identifiers**: Each server appears with a custom display name in the hub
- **Content Filtering**: Filter NSFW content and specific words from messages
- **Permission Management**: Different commands require different permission levels
- **Public & Private Modes**: Create open hubs or invitation-only private hubs

## Setup Instructions

1. **Installation**:
   - Place the `DisLink.py` file in your bot's `Extensions` folder
   - The extension will automatically create necessary configuration files:
     - `dislink_config.json`: General configuration
     - `dislink_hubs.json`: Hub and server link data

2. **Bot Permissions**:
   - Ensure the bot has the following permissions in all servers:
     - Read/Send Messages
     - Embed Links
     - Manage Messages (recommended)
     - Read Message History

3. **First-time Setup**:
   - Create a hub using `!dislink create` or join an existing hub with `!dislink join`
   - Configure hub settings as needed

## Command Reference

### Basic Commands

| Command | Description | Required Permission |
|---------|-------------|---------------------|
| `!dislink` | Shows help information and available commands | Manage Channels |
| `!dislink create <name> <description>` | Creates a new hub with the specified name and description | Administrator |
| `!dislink join <hub_id> [display_name]` | Joins an existing hub with optional custom display name | Manage Channels |
| `!dislink leave` | Leaves the current hub | Manage Channels |
| `!dislink list` | Lists all available public hubs | None |
| `!dislink info` | Shows information about the current hub | None |
| `!dislink delete` | Deletes a hub (hub owner only) | Administrator |

### Settings Management

| Command | Description | Required Permission |
|---------|-------------|---------------------|
| `!dislink settings` | Shows available settings commands | Administrator |
| `!dislink settings name <new_name>` | Changes the hub name | Administrator (hub owner) |
| `!dislink settings description <new_description>` | Changes the hub description | Administrator (hub owner) |
| `!dislink settings visibility <public/private>` | Changes hub visibility | Administrator (hub owner) |
| `!dislink settings nsfw <enable/disable>` | Toggles NSFW filtering | Administrator (hub owner) |
| `!dislink settings displayname <new_name>` | Changes your server's display name in the hub | Manage Channels |

### Word Filtering

| Command | Description | Required Permission |
|---------|-------------|---------------------|
| `!dislink filter` | Shows available filter commands | Administrator |
| `!dislink filter add <word>` | Adds a word to the filter list | Administrator (hub owner) |
| `!dislink filter remove <word>` | Removes a word from the filter list | Administrator (hub owner) |
| `!dislink filter list` | Lists all filtered words | Administrator |

## Usage Guide

### Creating a Hub

To create a new hub for servers to join:

```
!dislink create "Gaming Community" "A hub for gaming servers to chat and share content"
```

This creates a new hub and automatically links your current channel to it. The server that creates the hub becomes the hub owner with administrative control over hub settings.

### Joining a Hub

To join an existing hub:

1. First, list available hubs:
   ```
   !dislink list
   ```

2. Join a hub using its ID:
   ```
   !dislink join hub_123456789 "My Awesome Server"
   ```

The channel where you run this command becomes the linked channel for the hub. All messages sent in this channel will be forwarded to other servers in the hub.

### Managing Hub Settings

Hub owners can customize various settings:

- Change hub name:
  ```
  !dislink settings name "New Hub Name"
  ```

- Change hub visibility:
  ```
  !dislink settings visibility private
  ```

- Enable NSFW filtering:
  ```
  !dislink settings nsfw enable
  ```

### Word Filtering

Hub owners can filter specific words:

- Add words to filter:
  ```
  !dislink filter add badword
  ```

- Remove filtered words:
  ```
  !dislink filter remove badword
  ```

- View all filtered words:
  ```
  !dislink filter list
  ```

### Leaving or Deleting a Hub

- To leave a hub:
  ```
  !dislink leave
  ```

- To delete a hub (hub owner only):
  ```
  !dislink delete
  ```
  This will require confirmation and will disconnect all servers from the hub.

## Best Practices

1. **Choose Appropriate Channels**: Link channels specifically created for cross-server communication to avoid confusion.

2. **Set Clear Rules**: Establish guidelines for hub participants about appropriate content.

3. **Use Display Names Wisely**: Choose display names that clearly identify your server to other participants.

4. **Configure Filters**: Use word filtering to maintain a positive environment, especially in public hubs.

5. **Regular Maintenance**: Periodically review hub members and settings to ensure everything is functioning as expected.

## Troubleshooting

- **Messages Not Appearing**: Ensure the bot has proper permissions in both the source and target channels.

- **Can't Join Hub**: Verify the hub ID is correct and that the hub is public or you have been invited.

- **Settings Not Saving**: Check that the bot has write permissions for its configuration files.

- **Permission Errors**: Ensure users have the required permissions for the commands they're trying to use.

## Technical Details

DisLink uses a JSON-based storage system to maintain hub configurations and server links. The extension handles message forwarding through Discord's embed system, which preserves formatting and allows for rich content sharing between servers.

The filtering system uses regular expressions to match whole words, and the NSFW filter checks channel flags to prevent inappropriate content from being shared across servers.

## Comparison with DisShare

While DisShare connects individual channels directly in a one-to-one or one-to-many relationship, DisLink creates hub-based communities where:

- Multiple servers join a themed hub
- All messages are shared with all hub members
- Hub owners have central control over settings and filters
- Servers can have custom display names in the hub

This makes DisLink ideal for community networks, partner programs, or topic-based discussion groups across multiple servers.
