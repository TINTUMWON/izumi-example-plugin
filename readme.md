### Creating a Plugin

Izumi supports custom plugins, which can be created using the following template:

### text

```javascript
const { izumi, mode } = require('../lib/');
izumi({
	pattern: "test ?(.*)",
	fromMe: true, //false & mode
	desc: 'To get remoteJid',
	type: 'info'
}, async (message, match, client) => {
	await message.client.sendMessage(m.jid, {text: "Hey"})
});
```
### reply

```javascript
await message.reply("Hey")
```

### media

```javascript
await message.client.sendMessage(m.jid,
{
 audio: {url: "https://example.com"}, //video, image
 mimetype: "audio/mpeg", //"video/mp4", "image/jpg"
});
```
### button

```javascript
client.sendMessage(m.jid, {
     text: "Hello World !",
     footer: "Eypz - 2025",
     buttons: [
     {
     buttonId: `.ping`, 
     buttonText: {
     displayText: 'PING'
     },
     type: 1 
     }
     ],
     headerType: 1,
     viewOnce: true
 },{ quoted: null }) //message.data for reply
```
### buttons flow

```javascript
client.sendMessage(m.jid, {
  text: "Hello Wolrd !;", 
  footer: "© Eypz Dev",
  buttons: [
  {
    buttonId: '.runtime',
    buttonText: {
      displayText: 'RUNTIME'
    },
    type: 1,
  },
  {
    buttonId: '.ping',
    buttonText: {
      displayText: 'PING'
    },
    type: 1,
  },
  {
    buttonId: 'action',
    buttonText: {
      displayText: 'interactiveMeta'
    },
    type: 4,
    nativeFlowInfo: {
      name: 'single_select',
      paramsJson: JSON.stringify({
        title: 'message',
        sections: [
          {
            title: 'EypzDev - 2025',
            highlight_label: '🇧🇷',
            rows: [
              {
                header: 'HEADER',
                title: 'TITLE',
                description: 'DESCRIPTION',
                id: 'YOUR ID',
              },
              {
                header: 'HEADER',
                title: 'TITLE',
                description: 'DESCRIPTION',
                id: 'YOUR ID',
              },
            ],
          },
        ],
      }),
    },
  },
  ],
  headerType: 1,
  viewOnce: true
}, { quoted: message.data });
```

### mention User

```javascript
await client.sendMessage(
    jid,
    {
        text: 'Heyy',
        mentions: ['12345678901@s.whatsapp.net']
    }
)
```

### Button with media

```javascript
await client.sendMessage(
    jid,
    {
        image: { url : "https://example.jpg" }, // Can buffer
        caption: "Description Of Messages", //Additional information
        title: "Title Of Messages",
        subtitle: "Subtile Message",
        footer: "Footer Messages",
        media: true,
        interactiveButtons: [
             {
                name: "quick_reply",
                buttonParamsJson: JSON.stringify({
                     display_text: "Display Button",
                     id: "ID"
                })
             },
             {
                name: "cta_url",
                buttonParamsJson: JSON.stringify({
                     display_text: "Display Button",
                     url: "https://www.example.com"
                })
             }
        ]
    },
  {
    quoted : message.data
  }
)
```
