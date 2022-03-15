<hr />
<div align="center">
    <img src="public/static/img/tribe.png" alt="Logo" width='150px' height='auto'/>
</div>
<hr />

# Paw Tribes

The perfect tool for Paw tribes lists and network statistics.

## What is Paw?

PAW is a animal themed digital currency. More information is available over on the official [Paw repository](https://github.com/paw-digital/paw-node).

[![Twitter Follow](https://img.shields.io/twitter/follow/PAW_digital?style=social)](https://twitter.com/intent/follow?screen_name=PAW_digital)
[![Discord](https://img.shields.io/badge/discord-join%20chat-orange.svg?logo=discord&color=7289DA)](https://discord.gg/DjXn6bb3aE)

| Link | Description |
| :----- | :------ |
[PAW.digital](https://paw.digital) | PAW digital currency Homepage

## Prerequisites

- Webserver like nginx as a reverse proxy
- MongoDB
- Nano Node with RPC enabled
- Node.js
- PM2 `npm install pm2 -g`

## Installation

Clone the repository to your server and install the dependencies with `npm i`.

After that copy the `ecosystem.config.sample.js` as `ecosystem.config.js` and edit the environment variables accordingly.

To start up the application execute `pm2 start ecosystem.config.js`.

It is recommended to put the application behind a proper webserver like nginx, a configuration for that could look like this:

```nginx
server {
        listen 80;
        listen [::]:80;

        server_name tribes.paw.digital;

        // location to your PawTribes
        location / {
                proxy_pass http://127.0.0.1:4000;
        }

        // location to your PawAccept instance
        location /payment/ {
                rewrite ^/payment(/.*)$ $1 break;
                proxy_pass         http://127.0.0.1:5000;
        }
}
```

## Open Source Licenses

This product includes GeoLite2 data created by MaxMind, available from <a href="http://www.maxmind.com">http://www.maxmind.com</a>.

## Acknowledgements

Special thanks to the following!

- [My Nano Ninja](https://github.com/BitDesert/MyNanoNinja) - The original one 
