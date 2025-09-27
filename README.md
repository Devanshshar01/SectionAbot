# WhatsApp Tag Bot

A powerful WhatsApp bot built with Node.js that allows group administrators to tag all members in a group with a simple command. Perfect for announcements, important messages, or group notifications.

## Features

- 🏷️ **Tag All Members**: Mention all group participants with a single command
- 👑 **Admin Management**: Add and remove bot administrators dynamically
- 🔒 **Permission Control**: Only group admins and bot admins can use tag commands
- 📱 **QR Code Authentication**: Easy setup with WhatsApp Web QR code scanning
- ⚡ **Large Group Support**: Automatically handles large groups by chunking mentions
- 🛡️ **Error Handling**: Robust error handling and user feedback
- 💬 **Help System**: Built-in help command for users

## Commands

| Command | Description | Permission Required |
|---------|-------------|-------------------|
| `!tagall` | Tag all members in the group | Group Admin or Bot Admin |
| `!help` | Show available commands | Anyone |
| `!addadmin` | Add a new bot admin (reply to user's message) | Main Admin Only |
| `!removeadmin` | Remove a bot admin (reply to user's message) | Main Admin Only |

## Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- WhatsApp account

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/whatsapp-tag-bot.git
   cd whatsapp-tag-bot
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure admin numbers**
   
   Open `whatsapp-tagbot-fixed.js` and update the admin numbers in the constructor:
   ```javascript
   this.adminNumbers = ['919643355581']; // Replace with your phone numbers
   ```
   
   **Note**: Use phone numbers with country code but without the + sign.

4. **Run the bot**
   ```bash
   node whatsapp-tagbot-fixed.js
   ```

5. **Authenticate with WhatsApp**
   
   - A QR code will appear in your terminal
   - Scan it with your WhatsApp mobile app
   - Wait for the "WhatsApp Bot is ready!" message

## Usage

1. Add the bot account to your WhatsApp groups
2. Group admins can use `!tagall` to mention all members
3. Use `!help` to see available commands
4. Main admins can manage bot admins using `!addadmin` and `!removeadmin`

## Configuration

### Admin Management

- **Main Admins**: Defined in the `adminNumbers` array in the constructor
- **Dynamic Admins**: Can be added/removed using `!addadmin` and `!removeadmin` commands
- **Group Admins**: WhatsApp group administrators automatically have permission to use `!tagall`

### Chunking for Large Groups

The bot automatically splits large groups into chunks of 20 mentions per message to avoid WhatsApp's limits. You can adjust this by modifying:

```javascript
this.MENTION_CHUNK_SIZE = 20; // Change this value as needed
```

## Dependencies

```json
{
  "whatsapp-web.js": "^1.21.0",
  "qrcode-terminal": "^0.12.0"
}
```

## Project Structure

```
whatsapp-tag-bot/
├── whatsapp-tagbot-fixed.js    # Main bot file
├── package.json                # Project dependencies
├── README.md                   # This file
└── .session/                   # WhatsApp session data (auto-generated)
```

## Troubleshooting

### Common Issues

**QR Code not appearing**
- Ensure your terminal supports Unicode characters
- Try running with `--no-headless` flag

**Authentication failed**
- Delete the `.session` folder and restart the bot
- Make sure you're scanning with the correct WhatsApp account

**Bot not responding to commands**
- Verify the bot account is added to the group
- Check that commands start with `!` (exclamation mark)
- Ensure the user has proper permissions

**Large groups not working**
- The bot automatically handles this with chunking
- If issues persist, reduce `MENTION_CHUNK_SIZE`

## Security Notes

- Never share your session files (`.session` folder)
- Keep your admin phone numbers private
- Regularly review bot admin list
- Use the bot responsibly to avoid WhatsApp restrictions

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Create a Pull Request


## Disclaimer

This bot uses WhatsApp Web interface and is not officially affiliated with WhatsApp. Use responsibly and in accordance with WhatsApp's Terms of Service.

## Support

If you encounter any issues or have questions, please open an issue on GitHub.

---

**Made with ❤️ for better group communication**