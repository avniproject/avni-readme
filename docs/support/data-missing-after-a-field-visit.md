---
title: Data missing after a field visit
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
## Check whether they synced

Background sync is off by default. Unless the user has switched **Disable Auto Sync** off (under More, by tapping the account name at the top), the app sends data only when they tap the sync icon at the top of the Home screen.

If a user reports that records they saved are not on the server, first ask whether they have tapped the sync icon since saving.

## What to ask them to do

1. Open the app. On the Home screen, look at the sync icon at the top. A number on it means records are waiting to be sent.
2. Tap the sync icon and wait for it to finish. The number goes away when the records have been sent.
3. Check the server again.

## If it is still missing

If the sync fails, or the records are still missing after the number has gone, escalate with:

* the error text the user saw, if any
* a screenshot of the bottom of the **More** screen, showing the Backend and BuildVersion lines
* the user's name and organisation

## If the user says background sync is on

A user can switch **Disable Auto Sync** off under More, by tapping the account name at the top. When it is off, the app is set to try sending new records on its own about once an hour, and not in the half hour after a sync has finished. Ask them to tap the sync icon anyway, and treat the ticket as above.
