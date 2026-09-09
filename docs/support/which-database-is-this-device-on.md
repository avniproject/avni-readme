---
title: Which database is this device on
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
## Read the Backend line first

When a ticket mentions slowness, a missing card, or a sync problem, find out which database the phone is on before anything else.

Ask the user to open **More**, scroll to the bottom, and send a screenshot of the block there. It has a **Server** line, a **Backend** line, a **Database Schema :** line and a **BuildVersion** line.

* **Backend: realm** and the user is not in the **SQLite Migration** user group: the user was never moved. Nothing about the migration applies to this ticket.
* **Backend: realm** and the user is in the **SQLite Migration** user group: a move has started and has not finished. Escalate with the screenshot.
* **Backend: sqlite**: the user has been moved. Note it on the ticket. The Database Schema number is a small number on the new database, not the large one seen on the old one.

## Two other things that change on the new database

* The **Setup fast sync** item under More is not shown on the new database. Its absence on its own does not prove which database a phone is on. Read the Backend line.
* The **BuildVersion** line is the same on both. Send it with every ticket about the migration.

## How a user is moved

A user is moved by being added to the user group named **SQLite Migration** in the admin screen, and then syncing. The move happens on the phone during that sync.
