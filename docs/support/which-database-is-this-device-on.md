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

Ask the user to open **More**, scroll to the bottom, and send a screenshot of the block there. It has at least a **Server** line, a **Backend** line, a **Database Schema :** line and a **BuildVersion** line.

* **Backend: realm** and the user is not in the **SQLite Migration** user group: either the user was never moved, or they were moved and moved back. Ask whether they were ever in that group. If they were, treat the ticket as a moved-back user; see *A moved user is blocked*.
* **Backend: realm** and the user is in the **SQLite Migration** user group: escalate with the screenshot, and say the user is in the group.
* **Backend: sqlite**: the user has been moved. Note it on the ticket. The Database Schema number is a small number on the new database, not the large one seen on the old one.

![Bottom of the More screen on the old database: Backend: realm](https://github.com/user-attachments/assets/562c5ae4-f6bb-472f-b263-2bb613d72368)

![Bottom of the More screen on the new database: Backend: sqlite, with a small Database Schema number](https://github.com/user-attachments/assets/a0860890-072b-4a53-a62c-4883be91662a)


## Two other things that change on the new database

* The **Setup fast sync** item under More is not shown on the new database. Read the Backend line rather than the menu.
* The **BuildVersion** line is the same on both. Send it with every ticket about the migration.

## How a user is moved

A user is moved by being added to the user group named **SQLite Migration**, and then syncing. The move happens on the phone during that sync.
