# ZOROxBOT
// index.js
const express = require('express');
const app = express();
const port = process.env.PORT || 3000;

app.use(express.urlencoded({ extended: false }));

app.post('/webhook', (req, res) => {
    const msg = req.body.Body;
    const sender = req.body.From;

    let responseMessage = "Hello 👋, I'm your bot!";
    if (msg.toLowerCase().includes('hi')) {
        responseMessage = "Hi there! How can I help you?";
    }

    res.set('Content-Type', 'text/xml');
    res.send(`
        <Response>
            <Message>${responseMessage}</Message>
        </Response>
    `);
});

app.listen(port, () => {
    console.log(`Server running on port ${port}`);
});{
  "name": "whatsapp-bot",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "express": "^4.18.2"
  }
}
