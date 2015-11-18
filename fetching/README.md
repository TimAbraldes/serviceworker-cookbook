# Fetching remote resources

This recipe is showing 2 standard ways of loading a remote resource and one attempt to use service worker as a proxy middleware.

There are used 3 types of remote resources - unsecure (http) secured with allow-origin header and secured without the header.

## DOM Element
DOM elements are loading the resources

## Fetch
Fetch issues a cors or no-cors request to each resource

## Fetch with SW proxy
Fetch on the client loads a local resource ./cookbook-proxy/{full URL} which is then translated to real URL in the service worker and forwarded to the client.
