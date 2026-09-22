---
description: We need to filter and build the VT sequences.
icon: sun
---

# Weather Forecast

This feature allows you to get weather forecast information in your city or in your region.

***

## <mark style="color:$primary;">Usage</mark>

If you want to get weather forecast information in your city, you can use the `WeatherForecast` class from the `Nettify.Weather` namespace.

<details>

<summary>Functions</summary>

<table><thead><tr><th width="180.333251953125">Function</th><th>Description</th></tr></thead><tbody><tr><td><code>GetWeatherInfo()</code></td><td>Gets the weather info</td></tr><tr><td><code>ListAllCities()</code></td><td>Lists all cities</td></tr></tbody></table>

These functions download the weather information for either the specified city ID or city name and return the relevant weather information, `WeatherForecastInfo`.

{% hint style="info" %}
For web development and other cases where asynchronous development is appropriate, you can use the functions that are suffixed with the `Async` suffix.
{% endhint %}

</details>

<details>

<summary>Properties of the weather forecast info class</summary>

The weather forecast info class, which is obtained using the `GetWeatherInfo()` function, consists of the following properties:

<table><thead><tr><th width="230.3333740234375">Property</th><th>Description</th></tr></thead><tbody><tr><td><code>Weather</code></td><td>Current weather condition in a region</td></tr><tr><td><code>TemperatureMeasurement</code></td><td>Temperature unit measurement</td></tr><tr><td><code>Temperature</code></td><td>Current temperature</td></tr><tr><td><code>FeelsLike</code></td><td>Current feels like temperature</td></tr><tr><td><code>Humidity</code></td><td>Current humidity</td></tr><tr><td><code>WindSpeed</code></td><td>Current wind speed</td></tr><tr><td><code>WindDirection</code></td><td>Current wind direction</td></tr><tr><td><code>Pressure</code></td><td>Current pressure in hectopascals</td></tr></tbody></table>

where the `UnitMeasurement` is:

<table><thead><tr><th width="300.3333740234375">Type</th><th width="130.333251953125">Temperature</th><th width="125.333251953125">Wind speed</th><th>Pressure</th></tr></thead><tbody><tr><td><code>Kelvin</code></td><td><code>K</code></td><td><code>m.s</code></td><td><code>hPa</code></td></tr><tr><td><code>Metric</code></td><td><code>C</code></td><td><code>m.s</code></td><td><code>hPa</code></td></tr><tr><td><code>Imperial</code></td><td><code>F</code></td><td><code>mph</code></td><td><code>hPa</code></td></tr></tbody></table>

</details>

{% hint style="info" %}
There is an alternative version, called `WeatherForecastOwm`, that gets weather information from OpenWeatherMap. The normal `WeatherForecast` class gets info from [The Weather Channel](https://weather.com/).
{% endhint %}

{% hint style="warning" %}
`WeatherForecast` requires an API key that you can get from your IBM [Weather.com](https://www.ibm.com/products/environmental-intelligence-suite) dashboard. You'll need a package of **15 Day** weather forecast. **Kelvin is not supported in this mode.**

`WeatherForecastOwm` requires providing the OpenWeatherMap API key for each weather operation, which you can get by [visiting this page](https://home.openweathermap.org/api_keys).
{% endhint %}
