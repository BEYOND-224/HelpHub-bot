# HelpHub-bot
The officail discord bot for helphub
import discord, discord.app_commands as app_commands

intents = discord.Intents.default()
client = discord.Client(intents=intents)
tree = app_commands.CommandTree(client)


@client.event
async def on_ready():
    await tree.sync(guild=discord.Object(id=1067180984329580584))
    print("unknown br")


@tree.command(
    name="announce",
    description="announce br",
    guild=discord.Object(id=1067180984329580584),
)
async def announce(
    int: discord.Interaction, channel: discord.TextChannel, message: str
):
    if not channel.permissions_for(int.user).send_messages:
        int.response.send_message("n permission br")
    sent_message = await channel.send(message)
    await int.response.send_message(sent_message.jump_url, ephemeral=True)

@tree.command(
    name="announce_embed",
    description="announce embed br",
    guild=discord.Object(id=1067180984329580584),
)
async def announce_embed(
    int: discord.Interaction,
    channel: discord.TextChannel,
    message: str,
    title: str = "",
    colour: app_commands.Range[int, 0x000000, 0xFFFFFF] = 0x000000,
):
    if not channel.permissions_for(int.user).send_messages:
        int.response.send_message("n permission br")
    embed = discord.Embed(description=message, title=title, colour=discord.Colour(colour))
    sent_message = await channel.send(embed=embed)
    await int.response.send_message(sent_message.jump_url, ephemeral=True)


if __name__ == "__main__":
    client.run(
        "MTA3NDAxMTI3MzY3MjUyMzkxNg.G3Q4TL.Fo_pzrxoQyhMiMWK1C74TNyVNs1Xwjk9fWkwVE"
    )
