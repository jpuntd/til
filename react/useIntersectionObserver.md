# useIntersectionObserver hook

```javascript
import { useEffect } from 'react';

interface InterSectionObserverOptions {
  root: Element | null;
  rootMargin: string;
  threshold: number[];
}

export function useIntersectionObserver(
  ref: any,
  callback: Function,
  { root, rootMargin, threshold }: InterSectionObserverOptions
): Function {
  const intersectionObserverOptions = {
    root: root || null,
    rootMargin: rootMargin || '0px',
    threshold: threshold || [0.1]
  };
  const observer = new IntersectionObserver(([entry]) => {
    if (entry.isIntersecting) {
      callback(entry);
    }
  }, intersectionObserverOptions);
  useEffect(() => {
    if (ref.current) {
      observer.observe(ref.current);
    }
  }, []);
  return (): Element => {
    observer.unobserve(ref.current);
    return ref.current;
  };
}
```

## IntersectionObserver api

- observes changes in the intersection of a target element with an ancestor element
- can be used to understand the visibility and position of DOM elements relative to a containing element or to the top-level viewport.

See https://developer.mozilla.org/en-US/docs/Web/API/IntersectionObserver

You provide a callback when creating a new IntersectionObserver object :

    const intersectionObserver = new IntersectionObserver(callback, options);

and then you set the target element(s) with the observe() method:

    intersectionObserver.observe(document.querySelector('#endOfTableIndicator'));

## InterSectionObserverOptions

### root

The ancestor of the target element being observed. If no value was passed to the constructor or this is null, the top-level document's viewport is used.

### rootMargin

margins added around the root element to make it intersect earlier. They can, like in css, be expressed in pixels (px) or as a percentage (%). The default is "0px 0px 0px 0px".

### threshold (SINGULAR!)

a ratio or an array of ratios (in increasing order) telling the observer how much of the target element and root need to intersect before triggering the callback.

I only tested this in Chrome, but it seems using plural thresholds (as MDN + W3C mention) doesn’t work.
