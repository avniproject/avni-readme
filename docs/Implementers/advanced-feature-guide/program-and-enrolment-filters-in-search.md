---
title: Program and Enrolment Filters in Search
excerpt: How the Program filter, Not enrolled in any program, Include exited and the enrolment-level filters behave in Data Entry App search and on the phone.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
  pages:
    - type: basic
      slug: my-dashboard-and-search-filters
      title: My Dashboard and Search Filters
---
This page explains how search treats a subject's program enrolments: which subjects a Program filter returns, what happens to exited and deleted enrolments, and how the enrolment-level filters combine. Filters are set up in App Designer, as described in [My Dashboard and Search Filters](doc:my-dashboard-and-search-filters).

# Where each part works

| Feature | Data Entry App search | Phone |
|---|---|---|
| Program filter (program tick boxes, Not enrolled in any program, Include exited) | Yes | No. The phone leaves an empty space where the filter would be. |
| Enrolment Date, Program Encounter Date | Yes | Yes |
| Concept filters at Program Enrolment or Program Encounter scope | Yes | Yes |
| Exited enrolments | Left out unless **Include exited** is on | Always left out |

# Setting up the Program filter

1. In App Designer, open **Search Filters** and add a filter of type **Program** for a subject type. It only needs a title. There is no concept, scope or widget.
2. **Program** is offered only for a subject type that enrols into at least one program, which means a Program Enrolment form is mapped to it. It is not offered for My Dashboard filters.
3. A subject type can have one Program filter. Once it has one, **Program** is no longer offered for that subject type, except while you edit that same filter.

![App Designer, Search Filters: adding a filter of type Program for a subject type](https://github.com/user-attachments/assets/ebac2108-771e-495c-89c2-3ca668b7548e)

# Using the Program filter

On the search screen, after you choose the subject type, the Program filter shows:

- one tick box for each program the subject type enrols into
- a **Not enrolled in any program** toggle
- an **Include exited** toggle

![Data Entry App search: program tick boxes, with the Not enrolled in any program and Include exited toggles on the row below, each with a question-mark tooltip](https://github.com/user-attachments/assets/97b99beb-041d-4dc0-98a9-fc32276e9b69)

**Include exited** never narrows the results on its own. It adds subjects whose enrolment has ended to whatever else is on.

| What is on | Subjects found |
|---|---|
| Nothing | The Program filter is ignored. |
| One or more programs | Subjects with an enrolment in at least one of the ticked programs that they have not exited |
| Programs + Include exited | Subjects with an enrolment in at least one of the ticked programs, exited or not |
| Not enrolled in any program | Subjects who have never been enrolled in any program. A subject who enrolled and later exited still counts as enrolled. |
| Not enrolled in any program + Include exited | Subjects with no current enrolment: never enrolled, or exited from every program they were enrolled in |
| Programs + Not enrolled in any program | Both groups together. With Include exited on, each group also includes subjects whose enrolment has ended. |
| Include exited alone | No subject is left out by the Program filter. Exited enrolments count in the enrolment-level filters below, and show in the Enrolments column. |

- Both toggles can be on together. Hovering over the question mark next to either toggle shows what it does.
- A subject who is enrolled in one program and has exited another still has a current enrolment, so they are not found by **Not enrolled in any program**, even with **Include exited** on.
- A subject whose only enrolment was deleted counts as never enrolled, so **Not enrolled in any program** finds them.
- **Include exited** alone finds the same subjects as nothing ticked. It changes the results only together with an enrolment-level filter, such as Enrolment Date or an enrolment answer, where exited enrolments then count. It also shows exited programs in the Enrolments column.
- There is no option to find only the subjects who have exited a program. Tick the program with **Include exited** on, and look for the "· Exited" chips in the Enrolments column.
- The Program filter applies together with every other filter. For example, a ticked program and a gender return subjects that match both.
- The ticked programs and both toggles are kept when the page is refreshed, along with the rest of the search.

# Exited enrolments

An exited enrolment is one with an exit date. In the Data Entry App, exited enrolments are left out of every enrolment-level filter unless **Include exited** is on:

- Enrolment Date
- Program Encounter Date
- concept filters at Program Enrolment scope
- concept filters at Program Encounter scope
- answers on enrolment forms found by **Search All**

With **Include exited** on, exited enrolments count in all of them.

On the phone, these filters always leave exited enrolments out. The phone has no Include exited option.

# Deleted enrolments

A deleted (voided) enrolment never matches any filter in the Data Entry App, whether or not **Include exited** is on. Visits recorded under a deleted enrolment don't match either.

# Ticked programs narrow the enrolment-level filters

When programs are ticked in the Program filter, the enrolment-level filters look only at enrolments in those programs, and at visits recorded in those programs:

- Enrolment Date
- Program Encounter Date
- concept filters at Program Enrolment and Program Encounter scope
- answers on enrolment forms found by **Search All**

For example, with Pregnancy ticked and a Program Encounter Date range, only Pregnancy visits are checked. A Child visit in the same range does not make the subject match. With no program ticked, every program counts. Registration answers and the subject's name are not affected.

![Search with a program ticked and a Program Encounter Date range: only visits in the ticked program are checked](https://github.com/user-attachments/assets/b87f8a2d-9b14-4bf7-bb19-cf7a797c858a)

# How enrolment-level filters combine

In the Data Entry App, all the enrolment-level conditions in one search must be met by **the same enrolment**:

- the ticked program
- the exit rule above
- Enrolment Date
- every concept filter at Program Enrolment scope

So a subject enrolled twice, once in March and once in June with a different answer, matches "enrolled in March with that answer" only if the March enrolment has that answer.

- **Ranges:** both ends of a range are checked on the same enrolment or visit. A numeric range of 10 to 20 does not match a subject who has 5 on one enrolment and 50 on another.
- **Visits:** each concept filter at Program Encounter or Encounter scope looks at the visits of that scope, and a range must be met by one visit.

On the phone, each filter is checked on its own, and a subject matches when every filter is met by some enrolment or visit. Two filters can be met by two different enrolments.

# Date and time answers

- **DateTime concept filters** in the Data Entry App search by date only, and the filter asks for a date. A DateTime answer matches when it falls on the chosen date, or within the chosen dates for a range, in the user's time zone.
- On the phone, a DateTime filter with one value matches only an answer with exactly that date and time, and a range compares the full date and time.
- **Date and Time concept filters** compare the date or the time as stored.
- A stored answer that isn't a valid date, date-time or time is skipped, so it doesn't match and doesn't stop the search.

# The Enrolments column in the results

The results table has an **Enrolments** column with one chip per program the subject is enrolled in.

- By default it shows programs the subject is actively enrolled in.
- With **Include exited** on, programs the subject has exited also show, with an outlined chip reading "*program* · Exited". When programs are ticked, only exited enrolments in the ticked programs show.
- If a subject exited a program and then enrolled in it again, only the active enrolment's chip shows.
- Deleted enrolments, and programs that have been deleted from the organisation, don't show.
- The chip uses the program's name as set up for the organisation.

# Concept types that can be searched

Concept filters work for the types the phone supports: Coded, Text, Id, Notes, Numeric, Date, DateTime and Time. App Designer offers only these types for Search Filters. A filter saved earlier on another type, such as NA, is ignored by search and does not stop the search screen from opening.

# Users need to sync the app to get changes to filters.
