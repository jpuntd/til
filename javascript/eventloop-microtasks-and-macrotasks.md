# eventloop, microtasks and macrotasks

## microtasks

- come only from our code
- promise handler
- goal of a microtask: update application state (that's why they all need to complete before next rendering)
- microtasks get priority over a macrotask that was added to the queue before them

## macrotasks

- Timeout event (caused by setTimeout)
- Interval event (caused by setInterval) **but only if no task for the same timer is already in the queue**


        setTimeout(callback, 10)
        setInterval(callback, 10)

The setTimeout will be added to the queue after 10ms. So there will be at least 10ms between setting the timer and callback execution.
The setInterval will try to ececute callback every 10ms regardless of when the last callback was executed. This could be less than 10ms ago.

## the event loop

- checks the macrotask queue
- starts **one** task if there is one waiting
- runs the task to completion. This task can add microtasks to the microtasks queue (eg promise)
- processes **all** the microtasks in the microtasks queue (even if they were added to queue after a macrotask)
- (only then!) performs ui rerender if necessary. Rendering never happens when the engine is executing a task

Acts of detecting and adding tasks are done separately from the event loop.
No UI rendering happens between macrotask running to completion and processing of microtasks. To keep framerate at 60fps, a single macrotask ( + the microtasks generated by that task! ) should complete within 16 ms.

## methods

**macrotasks:** [setTimeout](https://developer.mozilla.org/docs/Web/API/WindowTimers/setTimeout), [setInterval](https://developer.mozilla.org/docs/Web/API/WindowTimers/setInterval), [setImmediate](https://developer.mozilla.org/docs/Web/API/Window/setImmediate), [requestAnimationFrame](https://developer.mozilla.org/docs/Web/API/window/requestAnimationFrame), [I/O](https://developer.mozilla.org/docs/Mozilla/Projects/NSPR/Reference/I_O_Functions), UI rendering

**microtasks:** [process.nextTick](https://nodejs.org/uk/docs/guides/event-loop-timers-and-nexttick/), [Promises](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise), [queueMicrotask](https://developer.mozilla.org/docs/Web/API/WindowOrWorkerGlobalScope/queueMicrotask), [MutationObserver](https://developer.mozilla.org/docs/Web/API/MutationObserver)

[source](https://stackoverflow.com/a/25933985/6570344)
