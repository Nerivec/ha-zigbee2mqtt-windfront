# Home Assistant App: Zigbee2MQTT WindFront

## How to use

Configure the Zigbee2MQTT API URLs & names in the "Configuration" tab.

> _Each field expects comma-separated values (no space around the commas)._

Example:

`api_urls`
```
localhost:5173/api,localhost:8181/api
```

> **You must provide valid URLs to the API endpoints of the Zigbee2MQTT instances you are targeting.**

`api_names`
```
dev,base
```

`api_tokens` _(optional)_

Set this if your Zigbee2MQTT instances require a frontend auth token (`frontend.auth_token`). The app adds the token to each WebSocket connection itself, so no browser needs it: access is controlled by the Home Assistant login. One token is used for every URL. For different tokens, give one per URL in the same order as `api_urls` (leave a position empty for an instance without a token):
```
tokenA,tokenB,
```

> _Tokens cannot contain commas, and URLs on the same host must use the same token. While tokens are set, the app does not log WebSocket proxy errors, because nginx would include the token in them._

Go back to "Info" tab and start the app.

Open the Web UI. _Optionally toggle "Show in sidebar" for quick access._

You can switch Zigbee2MQTT instances (as configured above) using the top right corner button.

> _The color of the icon on the button indicates the status on the underlaying WebSocket. Red means error/disconnected, if that happens after the initial load, make sure the configured URL is valid and your connection is stable._
