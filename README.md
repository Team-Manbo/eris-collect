Eris-Collect
====

A message, reaction, interaction collector for Eris. (supports v17.x)

This package is a modified version of [Oceanic-Collectors](https://github.com/Nuckyz/oceanic-collectors) to fit with eris.

Installing
----------

You need NodeJS 16.16.0+.
```
npm install eris-collect
```

Message Collector Example
-----------------

```js
const { MessageCollector } = require('eris-collect')

const filter = (message) => message.author.id === 'UserID'
const collector = new MessageCollector(client, channel, { filter, time: 60_000 }) // time in ms

collector.on('collect', (message) => {
    console.log(message)
})

collector.on('end', (collectedMessages) => {
    console.log(collectedMessages.length)
})
```

awaitMessages Example
------------

```js
const { awaitMessages } = require('eris-collect')

const filter = (message) => message.author.id === 'ANY USER ID'
const messages = await awaitMessages(client, channel, { filter, max: 2, time: 60_000 }) // time in ms

console.log(messages.length)
```


Interaction Collector Example
-----------------

```js
const { InteractionCollector } = require('eris-collect')

// Return if Interaction was created in DM
// if (!interaction.guildID) return

const filter = (interaction) => interaction.member.id === 'UserID'
const collector = new InteractionCollector(client, channel, { filter, time: 60_000 }) // time in ms

collector.on('collect', (interaction) => {
    console.log(interaction)
})

collector.on('end', (collectedInteractions) => {
    console.log(collectedInteractions.length)
})
```

awaitComponentInteractions Example
------------

```js
const { awaitComponentInteractions } = require('eris-collect')

// Return if Interaction was created in DM
// if (!interaction.guildID) return

const filter = (interaction) => interaction.member.id === 'UserID'
const collectedInteractions = await awaitComponentInteractions(client, channel, { filter, max: 5, time: 30_000 }) // time in ms

console.log(collectedInteractions.length)
```
