Here is an example of how you can create a Discord bot with Vue.js and Discord.js:

First, create a new Vue.js project by following the Vue.js installation instructions.

Install the Discord.js library by running the following command in your project directory:

Copy code
npm install discord.js
Create a new Discord bot by following the Discord Developer Portal instructions.

Once you have created your bot, you will need to add its token to your Vue.js project. 
You can do this by creating a new file in your project called .env.local and adding the following line to it:

makefile

VUE_APP_DISCORD_TOKEN=<your_bot_token>

In your Vue.js project, create a new file called bot.js and add the following code:

```javascript

const Discord = require('discord.js');

const client = new Discord.Client();

client.on('ready', () => {
  console.log(`Logged in as ${client.user.tag}!`);
});

client.on('message', (message) => {
  if (message.content === '!ping') {
    message.channel.send('Pong!');
  }
});

client.login(process.env.VUE_APP_DISCORD_TOKEN);
```

In your Vue.js project, create a new component called Bot.vue and add the following code:

```html
<template>
  <div>
    <h1>My Discord Bot</h1>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'Bot',
  setup() {
    const ready = ref(false);

    const client = new Discord.Client();

    client.on('ready', () => {
      console.log(`Logged in as ${client.user.tag}!`);
      ready.value = true;
    });

    client.on('message', (message) => {
      if (message.content === '!ping') {
        message.channel.send('Pong!');
      }
    });

    client.login(process.env.VUE_APP_DISCORD_TOKEN);

    return {
      ready,
    };
  },
};
</script>
```

In your Vue.js project, create a new component called App.vue and add the following code:

```html
<template>
  <div id="app">
    <Bot />
  </div>
</template>

<script>
import Bot from './Bot.vue';

export default {
  name: 'App',
  components: {
    Bot,
  },
};
</script>
```

Finally, update the main.js file in your Vue.js project to mount the App component:

```javascript
import { createApp } from 'vue';
import App from './App.vue';

createApp(App).mount('#app');
```

This example creates a simple Discord bot that responds to the "!ping" command. 
To add additional commands, you can add more logic to the client.on('message', ...) 
event handler in the bot.js file.
