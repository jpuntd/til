# Add properties to an object only when they are defined

Only add config.color and config.symbol if they are defined:

```javascript
const chartConfig = {
  ...(config.color && { color: config.color }),
  ...(config.symbol && { marker: { symbol: config.symbol } }),
  data: seriesEntry,
  name: name,
  dashStyle: config.dashStyle ? config.dashStyle : defaults.solid,
};
```
