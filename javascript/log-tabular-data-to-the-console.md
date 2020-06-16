# How to display tabular data as a sortable table in the browser console

    console.table(data);

## Data can be

- an array: each element in the array will be a row in the table.
- an object: each enumerable property of the object will be a row in the table.
- an array of arrays
- an array of objects

## Restrict columns to display

    console.table(performanceEntries, ['name', 'startTime', 'duration']);
