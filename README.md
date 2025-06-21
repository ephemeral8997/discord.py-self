discord.py-self
===============

![Telegram chat](https://img.shields.io/endpoint?color=neon&url=https%3A%2F%2Ftg.sumanjay.workers.dev%2Fdpy_self)
[Join Telegram](https://t.me/dpy_self)  
![PyPI version info](https://img.shields.io/pypi/v/discord.py-self.svg)
[PyPI](https://pypi.python.org/pypi/discord.py-self)  
![Python versions](https://img.shields.io/pypi/pyversions/discord.py.svg)
![Downloads](https://img.shields.io/pypi/dm/discord.py-self.svg)

A modern, easy to use, feature-rich, and async ready API wrapper for Discord's user API written in Python.

> **Note:**  
> Automating user accounts is against the Discord ToS. This library is a proof of concept and I cannot recommend using it. Do so at your own risk.

## Fork Changes

These changes have become too numerous to mention, so check out our [docs](https://discordpy-self.readthedocs.io/en/latest/index.html).

## Credits

- [Rapptz](https://github.com/Rapptz) for the original library this fork is based on.
- [arandomnewaccount](https://www.reddit.com/user/obviouslymymain123/) for help when the project was first started.

## Key Features

- Modern Pythonic API using `async` and `await`.
- Proper rate limit handling.
- Optimised in both speed and memory.
- Mostly compatible with the upstream `discord.py`.
- Prevents user account automation detection.
- Implements vast amounts of the user account-specific API.

**For a non-exhaustive list:**

- Sessions
- Read states
- Connections
- Relationships
- Experiments
- Protobuf user settings
- Application/team management
- Store/SKUs/entitlements
- Billing (e.g. subscriptions, payments, boosts, promotions, etc.)
- Interactions (slash commands, buttons, etc.)

## Installing

**Python 3.8 or higher is required.**

### Basic install:

```sh
# Linux/macOS
python3 -m pip install -U discord.py-self

# Windows
py -3 -m pip install -U discord.py-self
```

> A [Virtual Environment](https://docs.python.org/3/library/venv.html) is recommended to install the library, especially on Linux.

### With voice support:

```sh
# Linux/macOS
python3 -m pip install -U "discord.py-self[voice]"

# Windows
py -3 -m pip install -U discord.py-self[voice]
```

### Development version:

```sh
git clone https://github.com/dolfies/discord.py-self
cd discord.py-self
python3 -m pip install -U .[voice]
```

### Optional Packages

- [PyNaCl](https://pypi.org/project/PyNaCl/) (for voice support)

On Linux, you also need to install:

- libffi-dev (or `libffi-devel`)
- python-dev (e.g. `python3.6-dev`)

## Using with Upstream

To use the library alongside `discord.py`, you can install `selfcord.py` instead.  
See the [renamed branch](https://github.com/dolfies/discord.py-self/blob/renamed/README.rst) for more info.

## Quick Example

```python
import discord

class MyClient(discord.Client):
    async def on_ready(self):
        print('Logged on as', self.user)

    async def on_message(self, message):
        if message.author != self.user:
            return

        if message.content == 'ping':
            await message.channel.send('pong')

client = MyClient()
client.run('token')
```

## Bot Example

```python
import discord
from discord.ext import commands

bot = commands.Bot(command_prefix='>', self_bot=True)

@bot.command()
async def ping(ctx):
    await ctx.send('pong')

bot.run('token')
```

More examples can be found in the `examples` directory.

## Links

- [Documentation](https://discordpy-self.readthedocs.io/en/latest/index.html)
- [Project updates](https://t.me/dpy_self)
- [Discussion & support](https://t.me/dpy_self_discussions)