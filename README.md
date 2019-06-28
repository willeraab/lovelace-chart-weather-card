# Weather card

![custom-weather-card](https://user-images.githubusercontent.com/1109836/60332830-e6096e80-9997-11e9-9527-16b424e1984c.png)

## About

This is a fork from a [very nice weather card](https://github.com/sgttrs/lovelace-weather-card-chart) that I wanted to tweak and adapt a bit. Since the changes are quite extensive and I also do alter stuff to personal taste, I've chosen (for now) to keep this in a separate repo. To not collide with the original I've renamed this card.

## Configuration

Copy `custom-chart-weather-card.js` from this repository into your `config/www` directory first.

Add a reference to the copied file:
```yaml
# Example Lovelace UI config entry
resources:
- type: module
  url: /local/custom-chart-weather-card.js
```
Then you can add the card to the view:
```yaml
# Example Lovelace UI config entry
  - type: 'custom:chart-weather-card'
    title: Weather
    weather: weather.openweathermap
```
You can update this card using [custom updater](https://github.com/custom-components/custom_updater). To do this, add these lines to `custom_updater` configuration in `configuration.yaml`:
```yaml
# Example configuration.yaml entry
custom_updater:
  card_urls:
    - https://raw.githubusercontent.com/willeraab/lovelace-chart-weather-card/master/custom-updater.json
```

#### Configuration variables:

| Name    | Optional | Description                                                                                        |
| ------- | -------- | -------------------------------------------------------------------------------------------------- |
| type    | **No**   | Should be `'custom:chart-weather-card'`. |
| weather | **No**   | An entity_id with the `weather` domain. |
| title   | Yes      | Card title, defaults to friendly_name if no title is set. |
| temp    | Yes      | Entity_id of the temperature sensor. Show temperature value from sensor instead. |
| mode    | Yes      | Default value: `daily`. Set mode to `hourly` to display hours instead weekdays on the chart. |
| number_of_forecasts | Yes | Number of forecast recordings to show, min 3 max 9. |
| chart_only | Yes | Display the chart without displaying the header information. Boolean. |
