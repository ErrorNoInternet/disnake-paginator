# disnake-paginator
A Python library containing paginators for disnake

## Installation
```
pip install disnake-paginator
```

## Examples
Interaction example
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
	paginator = disnake_paginator.ButtonPaginator(title="aaa", segments=disnake_paginator.split("a"*6969, 1000), target_page=4)
	await paginator.start(inter)
```

## Arguments
`title` = The title of the embed\
`segments` = The contents (pages) of the paginator (supports `str` and `disnake.Embed`)\
`color` = The color of all the embeds\
`prefix` = The prefix of every page in the embed\
`suffix` = The suffix of every page in the embed\
`target_page` = The page that the paginator will display when sent\
`timeout` = The amount of seconds before the paginator stops working\
`button_style` = The style of the buttons on the paginator (red, gray, green, etc)\
`invalid_user_text` = The function that will be called when another user tries to use the paginator
`(x)_button_emoji` = The emoji displayed on the (x) button (for example `first_button_emoji`)
`(x)_button_label` = The label (text) displayed on the (x) button (for example `next_button_label`)

<sub>If you would like to modify this repository (including its code) in your own project, please be sure to credit!</sub>
