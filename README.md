# disnake-paginator
A module containing paginators for disnake

## Examples
Slash command example
```py
async def ping_command(inter):
	paginator = disnake_paginator.ButtonPaginator(title="Pong", segments=["Hello", "World"], color=0x00ff00)
	await paginator.start(inter)

```

`on_message` example
```py
async def on_message(message):
	if message.content == "!ping":
		paginator = disnake_paginator.ButtonPaginator(title="Pong", segments=["This is", "a message"], button_style=disnake.ButtonStyle.red)
		await paginator.start(disnake_paginator.wrappers.MessageInteractionWrapper(message)) #sends a message in the channel
		await paginator.start(disnake_paginator.wrappers.UserInteractionWrapper(message.author)) #sends a DM to the author
```

`split` function
```py
async def aaa_command(inter):
	paginator = disnake_paginator.ButtonPaginator(title="aaa", segments=disnake_paginator.split("a"*6969, 1000), target_page=2)
	await paginator.start(inter)
```

## Arguments
`title` = The title of the embed\
`segments` = The pages of the paginator (supports `str` and `disnake.Embed`)\
`color` = The color of the embed\
`prefix` = The prefix of every page in the embed\
`suffix` = The suffix of every page in the embed\
`target_page` = The page that the paginator will display when created\
`timeout` = The amount of seconds after the paginator will stop working\
`button_style` = The style of the buttons on the paginator\
`invalid_user_text` = The message that will be shown when someone else tries to use the paginator

