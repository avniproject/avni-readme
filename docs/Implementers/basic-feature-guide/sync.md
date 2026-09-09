---
title: How sync is triggered
excerpt: >-
  Sync can be automated or manual on the Android app. This article talks about
  the different triggers of sync
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Sync data between Avni Client and Server

Sync between Avni Client and Server is initiated by the Client and could be of following types:

### Manual Sync (user triggered, upload and fetch data)

The user taps the sync icon at the top of the Home screen. The app uploads what is on the phone and downloads what is new for the user.

### Automatic Sync

Background sync is off for every user by default. To turn it on, open More, tap the account name at the top (it says Edit Settings underneath), and switch **Disable Auto Sync** off. Until then, the app sends data when the user taps the sync icon at the top of the Home screen, and after login.

When it is on, it runs in one of two forms. For how it decides when to run, see [Internal details of Avni sync](doc:internal-details-of-avni-sync).


1. Complete Sync (Both upload and fetch data)
2. Partial Sync (Only upload of data)\
   ![](https://files.readme.io/d567681-Screenshot_2023-10-30_at_12.08.26_PM.png)
