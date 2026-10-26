# Population Demo API

Static JSON demo values from the Figma Population test design. Public GET /api/population.json. Data does not update automatically.

- Seven indicators preserve the design display strings alongside numeric values.
- Four annual changes are signed percentages, e.g. 1.2 means 1.2%.
- Land area and density keep the design unit m^2 without validation.
- Nine trend points are estimated from dot geometry. x is a normalized position, not a year. The five year labels are separate.
- These are unverified design examples, not official statistics.

Edit api/population.json, commit, and push main to update GitHub Pages. index.html provides a request example and live response check.

## Overview Demo API

Public endpoint: https://lylywzkj-svg.github.io/population-demo-api-20261026/api/overview.json

`GET /api/overview.json` provides the five groups in the bottom panel of the Figma `overview test` frame. It uses the same `data.metrics` convention as the Population endpoint. The values match this frame; the earlier Population demo's 10% adjustment is not applied here.

| Panel text | JSON binding path | Display value |
| --- | --- | --- |
| Temperature / 温度 | `data.metrics.weather.displayText` | 25 -33°C |
| Weather description / 天气说明 | `data.metrics.weather.description` | Cloudy, 55% chance of rain |
| Total land area / 土地总面积 | `data.metrics.landArea.displayText` | 734.3 km² |
| Population / 人口 | `data.metrics.totalPopulation.displayText` | 5,029,130 |
| GDP per capita / 人均 GDP | `data.metrics.gdpPerCapita.displayText` | US$ 87,880 |
| Tourist arrivals / 游客到访量 | `data.metrics.touristArrivals.displayText` | 6,305,600 |

Use `displayText` with the plugin's **As received / 原样显示** format to retain units and separators. Use `displayLabel` for the four statistical captions, including the GDP and tourist-arrival years. Weather's second text line uses `description` instead.

- The four statistical metrics provide numeric `value` fields and unit-free `displayValue` strings.
- Weather provides numeric `temperatureMin`, `temperatureMax`, and `chanceOfRainPercent` fields. A rain chance of `55` means 55%.
- GDP is corrected to **87,880 USD** as confirmed by the user. The original design text, `US$ 87,8800`, is retained in `originalDisplayText` for reference.
- GDP refers to 2023; tourist arrivals refer to 2022. The design does not specify a date for the other metrics.
- This is static design demo data. Requests return the same data until the JSON file is updated. These values are not a live feed or verified official statistics.

```js
const response = await fetch(
  'https://lylywzkj-svg.github.io/population-demo-api-20261026/api/overview.json'
);
if (!response.ok) throw new Error(`HTTP ${response.status}`);
const result = await response.json();
console.log(result.data.metrics.gdpPerCapita.value); // 87880
console.log(result.data.metrics.weather.description); // Cloudy, 55% chance of rain
```

Edit `api/overview.json` and publish to `main` to update this endpoint. The Population endpoint remains at `api/population.json`.
