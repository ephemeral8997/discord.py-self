discord.py-self  
===============

![PyPI version info](https://img.shields.io/pypi/v/discord.py-self.svg)  
![Python versions](https://img.shields.io/pypi/pyversions/discord.py.svg)  
![Downloads](https://img.shields.io/pypi/dm/discord.py-self.svg)  

A modern, easy to use, feature-rich, and async ready API wrapper for Discord's user API written in Python.

> **Note:**  
> Automating user accounts is against the Discord ToS. This library is a proof of concept and I cannot recommend using it. Do so at your own risk.

## Fork Notice

This is a **personal fork**: [`ephemeral8997/discord.py-self`](https://github.com/ephemeral8997/discord.py-self)  
**Build:** `exact-build` — based on a version prior to the shift from `aiohttp` to `cffi`.

Created primarily for **personal use**, but contributions via pull requests or issues are absolutely welcome.

## Key Features

- Modern Pythonic API using `async` and `await`.
- Proper rate limit handling.
- Optimised in both speed and memory.
- Mostly compatible with the upstream `discord.py`.
- Prevents user account automation detection.
- Implements vast amounts of the user account-specific API.

**Includes but not limited to:**

- Sessions  
- Read states  
- Connections  
- Relationships  
- Experiments  
- Protobuf user settings  
- Application/team management  
- Store/SKUs/entitlements  
- Billing (subscriptions, payments, boosts, promotions, etc.)  
- Interactions (slash commands, buttons, etc.)

## Installing

**Python 3.8 or higher is required.**

### Basic install:

```sh
# Linux/macOS
python3 -m pip install -U git+https://github.com/ephemeral8997/discord.py-self.git@exact-build

# Windows
py -3 -m pip install -U git+https://github.com/ephemeral8997/discord.py-self.git@exact-build
```

> A [Virtual Environment](https://docs.python.org/3/library/venv.html) is recommended, especially on Linux.

### With voice support:

```sh
# Linux/macOS
python3 -m pip install -U "git+https://github.com/ephemeral8997/discord.py-self.git@exact-build#egg=discord.py-self[voice]"

# Windows
py -3 -m pip install -U git+https://github.com/ephemeral8997/discord.py-self.git@exact-build[voice]
```

### Development version:

```sh
git clone --branch exact-build --single-branch https://github.com/ephemeral8997/discord.py-self.git
cd discord.py-self
python3 -m pip install -U .[voice]
```

### Optional Packages

- [PyNaCl](https://pypi.org/project/PyNaCl/) (for voice support)

On Linux, you may also need:

- `libffi-dev` (or `libffi-devel`)  
- `python-dev` (e.g. `python3.6-dev`)

## Using with Upstream

To use this library alongside `discord.py`, you can install `selfcord.py` instead.  
Refer to the [renamed branch](https://github.com/ephemeral8997/discord.py-self/blob/renamed/README.rst) for compatibility details.

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
- [Original Project (dolfies)](https://github.com/dolfies/discord.py-self)
