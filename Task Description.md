# Task 1: Weather Report

Create a class `Forecast`, which can analyze data from multiple weather stations and generate a weather forecast.

### Constructor
`CONSTRUCTOR(int[][] rainfall, String[] descriptors)`

A constructor that accepts two parameters: 
- `rainfall`: a 2D integer array representing rainfall data.
- `descriptors`: a string array containing general weather reports for the day.

In the `rainfall` array, each row corresponds to a weather station, and each column represents a day.

In the `descriptors` array, each column represents a day and contains one of the values: "sunny," "rainy," or "thunderstorm."

#### Example:

| Weather Stations | Day 1 | Day 2 | Day 3 | Day 4 | Day 5 | Day 6 | Day 7 |
|------------------|-------|-------|-------|-------|-------|-------|-------|
| Station 1        | -10   | 22    | 33    | 19    | 45    | 75    | 20    |
| Station 2        | 35    | -6    | 57    | 8     | 10    | -100  | 10    |
| Station 3        | 15    | 20    | 29    | 39    | 30    | 75    | 20    |

| Day 1   | Day 2   | Day 3       | Day 4   | Day 5   | Day 6       | Day 7   |
|---------|---------|-------------|---------|---------|-------------|---------|
| sunny   | rainy   | thunderstorm| sunny   | sunny   | thunderstorm| sunny   |

### Data Preparation
`dataPreparation()`

The rainfall data may contain erroneous negative values. This method should clean the data according to the following rules:
- If the descriptor for a day is "sunny," replace negative values with 0.
- If the descriptor is "rainy," replace negative values with the average of all positive values from other weather stations for that day. If all stations report errors, set the values to 0.
- If the descriptor is "thunderstorm," replace negative values with their absolute value.

#### Example after `dataPreparation`:

| Weather Stations | Day 1 | Day 2 | Day 3 | Day 4 | Day 5 | Day 6 | Day 7 |
|------------------|-------|-------|-------|-------|-------|-------|-------|
| Station 1        | 0     | 22    | 33    | 19    | 45    | 75    | 20    |
| Station 2        | 35    | 21    | 57    | 8     | 10    | 100   | 10    |
| Station 3        | 15    | 20    | 29    | 39    | 30    | 75    | 20    |

### Total Rainfall
`totalRainfall()`

This method calculates the total rainfall measured by all weather stations during the observation period.

#### Example:
For the given data, the total rainfall is 683.

### Rainfall Query
`getRainfall(int day_index, String mode)`

This method receives a day index and a mode as parameters. If the index is invalid, return -1. The mode can be either "biggest," "lowest," or "sum."
- "lowest" returns the lowest rainfall value of the day.
- "biggest" returns the highest rainfall value of the day.
- "sum" returns the sum of rainfall for the day.

#### Examples:
- `getRainfall(0, "lowest")` → returns 0
- `getRainfall(3, "biggest")` → returns 39
- `getRainfall(4, "sum")` → returns 85
- `getRainfall(7, "sum")` → returns -1

### Temperature Calculation
`calculateTemperature()`

This method determines the temperature per day for each weather station. The temperature is calculated as follows:
- If the weather is "sunny," multiply the rainfall by 3 to get the temperature.
- If the weather is "rainy," divide the rainfall by 2 to get the temperature.
- If the weather is "thunderstorm," return the remainder of dividing the rainfall by the current day index. If the day index is 0, divide the rainfall by the number of stations.

#### Example:

| Day 1 | Day 2 | Day 3 | Day 4 | Day 5 | Day 6 | Day 7 |
|-------|-------|-------|-------|-------|-------|-------|
| 0     | 11    | 1     | 57    | 135   | 0     | 60    |
| 105   | 10    | 1     | 24    | 30    | 0     | 30    |
| 45    | 10    | 1     | 117   | 90    | 0     | 60    |

### Trend Calculation
`trend(int n)`

This method creates a forecast based on the average rainfall per station and day for the last `n` days. It returns a string corresponding to one of the descriptors:
- If the average rainfall over the last `n` days is below 50, return "sunny."
- If the average rainfall is 50 or higher, return "rainy."
- If the average rainfall is exactly 75, return "thunderstorm."

#### Examples:
- `n = 3` → The average rainfall over the last 3 days is 42. Return "sunny."
- `n = 2` → The average rainfall over the last 2 days is 50. Return "rainy."
