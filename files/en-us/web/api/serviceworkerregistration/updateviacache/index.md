---
title: ServiceWorkerRegistration.updateViaCache
slug: Web/API/ServiceWorkerRegistration/updateViaCache
tags:
  - API
  - Property
  - Reference
  - Service Workers
  - ServiceWorkerRegistration
  - updateViaCache
browser-compat: api.ServiceWorkerRegistration.updateViaCache
---
{{APIRef("Service Workers API")}}

The **`updateViaCache`** read-only property of the
{{domxref("ServiceWorkerRegistration")}} interface updates the cache using
the mode specified in the call to {{domxref('ServiceWorkerContainer.register')}}.
Requests for \`importScripts\` still go via the HTTP cache. \`updateViaCache\` offers
control over this behavior.

## Value

Returns one of the following values:

- `imports`, meaning the HTTP cache is not consulted for update of the service worker, but is consulted for `importScripts`.
- `all`, meaning the HTTP cache is consulted in both cases
- `none`, meaning the HTTP cache is never consulted.

## Example

The following example shows the use of updateViaCache.

```js
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('/service-worker.js', {
    updateViaCache: 'none'
  }).then(function(registration) {
    registration.addEventListener('updatefound', function() {
      // If updatefound is fired, it means that there's
      // a new service worker being installed.
      console.log('Value of updateViaCache:', registration.updateViaCache);
    });
  })
  .catch(function(error) {
    console.log('Service worker registration failed:', error);
  });
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using Service Workers](/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [Service workers basic code example](https://github.com/mdn/sw-test)
- [Is ServiceWorker ready?](https://jakearchibald.github.io/isserviceworkerready/)
- {{jsxref("Promise")}}
- [Using web workers](/en-US/docs/Web/API/Web_Workers_API/Using_web_workers)
