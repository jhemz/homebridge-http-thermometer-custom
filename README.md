# homebridge-http-thermometer

#### Homebridge plugin to monitor a web-based thermometer

## Description

homebridge-http-thermometer exposes a thermometer to HomeKit and monitors it via HTTP requests. The plugin will poll your thermometer at regular intervals and present you with this information.

## Installation

1. Install [homebridge](https://github.com/nfarina/homebridge#installation-details)
2. Install this plugin: `npm install -g homebridge-http-thermometer`
3. Update your `config.json` file

## Configuration

```json
"accessories": [
     {
       "accessory": "Thermometer",
       "name": "Thermometer",
       "apiroute": "http://myurl.com"
     }
]
```

### Core
| Key | Description | Default |
| --- | --- | --- |
| `accessory` | Must be `Thermostat` | N/A |
| `name` | Name to appear in the Home app | N/A |
| `apiroute` | Root URL of your Thermostat device (excluding the rest of the requests) | N/A |
| `pollInterval` _(optional)_ | Time (in seconds) between when homebridge will check the `/status` of your thermostat | `60` |

### Additional options
| Key | Description | Default |
| --- | --- | --- |
| `timeout` _(optional)_ | Time (in milliseconds) until the accessory will be marked as "Not Responding" if it is unreachable | `3000` |
| `http_method` _(optional)_ | The HTTP method used to communicate with the thermostat | `GET` |
| `username` _(optional)_ | Username if HTTP authentication is enabled | N/A |
| `password` _(optional)_ | Password if HTTP authentication is enabled | N/A |
| `model` _(optional)_ | Appears under the "Model" field for the device | `homebridge-web-thermostat` |
| `serial` _(optional)_ | Appears under the "Serial" field for the device | apiroute |
| `manufacturer` _(optional)_ | Appears under the "Manufacturer" field for the device | `Tom Rodrigues` |

## API Interfacing

Your API should be able to return the temperature when it receives `/status` in the JSON format like below:
```
{
    "currentTemperature": FLOAT_VALUE
}
```
