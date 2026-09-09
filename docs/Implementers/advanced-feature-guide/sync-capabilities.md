---
title: Sync capabilities
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Offline

Avni works completely in offline mode except during login and sync. The first time sync runs just after login.

## About Sync

* Download - Get data meant for the user from the server onto the device. It is incremental after first sync after login.
* Upload - Uploads any new data created by the user.

| Sync Initiation | Function         | Frequency      |
| :-------------- | :--------------- | :------------- |
| Login           | Download, Upload | NA             |
| Manual Sync     | Download, Upload | NA             |
| Auto Sync       | Upload           | Every hour     |
| Auto Sync       | Download         | Every 12 hours |

The two Auto Sync rows apply only after the user has switched **Disable Auto Sync** off. It is on by default.

<br/>

## More about Auto Sync

Background sync is off for every user by default. To turn it on, open More, tap the account name at the top (it says Edit Settings underneath), and switch **Disable Auto Sync** off. Until then, the app sends data when the user taps the sync icon at the top of the Home screen, and after login.

When a user has turned it on, the app syncs on its own, on a schedule:

* Battery usage - Upload sync should have minimal device resource usage as it will do anything only if the user has captured any new data. Download sync will run twice in a day and the duration for which it runs depends on Internet quality and amount of incremental data it has to get from the server. Also, if the internet quality is poor the device is mostly be CPU idle during the sync.
  * The users may report unusual battery usage using the Battery Usage in the settings for a period of time > 1 day.