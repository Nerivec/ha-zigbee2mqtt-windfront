# Home Assistant Add-on: Zigbee2MQTT WindFront

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

Go back to "Info" tab and start the add-on.

Open the Web UI. _Optionally toggle "Show in sidebar" for quick access._

You can switch Zigbee2MQTT instances (as configured above) using the top right corner button.

> _The color of the icon on the button indicates the status on the underlaying WebSocket. Red means error/disconnected, if that happens after the initial load, make sure the configured URL is valid and your connection is stable._
