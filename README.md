# discord_moderator.py
# discord_moderator.py
import discord
from discord.ext import commands

intents = discord.Intents.default()
intents.messages = True
intents.guilds = True

bot = commands.Bot(command_prefix='!', intents=intents)

# List of banned words
banned_words = ["badword1", "badword2"]

@bot.event
async def on_ready():
    print(f'Logged in as {bot.user}')

@bot.event
async def on_message(message):
    if message.author == bot.user:
        return
    for word in banned_words:
        if word in message.content.lower():
            await message.delete()
            await message.channel.send(f"{message.author.mention}, that word is not allowed!")
    await bot.process_commands(message)

# Example command
@bot.command()
async def ping(ctx):
    await ctx.send("Pong!")

# Run the bot
bot.run("YOUR_BOT_TOKEN")
# Discord Auto-Moderation Bot

This bot automatically deletes messages containing banned words and allows simple commands like !ping.

## Features
- Automatic moderation of bad words
- Simple command support
- Easy to set up

## Setup
1. Install Python 3.11+ and pip
2. Install dependencies:

3. Replace `"YOUR_BOT_TOKEN"` in `discord_moderator.py` with your Discord Bot Token
4. Run the bot:

## Pricing
💰 Want the full version with advanced features like:
- Customizable banned word list
- Auto-welcome new members
- Logging deleted messages

**Pay $10 via [Cashap](freddycuka5) and get the premium version immediately!**

---

DM me after payment and I’ll send you the full version.
