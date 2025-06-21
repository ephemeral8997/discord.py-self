
discord.py-self
===============

.. image:: https://img.shields.io/endpoint?color=neon&url=https%3A%2F%2Ftg.sumanjay.workers.dev%2Fdpy_self
   :target: https://t.me/dpy_self
   :alt: Telegram chat

.. image:: https://img.shields.io/pypi/v/discord.py-self.svg
   :target: https://pypi.python.org/pypi/discord.py-self
   :alt: PyPI version info

.. image:: https://img.shields.io/pypi/pyversions/discord.py.svg
   :target: https://pypi.python.org/pypi/discord.py-self
   :alt: PyPI supported Python versions

.. image:: https://img.shields.io/pypi/dm/discord.py-self.svg
   :target: https://pypi.python.org/pypi/discord.py-self
   :alt: PyPI downloads per month

A modern, easy to use, feature-rich, and async ready API wrapper for Discord's user API written in Python.

**Note:**  
Automating user accounts is against the Discord ToS. This library is a proof of concept and I cannot recommend using it. Do so at your own risk.

Fork Changes
------------
This fork uses an exact replica of commit `20ae80b3` from the original [`dolfies/discord.py-self`](https://github.com/dolfies/discord.py-self),
which is the last commit to use `aiohttp` before transitioning to `curl-cffi`.  
My goal is to maintain and eventually optimize it beyond all prior limits.

Check out our `docs <https://discordpy-self.readthedocs.io/en/latest/index.html>`_ for more.

Credits:
--------
- `Rapptz <https://github.com/Rapptz>`_ – Creator of the original library.
- `arandomnewaccount <https://www.reddit.com/user/obviouslymymain123/>`_ – Helped in early development.

Key Features
------------
- Modern Pythonic API using ``async`` and ``await``.
- Proper rate limit handling.
- Optimised in both speed and memory.
- Mostly compatible with the upstream ``discord.py``.
- Prevents user account automation detection.
- Implements vast amounts of the user account-specific API:
  * Sessions
  * Read states
  * Connections
  * Relationships
  * Experiments
  * Protobuf user settings
  * Application/team management
  * Store/SKUs/entitlements
  * Billing (subscriptions, payments, boosts, promotions)
  * Interactions (slash commands, buttons, etc.)

Installing
----------
**Python 3.8 or higher is required.**

A `virtual environment <https://docs.python.org/3/library/venv.html>`_ is highly recommended, especially on Linux systems.

Without voice support:

.. code:: sh

   # Linux/macOS
   python3 -m pip install -U discord.py-self

   # Windows
   py -3 -m pip install -U discord.py-self

With voice support:

.. code:: sh

   # Linux/macOS
   python3 -m pip install -U "discord.py-self[voice]"

   # Windows
   py -3 -m pip install -U discord.py-self[voice]

To install the development version:

.. code:: sh

   git clone https://github.com/ephemeral8997/discord.py-self
   cd discord.py-self
   python3 -m pip install -U .[voice]

Optional Packages
~~~~~~~~~~~~~~~~~
- `PyNaCl <https://pypi.org/project/PyNaCl/>`_ – Required for voice support

On Linux, you must also install:

- `libffi-dev` (or `libffi-devel`)
- `python-dev` (e.g., `python3.8-dev`)

Using with Upstream
~~~~~~~~~~~~~~~~~~~
To use alongside upstream ``discord.py``, install ``selfcord.py`` instead.  
See the `renamed branch <https://github.com/dolfies/discord.py-self/blob/renamed/README.rst>`_ for more.

Quick Example
-------------
.. code:: py

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

Bot Example
~~~~~~~~~~~
.. code:: py

   import discord
   from discord.ext import commands

   bot = commands.Bot(command_prefix='>', self_bot=True)

   @bot.command()
   async def ping(ctx):
       await ctx.send('pong')

   bot.run('token')

More examples can be found in the examples directory.

Links
-----
- `Documentation <https://discordpy-self.readthedocs.io/en/latest/index.html>`_
- `Project updates <https://t.me/dpy_self>`_
- `Discussion & support <https://t.me/dpy_self_discussions>`_
