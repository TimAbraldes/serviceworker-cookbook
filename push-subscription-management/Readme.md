https://github.com/mozilla/serviceworker-cookbook/issues/44

Recipe: Push notifications with subscription management
=======================================================

Init state
----------
After service worker is registered, client is checking if it is already subscribed to the notificiation service. Button's contents is set depending on this.

Subscribe
---------
After successful subscription (index.js::pushManager.subscribe) client sends a post request to application server to register the subscription

Notifications
-------------
Server periodically sends a notification using web-push library to all registered endpoints.
If an endpoint is not registered anymore (expired or cancelled) it is removed from subscription list.

Unsubscribe
-----------
After successful unsubscription (index.js::pushSubscription.unsubscribe) client sends a post request to application server to unregister the subscription. Server is no longer sending notification.

Subscription expired
--------------------
Service worker is watching for the *pushsubscriptionchange* event and resubscribes to the push service.

Not in recipe
-------------
Subscription might be cancelled by the user outside of this page (from browser settings or notification UI). In this recipe server will stop to send the notifications, but the front-end doesn't know about it. One could periodically check if registration is still active.