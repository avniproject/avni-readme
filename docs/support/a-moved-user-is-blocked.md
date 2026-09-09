---
title: A moved user is blocked
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
A user who has been moved to the new database and cannot work needs two things: the platform team told, and the phone made usable again. Do them in that order.

## 1. Escalate first

Before changing anything, collect:

* a screenshot of the bottom of the **More** screen, showing the Backend, Database Schema and BuildVersion lines
* the exact error, or a screenshot of the screen the user is stuck on
* whether the user has records saved on the phone that have not been sent: a number on the sync icon at the top of the Home screen means yes
* the app's logs: under **More**, tap **Upload app info**

Send these to the platform team. Do not move the user back until they have replied.

## 2. Move the user back, only if the platform team agrees

1. Ask the user to tap the sync icon on the Home screen and wait until the number on it is gone. Repeat until nothing is waiting. This is what protects their data. Anything not sent before the next step is lost.
2. In the admin screen, remove the user from the **SQLite Migration** user group.
3. Ask the user to tap the sync icon again. If the More screen still says **Backend: sqlite**, ask them to tap it once more. If it still says sqlite after that, stop and escalate.
4. Confirm the More screen now says **Backend: realm**. The app then downloads the user's data afresh, which can take a while for a large area.

## What this does not do

It does not bring back anything that was not sent before step 1. Do not skip step 1.

## When not to do it

If the app crashes every time it opens, or the user cannot reach the sync icon, do not move them back. Escalate and wait.
