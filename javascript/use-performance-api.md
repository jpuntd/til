# Use the performance api in your browser to measure performance

Create a marker and give it a name.

    const markerNameA = "example-marker-a";
    const markerNameB = "example-marker-b";

Create a variety of measurements.

    performance.measure("measure a to b", markerNameA, markerNameB);
    performance.measure("measure a to now", markerNameA);
    performance.measure("measure from navigation start to b", undefined, markerNameB);
    performance.measure("measure from the start of navigation to now");

Pull out all of the measurements.

    performance.getEntriesByType("measure")
    performance.getEntriesByName("measure from navigation start to b")

Finally, clean up the entries.

    performance.clearMarks();
    performance.clearMeasures();

[source](https://developer.mozilla.org/en-US/docs/Web/API/Performance)

## Example

    function measurePerformance(title, fn, ...args) {
      for (let i = 0; i < 10; i++) {
        performance.mark(`start`);
        for (let j = 0; j < 50000; j++) {
          fn.call(null, ...args);
        }
        performance.measure(title, `start`);
      }
      const performanceEntries = performance.getEntriesByType('measure');
      console.table(performanceEntries, ['name', 'startTime', 'duration']);
    }

## Explanation

- make 50,000 calls to a function with args
- repeat 10 times, each time measuring
- log the 10 results in a table

I used `console.table` to log all the results. This allows you to sort inside the developer console.
