# Innovorix

## Executive Product Document

## Institute Management Platform

Innovorix is a complete institute management platform built to run the daily, monthly, and yearly operations of an educational institute from one connected system.

It is designed for institutes that want to replace scattered manual work, disconnected staff coordination, repeated data entry, paper-heavy fee handling, and weak parent visibility with one organized digital workflow.

This document is intentionally written for:

- institute owners
- principals
- directors
- campus heads
- branch managers
- operations teams
- admissions teams
- finance teams
- marketing teams
- sales teams
- implementation teams

This is not only a technical README.

This is also a product understanding document.

It explains:

- what Innovorix is
- what modules are included
- what each role gets
- what each page does
- what hidden strengths exist inside the workflows
- what makes the product attractive for institutes
- what makes it practical for daily operations
- what makes it useful for parents, teachers, finance staff, and institute leadership
- what makes it strong on desktop and mobile

---

## One-Line Positioning

Innovorix is an all-in-one institute ERP and operations platform for academics, fees, attendance, communication, results, promotion, library work, leave handling, and multi-role day-to-day management.

---

## Short Product Pitch

An institute does not only need software that stores records.

It needs software that helps people work faster, make fewer mistakes, follow clearer processes, and communicate better.

Innovorix is built around that practical goal.

Instead of giving every department a disconnected tool, it connects the major operational areas of an institute:

- admissions
- student records
- guardian records
- staff records
- class and timetable planning
- attendance
- assessments
- exams and marks
- marksheets
- fees and payment proof review
- fee defaulters
- promotion
- communication
- library circulation
- notifications
- mobile access

The WhatsApp Gateway used by the Baileys service also reuses the shared SMTP flow for signup verification and password reset emails, so gateway users can recover access without a separate mail path.
The gateway signup and reset screens now both require password confirmation so the user can catch typos before submitting.

<details>
<summary><b>WhatsApp Gateway: safe sending, spreadsheet uploads and developer tools</b></summary>

**Sending is queued, never instant.** When a message is submitted the gateway stores it and answers immediately, then delivers it a few seconds later. Messages leave one at a time per linked number, with a random pause in between and a firm limit on how many go out per minute, per hour and per day. This is deliberate: a burst of identical instant messages is what gets a WhatsApp number banned. An institute can submit a thousand messages at once and they will simply go out safely over time. Nothing is lost if the service restarts, because the waiting messages are stored in the database rather than in memory. If the number disconnects mid-run, the remaining messages wait for it to come back instead of failing.

**Send to a list from a file.** The gateway dashboard accepts a CSV, TSV or Excel file with one person per row: a phone number, optionally a name, and either a message column or one message written once for everybody. A message can be personalised per person by writing a column name in double braces, for example `Hi {{name}}, your fee for {{month}} is due`. Local numbers written as `03001234567` are converted automatically. Before anything is sent, the page shows how many rows are usable, which rows will be skipped and why, duplicate numbers, the exact text the first few people will receive, and how long the whole run will take. Once it is running, progress can be watched and the rest can be cancelled at any time. A sample file is downloadable from the same card.

**Control over each number.** Every linked number shows how many messages are still waiting and roughly how long they will take. Each can be paused and resumed without losing anything, have its waiting messages cleared, or be set to a slower sending speed. Speeds can only be made slower than the service default, never faster, so no setting can put a number at risk. A "Very slow" option exists for numbers that were linked recently.

**Developer tools.** The dashboard has a one-click Postman collection download with the institute's own API key and gateway address already filled in, so it can be imported and used immediately without configuration, alongside the live API documentation. The same pacing applies to anything sent from Postman or from custom code, so experimenting with the API cannot get the number banned.

**Where the waiting messages live.** Waiting messages are held in two places at once: the database records what was sent, to whom and what happened to it, and Redis handles the timing, the retries and the waiting. If either one is interrupted the other repairs it, so a server restart, a crash, or a wiped cache never loses a queued message and never sends one twice.

</details>

<details>
<summary><b>How the WhatsApp services are kept running and up to date</b></summary>

The WhatsApp sender and the incoming-message handler run as their own small services alongside the main system, rather than inside it, so a problem in one cannot slow down or take down the rest of the platform. One copy of each serves the whole machine.

Keeping them current is automatic. Every time the platform starts, it checks whether each service is running and whether it is running the current version. Missing services are started, out-of-date ones are updated in place, and anything already current is simply reused. Where two copies of the platform run side by side on one server, the more recent version wins and the other attaches to it instead of fighting over it. Only the service that actually changed is restarted, so updating the incoming-message handler never interrupts a live WhatsApp connection.

Both services also report their own health, including whether the database and the queue behind them are reachable, so a problem can be seen directly rather than inferred from failed messages.

</details>

<details>
<summary><b>What a head of school can ask over WhatsApp</b></summary>

Messaging the school's WhatsApp number from a registered admin's phone opens a short numbered menu. Every answer covers that admin's own institute only.

- **Today's attendance** — present, absent and on leave across the school, the resulting percentage, and how many students nobody has marked yet.
- **Absent students today** — the first few by name and class, with a count of the rest.
- **Fees** — collected so far this month, what is still outstanding, how much of that is overdue and how many bills that is, and anything waiting for a payment to be reviewed.
- **Leave requests to approve** — how many are waiting, who they are for and when they were raised, oldest first.
- **School at a glance** — students, staff and classes on the books.

Attendance follows the same rule as the rest of the platform: approved leave is shown as its own figure and never counted against the school, and a day on which every marked student was on leave says so rather than showing a misleading percentage.

Entering marks and changing school settings stay in the app, because both need the full record in front of you; asking for them over WhatsApp explains that rather than leaving you waiting for a reply.

</details>

The result is a platform that is useful not only for management, but for daily execution.

---

## What Type Of Institutes Can Use Innovorix

Innovorix is suitable for:

- schools
- colleges
- academies
- coaching centers
- tuition networks
- training institutes
- branch-based education businesses
- private institute groups

In this document, the preferred word is `institute`.

Where a workflow is common in a traditional classroom-based institute, the same workflow still applies here.

---

## Core Product Promise

Innovorix helps an institute:

- centralize records
- reduce repeated data entry
- improve operational discipline
- increase parent transparency
- speed up fee management
- improve attendance handling
- simplify academic workflows
- formalize leave approvals
- organize communication
- support staff on mobile
- create cleaner year-end promotion workflows

---

## Major Benefits For Institute Leadership

### Better Control

Leadership gets clearer visibility into students, staff, attendance, fees, exams, and operational progress.

### Less Dependency On Informal Systems

Instead of relying on:

- paper registers
- personal WhatsApp groups
- manual fee notebooks
- spreadsheet fragments
- separate result files

the institute can work from one connected platform.

### Faster Daily Work

Bulk actions, templates, auto-fill logic, duplication tools, and role-based pages reduce the effort needed for repetitive work.

### Better Parent Trust

Guardians can see attendance, fees, marksheet, and communication history more clearly.

### Better Staff Accountability

Leave reviews, exam progress, attendance entries, fee approvals, and communication flows all become more structured.

### Better Mobile Usability

A strong part of the product experience is designed around practical mobile use for staff, parents, and students.

---

## Modules At A Glance

Innovorix includes the following major modules:

- Dashboard
- Staff Management
- Student Management
- Guardian Management
- Classes & Sections
- Timetable Management
- Attendance
- WiFi Attendance (staff check-in and QR sessions)
- Leaves
- Assessments
- Exams
- Marksheet
- Fees & Payments
- Fee Defaulters
- Payment Proof Review
- Library
- Promotion
- Communication
- Notices & Calendar
- Settings & Institute Configuration
- Notifications
- Mobile App Experience

---

## Roles Covered In This Document

This document covers these roles in detail:

- Admin
- Teacher / Staff
- Student
- Guardian
- Accountant
- Librarian

Super admin capabilities exist in the platform as well, but this document focuses on the operational roles that matter most in regular institute use and sales conversations.

---

## Quick Role Summary

| Role       | Main Purpose In The Institute                                                                |
| ---------- | -------------------------------------------------------------------------------------------- |
| Admin      | Runs institute setup, records, fees, academics, communication, and promotions                |
| Teacher    | Runs class-level teaching workflows such as attendance, assessments, marks, and leave review |
| Student    | Views own learning, attendance, fees, results, timetable, and leave status                   |
| Guardian   | Tracks child progress, fees, attendance, marksheet, leave requests, and conversations        |
| Accountant | Runs the fee collection side, fee follow-up side, and payment proof review side              |
| Librarian  | Manages books, issue-return flow, overdue books, and library fine handling                   |

---

<details>
<summary><strong>Platform Overview, Product Value, Setup Journey, And General Product Story</strong></summary>

## Why Innovorix Is Attractive From A Product Perspective

Many institute systems can list students.

Many can record fees.

Many can create timetables.

Many can show marks.

But the stronger value comes when those modules work together.

Innovorix is attractive because it does not stop at simple record storage.

It includes operational logic.

It includes hand-holding inside workflows.

It includes shortcuts that reduce staff effort.

It includes review states so actions are not lost.

It includes role-specific views so people are not overwhelmed.

It includes mobile usability, which is essential for real institute adoption.

---

## Product Philosophy

Innovorix is not meant to be used only by an IT person.

It is meant to be used by:

- an admin officer
- a finance operator
- a teacher
- a class in-charge
- a librarian
- a parent
- a student

That is why the platform is built around practical operational pages rather than technical complexity.

---

## Main Product Stories

The easiest way to understand Innovorix is to see the types of stories it solves.

### Story 1: Admission To Daily Learning

An institute admits a student.

The student gets linked to a class.

The guardian can be linked during admission.

Admission fees can be suggested automatically.

Student and guardian credentials can be generated automatically.

The student then appears in attendance, assessments, exams, marksheet, fees, and leave workflows without needing repeated record creation in each module.

### Story 2: Timetable To Teacher Work

The institute creates classes and timetable slots.

Teachers are assigned during timetable setup.

Those assignments then support:

- teacher timetable views
- teacher class views
- attendance workflows
- communication workflows
- class-based academic workflows

### Story 3: Fee Planning To Fee Recovery

The institute creates fee sessions and fee campaigns.

Fees are generated in bulk.

Students and guardians can view their challans.

Payment proofs can be uploaded and reviewed.

Defaulters can be isolated on a dedicated page.

Reminders can be sent.

Fees can be marked paid.

Next fee cycles can be duplicated from earlier sessions to reduce effort.

### Story 4: Exam Creation To Result Visibility

The institute creates exam sessions and exam slots.

Teachers enter marks.

Progress bars help track grading completion.

Students and guardians later see datesheets, marks, and marksheets in role-appropriate pages.

### Story 5: Student Leave To Approved Record

A student requests leave.

Guardian approval can happen first.

Teacher approval can happen next.

Attachments, comments, bypass reasons, and status history stay visible.

The institute gets a cleaner leave process than informal message-based handling.

### Story 6: End Of Session Promotion

At the end of an academic cycle, the institute can:

- promote selected students from one class
- or run bulk promotion across many classes

The system records promotion history by academic session so the institute keeps better long-term records.

---

## Product Value For Marketing Teams

If a marketing team needs to explain Innovorix clearly, these are strong talking points:

- one platform for the full institute operation
- better control for management
- less manual duplication for staff
- stronger fee collection workflows
- parent transparency through guardian access
- teacher productivity through role-based pages
- mobile-friendly daily usage
- structured approvals and audit trails
- modern communication features
- result and fee visibility in one system

Another good selling angle is this:

Innovorix is not just a record system.

It is an operating system for an institute.

---

## Product Value For Sales Conversations

When presenting to a prospect, the strongest practical points are often:

- how the fee system reduces repeated work
- how the parent side improves transparency
- how the teacher side stays focused and simple
- how mobile usage makes adoption easier
- how attendance and exam data connect naturally
- how the promotion workflow saves year-end operational time
- how communication becomes more controlled

---

## Product Value For Implementation Teams

An implementation team can use this document to understand:

- which modules must be configured first
- which roles must be trained first
- which workflows are interconnected
- which quick wins the institute will notice early

---

## Suggested First-Time Institute Setup Journey

An ideal rollout journey inside Innovorix can follow this order:

### Step 1: Institute Setup

- create institute profile
- set contact details
- set domain
- set timetable display mode
- set timezone
- configure preferences

### Step 2: Staff Setup

- add staff
- add teachers
- define who is operationally active
- create credentials where needed

### Step 3: Class Setup

- create classes
- create sections
- assign teachers
- create subjects
- build timetable

### Step 4: Student And Guardian Setup

- add students
- link guardians
- import data if needed
- create credentials
- confirm class placement

### Step 5: Financial Setup

- configure admission fee rules
- configure late fee rules
- configure sibling discount if needed
- create first fee session
- create fee campaigns

### Step 6: Academic Workflow Start

- start attendance
- create assessments
- create exams
- train teachers on marks entry

### Step 7: Parent Visibility Start

- enable guardian visibility
- train office on payment proof review
- train guardians on fee and leave workflows

### Step 8: Year-End Flow

- results and marksheet review
- promotion planning
- single or bulk promotion execution

---

## Desktop And Mobile Experience

Innovorix is not only a desktop dashboard.

The product experience is clearly designed to work in mobile use cases too.

That matters because in real institute environments:

- parents often use phones, not laptops
- students often use phones, not laptops
- teachers often check schedules, notices, and updates on phones
- admin and finance staff may need quick mobile confirmation and visibility

---

## Mobile App And Mobile Experience

Innovorix includes strong mobile-readiness and native mobile support.

### What This Means In Practical Terms

- the interface is designed to remain usable on mobile screens
- the product includes a mobile-oriented navigation flow
- the layout adapts for role-based usage on smaller devices
- important workflows such as attendance, fees, communication, and notices are available in mobile-friendly presentation
- push notification handling is built into the product
- Android app packaging exists through a native wrapper workflow
- the system can also operate as a standalone installed web app experience

### Native Mobile App Direction

The project includes Android build support through a native mobile packaging setup.

This means the product can be delivered not only as a browser platform, but also as a mobile app experience for institutes that prefer app-based usage.

### Mobile Strengths That Matter For Adoption

- quick access to dashboard and menu items
- better experience for guardians checking child progress
- easier fee and payment proof interaction from phones
- easier communication handling from phones
- easier notice consumption from phones
- better teacher access to timetable and attendance on the go

### Mobile Notifications

The platform supports notification-oriented workflows and mobile permissions handling.

This helps the institute reach users more directly for operational updates.

### Mobile Design Value In Marketing Terms

For a marketing team, this matters because many prospects do not ask only:

`What can the product do?`

They also ask:

`Will people actually use it regularly?`

Mobile readiness improves the answer to that question.

### Mobile Experience Positioning

A good product positioning line can be:

Innovorix is built for real institute life, not only for office desktops.

---

## Notices, Communication, And Visibility

One of the stronger product stories in Innovorix is visibility.

An institute often struggles because information is available, but not visible to the right people at the right time.

Innovorix improves that through:

- role-based dashboards
- noticeboard visibility
- fee visibility
- attendance visibility
- marksheet visibility
- communication threads
- mobile access
- notifications

This is especially helpful in institutes where parents repeatedly call the office for information that should already be visible digitally.

---

## Detailed Role And Module Breakdown

The following sections describe what each role gets and what each page is meant to achieve.

---

</details>

<details>
<summary><strong>Admin Role, Admin Pages, And Admin Workflows</strong></summary>

# Admin Role

## Admin Role Summary

The Admin role is the main operational leadership role inside the institute.

This role is not only about data entry.

It is about running the institute digitally.

Admin controls the daily backbone of the product:

- staff setup
- student and guardian records
- class and timetable planning
- fee lifecycle
- attendance management
- leave review
- academic planning
- marksheet access
- fee recovery
- parent visibility
- promotion execution
- institute settings

If someone asks, `What is the main control role inside Innovorix?`

the answer is:

`Admin`

---

## Admin Dashboard

### Purpose

The dashboard gives the admin a central operational overview instead of forcing the admin to open many modules one by one.

### Institute Health Score

The first thing Admin/SuperAdmin sees is an executive **Institute Health** panel — a single 0-100 score blended from six operational metrics, each shown as a trend card with its change versus the previous period:

- **Attendance** — present vs absent (leave excluded)
- **Fee Recovery** — amount collected vs billed
- **Student Performance** — average grade percentage
- **Teacher Compliance** — class days with attendance marked
- **Leave Resolution** — leave requests resolved vs pending
- **Parent Engagement** — active guardians in messaging

It includes an attendance trend chart and a current-vs-previous comparison chart. The time range adapts to how long the institute has existed (Last 7 Days, 30 Days, 90 Days, 6 Months, Last Year, or a custom range), and the comparison period adjusts automatically. Metrics with no data show **N/A** and are excluded from the score, so a newly-created institute still gets a fair reading. The whole panel loads from a single backend request and refreshes in one request when the range changes.

### What The Admin Sees

- total students
- total classes
- total sections indirectly through class structure
- active teachers
- upcoming exams
- notices and calendar

### What The Admin Can Do From Here

- understand current institute scale
- quickly notice if class structure or staff scale is growing
- post notices
- review upcoming academic activity
- use the dashboard as a command center before entering deeper modules

### Why This Matters

A dashboard should not be decorative.

It should reduce uncertainty.

For an admin, that means being able to quickly understand:

- how many students exist
- how many teachers are active
- whether exam periods are approaching
- whether notices need to be pushed

### Posting A Notice

A notice is aimed at roles and, optionally, at classes.

- pick the roles that should hear it, exactly as before
- leave the class picker empty and the notice goes to the whole institute
- pick one or more classes, or individual sections, and the notice is limited to them

When classes are chosen, a notice reaches the students in those classes, the guardians of
those students (a guardian is matched through the children they have there, not through a
class of their own), and the teachers assigned to those classes. Admins, accountants and
librarians run the whole institute, so a class filter never hides a notice from them.

Every notice in the list carries a small line showing its roles and either "All classes" or
the classes it was aimed at, so a school-wide announcement is distinguishable from a
class-specific one at a glance. Hovering that line explains who received it and why.

### Nice Points

- dashboard cards are practical, not abstract
- notices and calendar are integrated
- role-specific dashboard behavior exists in the platform, so the admin experience stays distinct from the teacher and guardian experience

---

## Admin Staff Page

### Purpose

This page manages the people who work inside the institute.

### Main Capabilities

- add staff
- edit staff
- view staff details
- disable staff accounts
- permanently delete staff records
- import staff from CSV
- export staff to CSV
- sync staff records with login/auth accounts
- send notifications to staff
- use tags for organization
- open teacher timetable directly from the staff page

### What The Admin Can Maintain In A Staff Record

- name
- role
- email
- mobile number
- joining-related information
- password where relevant
- tags
- assigned teaching visibility via timetable and classes

### Operational Benefits

- staff onboarding becomes structured
- role-based staff creation becomes easier
- the institute does not lose control over active versus disabled accounts
- admin can review a teacher’s schedule without leaving the module

### Hidden And Useful Points

- the platform supports staff that may not need a normal login, using the `Other` role
- bulk account handling reduces repetitive office work
- timetable visibility from the staff page helps in workload review, conflict review, and internal planning
- import/export makes migration and periodic auditing easier

### Why A Principal Or Director Should Care

A strong staff page is not only a database.

It helps the institute answer questions like:

- who is active
- who is teaching what
- whose account should be disabled
- whether staff records are complete
- whether teacher timetable assignment looks balanced

---

## Admin Classes Page

### Purpose

The classes page controls the structural academic design of the institute.

This is where class organization becomes usable across the system.

### Main Capabilities

- create classes
- create sections
- edit full class records
- edit a single section inside a class
- assign teachers
- assign subjects
- build weekly timetable
- import timetable data
- export class data
- switch between grid and list views
- view timetable by class
- view timetable by section
- delete classes
- delete sections when safe

### What This Page Connects To

This page does not work in isolation.

It directly influences:

- teacher timetable
- student placement
- attendance module
- exam planning
- communication context
- timetable viewing pages

### Timetable Creation Experience

The timetable builder allows the admin to define:

- start time
- end time
- subject
- teacher
- repeat days

### Important Smart Workflow

One of the nicest workflow points in the project exists here.

When the admin adds the first lecture slot and then clicks to add another one:

- the system can reuse the previous selected days
- the next slot can start from the previous end time
- the duration pattern continues

This speeds up routine timetable building significantly.

For institutes that build many periods in one go, this is a real time saver.

### Section Handling Strength

The section system is practical rather than shallow.

The admin can:

- manage multiple sections inside the same class
- open only a particular section for editing
- see student counts per section
- remove a section only when it is operationally safe

### Safety Controls

The page protects the institute from accidental structural damage.

For example:

- a section with assigned students cannot simply be removed without action
- timetable-linked sections warn before deletion

### Notifications

When timetable changes are made, the admin can control notifications to:

- staff
- students
- guardians

### Why This Matters

For many institutes, timetable editing is one of the most painful repetitive tasks.

Innovorix makes it easier through:

- repeated-day reuse
- next-slot continuation
- section-aware editing
- direct teacher assignment
- subject creation inside the flow

### Marketing-Friendly Angle

This is a good section to position as:

`Less timetable effort. More control. Fewer mistakes.`

---

## Admin Students And Guardians Page

### Purpose

This page manages the central records of the institute: students and the guardians linked to them.

### Structure

The page separates:

- Students
- Guardians

This is important because institutes need both linked records and independent management.

### Student-Side Capabilities

- add student
- edit student
- view student
- disable student
- permanently delete student
- import students
- export students
- change class in bulk
- send notifications
- open communication actions
- view attendance percentage
- assign tags

### Guardian-Side Capabilities

- add guardian
- edit guardian
- view guardian
- disable guardian where needed through account logic
- permanently delete guardian
- sync guardian login records
- track linked children

### Admission Workflow Strength

This page is stronger than a basic registration form because the student record and guardian record can be handled together.

During admission, admin can:

- create the student
- link an existing guardian
- create a new guardian
- auto-generate credentials
- connect the student to class placement
- support the admission fee workflow

### Hidden And Useful Point: Roll Number Handling

Innovorix includes stronger roll number handling than many simple systems.

When a roll number conflict happens, the admin does not have to solve it manually outside the platform.

The platform supports:

- swapping roll numbers between students
- auto-resolving conflicts by shifting the conflicting record to the next available number

This is a small-looking feature with very high operational usefulness.

### Hidden And Useful Point: Credential Automation

The platform can auto-generate:

- student IDs
- guardian IDs
- student passwords
- guardian passwords

based on institute-defined patterns.

This is especially useful for institutes that want:

- cleaner record standards
- less manual credential creation
- a predictable institutional format

### Hidden And Useful Point: Optional Guardian Support

Not every student record in every institute comes with a clean guardian login setup from day one.

Innovorix supports that practical reality.

Student records can still exist even if guardian setup is not complete yet.

### Attendance Visibility

Admin can see attendance percentage alongside student records.

This makes the student page more informative than just a profile list.

### Tags And Segmentation

Tags help the institute categorize students for internal workflows.

This can support:

- special follow-up groups
- internal academic categories
- administrative grouping
- future segmentation for communication or reporting

### Why This Matters

This page becomes the living core of the institute record system.

If student and guardian management is weak, every other module becomes harder to run.

Innovorix makes this page operationally strong through:

- linked admission handling
- smart credential generation
- bulk operations
- roll number conflict resolution
- class-change support
- communication access

### Marketing-Friendly Angle

This can be positioned as:

`A complete student and guardian record system that actually supports admissions and day-to-day institute work.`

---

## Admin Attendance Page

### Purpose

This page is where daily attendance becomes organized, visible, and reportable.

### Main Capabilities

- open any class or section
- mark attendance
- review earlier attendance by date
- edit attendance where needed
- download reports for one class
- download reports across multiple classes
- export date-range attendance to CSV

### Class-Day Restriction

Attendance can only be marked on days the selected class actually meets, based on its timetable. The date picker disables non-class days (weekends and any weekday the class has no timetable slots) and highlights valid class days, with a "Class days" hint listing them. The same rule is enforced on save, so admins and teachers cannot record attendance for a non-class day even via the API. A class with no timetable configured is left unrestricted so it is never locked out of attendance.

### Absence Alerts That Say What Was Missed

When a child is marked absent, the alert their guardian receives (in the app, on the phone and on WhatsApp) checks what that child's own class and section had booked for the day. If an exam paper, a quiz or a homework deadline fell on it, the alert names it, so the guardian learns their child missed the Physics paper rather than just that they were away. If several things fall on one day, the alert names the most serious one: an exam first, then a quiz, then a homework deadline. Work set for another section of the same class is never mentioned, because that child did not miss it. On a day with nothing booked the alert reads exactly as it always has, and either way only one message is sent.

### Role Strength

Even though teachers commonly mark attendance, the admin role can still manage attendance operationally.

This is useful when:

- the institute wants office oversight
- attendance must be corrected
- reports must be prepared centrally
- the office must verify whether attendance was marked

### Bulk Report Handling

The page includes a bulk report workflow that can:

- choose multiple class-sections
- choose a date range
- export combined attendance data

This is helpful for:

- audits
- parent meetings
- management reviews
- compliance summaries

### Daily Usefulness

The admin can see how many class-sections were marked today.

That gives a simple but useful operational signal.

### Smart Controls

- invalid future attendance dates are prevented
- filtered class/section selection keeps the page practical
- date-range exports are available without needing outside spreadsheets first

### Why This Matters

Attendance is one of the most frequently used workflows in any institute.

If attendance data is hard to enter or hard to extract, staff confidence drops quickly.

Innovorix improves this by combining:

- daily marking
- date-based review
- report generation
- class-based organization

### Marketing-Friendly Angle

`Easy daily attendance, strong reporting, and better administrative control.`

---

## WiFi Attendance (Smart Attendance)

### Purpose

Attendance that proves presence instead of trusting it. The institute saves the WiFi surroundings of its own building, and every check-in is compared against them: staff check in with one tap when they arrive, and students mark themselves present by scanning a QR code the teacher shows in class. The comparison happens on the server, so a record cannot be faked by editing what the phone sends.

### How Verification Works

- The admin walks to each spot where check-ins should work and captures the nearby WiFi networks into a named location. Several capture points merge into one location, so a large campus is covered by capturing from a few good spots.
- A check-in matches a location when at least two of its saved networks are audible and the strongest one is loud enough. One network disappearing is normal; two rules out coincidence.
- Every verdict shown in the app explains itself on hover: which networks matched, how strong they were, and which threshold decided the outcome.

### Staff Check-In

- Staff see a check-in card on their dashboard. One tap when they arrive, one tap when they leave.
- Arriving after the configured day start plus grace period marks the day Late instead of Present.
- No internet in the building corner where they checked in: the tap is saved on the phone and sent automatically once the connection returns, with the original time and the original WiFi evidence, which the server re-verifies on arrival.
- Admins get a staff attendance page per date: who is in, who is late, who is missing, and how each check-in was verified.

### Student QR Sessions (Beta)

- The teacher starts a QR session for their class; the code on screen changes every half minute, so a screenshot sent to a friend stops working almost immediately.
- Each student scans the code inside the app. The phone quietly reads the strongest nearby WiFi networks and sends them with the scan.
- The server compares every student's surroundings with the rest of the class. A student sitting at home matches nothing and is flagged instantly. A student sitting just outside the room hears the same networks noticeably weaker and is marked suspect for the teacher to decide.
- The teacher watches a live counter of scanned and missing students, reviews the flagged list, and closes the session, which writes the normal daily attendance record, respects approved leaves, and notifies guardians of absences the same way manual marking does.
- Phones that cannot read WiFi (older app versions, or a plain browser) still check in; they are simply labelled unverified so the teacher knows the scan carried no proof.

### Per-Lecture Mode For Universities

- The institute type (School, College, University, Academy, Madrasa) is now editable in settings, and universities and colleges are pointed at a per-lecture attendance mode.
- In per-lecture mode every teacher runs a QR session for their own lecture, and the daily record is derived from those sessions: a student who attended at least half of the day's lectures counts present for the day, so every existing report and guardian alert keeps working unchanged.
- Leave requests adapt with the mode: the student is told the request will be visible to all teachers who take their class, all of those teachers can review it, and approval notifications reach the same set.

### Honest Limits

WiFi evidence is strong but not absolute, which is why the student flow carries a Beta tag. The corridor-outside-the-room case is surfaced as suspect rather than silently accepted or rejected, and the teacher always has the final word. Reading WiFi requires the Android app with location permission granted; the feature asks for it with a plain-language explanation before the system prompt appears.

### Marketing-Friendly Angle

`Attendance that proves people were actually there.`

---

## Admin Leaves Page

### Purpose

This page organizes student leave handling in a more disciplined way than message-based approvals.

### Main Capabilities

- view pending leave requests
- view leave history
- open request details
- review attachments
- approve leaves
- reject leaves
- add reviewer comments
- understand guardian approval status

### Leave Workflow Depth

This is not a flat yes/no leave page.

It supports more realistic leave handling such as:

- guardian approval first
- teacher approval next
- bypass cases
- attachment support
- leave type behavior
- comments and review identity

### Why This Is Useful

Institutes often face confusion in leave handling because requests are split across:

- WhatsApp messages
- call records
- verbal instructions
- notebook notes

Innovorix gives the institute a cleaner record with:

- status
- date set
- reason
- attachment
- reviewer
- comments
- guardian context

### Nice Operational Point

Bypassed guardian approvals are still visible.

That means the institute does not lose approval context even when the workflow needs flexibility.

### Another Strong Point

Advance notice requirements can be configured by leave type.

This supports different institute expectations for:

- casual leave
- planned leave
- emergency leave
- document-required leave

### Why Leadership Should Care

A formal leave workflow improves:

- discipline
- clarity
- auditability
- parent trust

---

## Admin Assessments Page

### Purpose

This page manages smaller academic evaluation work such as assignments and quizzes.

### Main Capabilities

- create assignments
- create quizzes
- filter by class
- filter by subject
- filter by type
- edit assessments
- delete assessments
- review submissions

### Why The Assignment And Quiz Separation Matters

Some systems mix everything into one simple item list.

Innovorix separates assessment types more clearly.

This helps with:

- cleaner academic understanding
- better teacher workflow
- more meaningful student visibility
- better reporting language

### Role-Based Visibility

The page is role-aware.

That means:

- admin sees broadly
- teacher sees assigned relevance
- student sees only what belongs to them

### Why This Matters

This keeps the system from feeling overloaded while still staying powerful.

### Marketing-Friendly Angle

`Assignments and quizzes managed in a cleaner, more structured academic workflow.`

---

## Admin Exams Page

### Purpose

This page manages the larger formal academic evaluation cycle.

### Main Capabilities

- create exams
- create exam sessions
- assign classes and sections
- define subject slots
- define dates
- define timings
- define total marks
- manage grade entry
- track grading completion
- view datesheets
- archive exams into history
- archive entire exam sessions into history
- restore archived sessions

### Session-Based Organization

Exam sessions are a major strength.

Instead of creating disconnected exam items forever, the institute can group them into named sessions such as:

- monthly test cycle
- mid-term
- term exams
- annual exams

This keeps the page much more organized over time.

### Datesheet Building

Only the first paper of an exam is typed out in full. Every paper added after it
is proposed from the one above: the next subject that has no paper yet, the same
start and end time, the same total marks, and the next date.

The gap between dates repeats whatever gap was last set by hand, counted in
teaching days. Setting the second paper two days after the first puts the third
two days after the second.

Teaching days come from the timetables of the classes actually sitting the exam,
so a day those classes do not meet is never proposed. Weekends are skipped;
classes with no timetable fall back to Monday to Friday.

Every proposed value can be overwritten, and the change feeds the next proposal.
Once every subject taught in the selected classes has a paper, no more can be
added and the button says so.

### Grade Entry Workflow

Marks are entered inside a structured grade-entry dialog.

The system helps protect data quality by validating marks.

If marks exceed total marks, the system does not silently accept bad values.

### Progress Tracking

Section-level progress indicators show how much grade entry is complete.

Choosing which section to mark opens a searchable list showing, for each one,
how many of its marks entries are filled and how many are expected, and how many
sections are finished overall. It stays inside the screen however many classes
the exam covers.

This is very helpful during active exam periods when the institute wants to know:

- which sections are complete
- which teachers may still have pending work

### History Handling

The system supports moving:

- a single exam
- or a whole exam session

into history.

This keeps the active exam area cleaner without deleting long-term records.

### Why This Matters

Exam clutter becomes a real issue in growing institutes.

Session grouping plus history management helps the institute stay organized year after year.

### Datesheet Benefit

Students can access datesheet-oriented visibility, making the exam experience more practical for end users too.

### Marketing-Friendly Angle

`Formal exam management with cleaner session control, grade validation, and progress visibility.`

---

## Admin Marksheet Page

### Purpose

This page turns stored marks into result visibility.

### Main Capabilities

- search students by name or ID
- browse by class
- open marksheet views
- support report-card style result access
- support transcript-style result access

### Why This Matters

Marks entry has little operational value if the institute cannot later open and use the results clearly.

This page helps bridge that gap.

### Practical Office Use Cases

- result checking
- parent meeting preparation
- quick office verification
- result viewing support

### Strong Usability Point

Search makes result retrieval fast.

That matters a lot for office staff during busy result periods.

### Marketing-Friendly Angle

`From marks entry to clear marksheet access with less search effort and better result presentation.`

---

## Admin Fees And Payments Page

### Purpose

This is one of the most commercially important modules in Innovorix.

It handles fee planning, fee generation, fee visibility, fee status, and fee continuity.

### Main Capabilities

- create fee sessions
- create fee campaigns
- add multiple fee components
- assign campaigns to classes
- generate fees in bulk
- mark fees as paid, one student or a whole class at a time
- manage draft sessions
- activate sessions
- delete individual fees
- delete fee campaigns
- open and print challans
- use templates
- receive template-based suggestions
- review fee status

### Reading The Fee Status Screen For One Class

Once a class is picked, the screen opens with the class's own breakdown across the top:
how many challans exist in total, how many are paid, how many are still due and how many
have gone past their date, each with the money that group is worth, and a bar showing the
share of the billed money that has actually come in. Those four cards are also the filter:
tapping one narrows the list underneath to that group, and the counts stay class-wide so
they keep their meaning while a filter is on. Hovering a card says what puts a challan in
that group, including why a part paid challan stays under Due or Overdue rather than
moving to Paid.

### Collecting From A Whole Class At Once

When a class pays together, the fee list lets an admin or accountant tick the students
concerned and record all of those payments in one step, instead of opening each row on its
own. Ticking rows reveals a "Mark as paid" button, and before anything is written a
confirmation names how many students are involved, the total being recorded and every
student with their class, section and amount. Challans that are already paid are shown but
left alone.

The whole batch is written together, so if anything fails no student in that class is left
half-recorded, and the result reports how many were marked paid and how many were skipped.
Only an admin, accountant or super-admin can do this; the check happens on the server, and
every selected challan is re-checked against the caller's own institute before it is
touched.

### What A Fee Session Means

A fee session is a broader collection container for one fee cycle or period.

For example:

- January 2026
- Spring Session
- Admission Cycle
- Monthly Fee Batch

### What A Fee Campaign Means

Inside a fee session, the institute can create one or more campaigns.

A campaign may represent:

- monthly tuition
- lab fee
- transport-related fee
- composite fee set

### What A Fee Contains

A generated fee may include:

- student
- class targeting source
- session
- campaign
- fee components
- due date
- total amount
- payment status
- late fee logic

### Draft Session Strength

This is a major operational feature.

Admin can prepare a fee session as draft first.

That means:

- planning can happen before going live
- review can happen first
- accidental notices can be avoided
- the institute can work more carefully

### Hidden And Very Attractive Point: Duplicate For Next Session

This is one of the strongest “less double work” features in the project.

The platform includes a multi-step next-session duplication wizard.

The admin can choose an earlier fee session and create the next one using that previous structure as the base.

The wizard can pre-fill:

- new session name
- fee campaign structure
- fee component amounts
- class selections
- due date suggestions

Then the admin only reviews and confirms.

This is very useful for recurring fee cycles.

Instead of rebuilding routine monthly fee structures from scratch every time, the institute can move faster with more consistency.

### Hidden And Useful Point: Save As Template

Campaigns can be saved as templates.

These templates then help drive future suggestions and reduce repeated configuration.

### Hidden And Useful Point: Duplicate Protection With Flexibility

The system protects against accidental duplication.

But it also allows intentional duplication when the institute genuinely needs multiple campaigns with the same name for the same class context.

That balance is practical.

### Late Fee Visibility

Late fee rules connect into the challan experience.

This improves clarity for students and guardians.

### Why Institute Leadership Should Care

This page is not just about fee creation.

It affects:

- cashflow discipline
- fee record consistency
- staff workload
- parent transparency
- error reduction

### Marketing-Friendly Angle

`A fee system built not just for record keeping, but for recurring fee operations, review control, and faster monthly execution.`

---

## Admin Fee Defaulters Page

### Purpose

This page isolates overdue fee follow-up into a dedicated workflow.

### Main Capabilities

- choose a fee session
- see total defaulters
- see overdue amount
- see affected classes
- filter by class
- filter by overdue days
- filter by amount range
- export defaulters to CSV
- mark selected fees as paid
- mark individual fees as paid
- send reminders

### Reminder Handling

The reminder workflow can use:

- WhatsApp
- in-app notifications
- or both

### Recovery Insights

A second tab on the same page turns the overdue list into a recovery picture, using the payment ledger that records when each instalment actually arrived. For every student who still owes something it shows how many challans were paid on time, paid late or missed, the average number of days late, what is outstanding and how long it has been overdue, plus a behaviour band: **Always Pays On Time**, **Occasionally Late**, **Frequent Late Payer** or **High-Risk Defaulter**. A month-by-month strip shows the last twelve months at a glance, and students with repeated defaults or delays that are growing are flagged.

A recovery score out of 100 estimates how likely the outstanding money is to come in. The formula is printed on the page, every contributing signal is shown next to the score, and hovering or focusing any band, score or month cell explains why that student has that value.

Two limits are stated rather than papered over. A challan the office closed before itemised payments existed carries no payment date, so whether it was late is unknowable: those are counted separately as "timing unknown" and never assumed on time. And a student with only one or two concluded challans gets no band and no score at all, because two months is not a pattern. The sample size sits next to every judgement.

Because this exposes how individual households handle money, the tab is limited to administrators and accountants of that institute.

### Why This Is Strong

Many systems force staff to find defaulters manually inside a long fee list.

Innovorix gives the institute a proper recovery-focused page.

### Operational Benefits

- finance staff can focus only on overdue cases
- class-wise follow-up becomes easier
- the office can isolate higher-risk dues faster
- reminders can happen from the same context

### Hidden Strength

Reminder handling runs in the background, so the office does not need to stop all work while notifications are being processed.

### Marketing-Friendly Angle

`A dedicated fee recovery page, not just a generic fee list.`

---

## Admin Payment Proof Review Page

### Purpose

This page handles proof-based payment confirmation.

It is especially useful for institutes where payment may happen externally and the user later submits evidence.

### Main Capabilities

- view pending payment proofs
- review uploaded proof details
- approve proof
- reject proof
- add review notes
- notify the student
- review past decisions in history
- filter history by class
- filter history by fee session
- filter history by approval status

### Why This Matters

Without this workflow, many institutes face one of two problems:

- office staff mark fees paid informally without a controlled review flow
- or students keep sending screenshots manually with no traceable process

Innovorix improves this through:

- pending review queue
- approval and rejection handling
- review history
- notification feedback

### Approval Behavior

When a proof is approved:

- the fee can be marked paid
- the review history becomes part of the fee workflow

### Rejection Behavior

When a proof is rejected:

- notes can explain why
- the student is informed

### Why A Principal Or Owner Should Care

This workflow reduces confusion between:

- proof received
- proof reviewed
- payment accepted
- payment rejected

That is especially valuable in institutes with growing student volume.

### Marketing-Friendly Angle

`Controlled payment proof review that brings discipline to off-platform fee collection scenarios.`

---

## Admin Library Page

### Purpose

This page handles the institute’s library circulation and book record workflows.

### Main Capabilities

- maintain book catalog
- add books
- edit books
- delete books
- issue books
- return books
- view circulation
- track overdue books
- manage fine collection logic
- view total books, issued books, overdue books, and total members

### Catalog And Circulation Split

The page is structured around meaningful library work areas such as:

- catalog
- circulation
- fines

This makes the role easier to use.

### Overdue Fine Strength

Library fine rules are connected into the circulation workflow.

That means fines are not just a side note.

They become part of return handling.

### Operational Benefits

- books are not just stored, but tracked
- overdue follow-up becomes clearer
- book return handling becomes more formal
- fines become more visible and more consistent

### Marketing-Friendly Angle

`A real library operations page, not only a static book inventory.`

---

## Admin Promotion Page

### Purpose

This page handles one of the most sensitive academic year-end workflows: student promotion.

### Main Capabilities

- choose academic session
- choose source class-section
- choose target class-section
- select eligible students
- confirm promotions
- see already-promoted students
- use single-class promotion
- use bulk promotion across many classes

### Single Promotion Mode

This is useful when the institute wants careful, class-by-class promotion control.

Admin can:

- choose the current class-section
- choose the target class-section
- select students
- confirm movement

### Bulk Promotion Mode

This is useful when the institute wants larger-scale execution.

Admin can:

- work across many class-sections
- set a target for all students in one class block
- or select different targets student by student

### Important Hidden Strength

Bulk promotion is not only class-aware.

It is section-aware too.

That matters because real institutes often promote not only to the next class, but also to the correct next section structure.

### Protection Against Duplicate Promotion

Students already promoted for the selected academic session are clearly identified.

This reduces mistakes during year-end operations.

### Promotion History Value

Promotion history stays attached to session context.

This improves longitudinal record quality.

### Marketing-Friendly Angle

`Smart promotion handling for both careful class-by-class movement and large year-end promotion cycles.`

---

## Admin Communication Monitoring

### Purpose

This gives administrative oversight over institute communication flows.

### Main Capabilities

- review communication environment
- monitor structured conversations
- use message supervision functions

### Why This Matters

When communication moves into the system, the institute gains:

- structure
- visibility
- less dependency on personal message trails

### Marketing-Friendly Angle

`More controlled institute communication, with less dependence on scattered informal channels.`

---

## Admin Settings Page

### Purpose

This page is the configuration backbone of Innovorix.

### Main Areas Included

- profile
- password
- security
- institute information
- admission fee setup
- fee management setup
- sibling discount setup
- library fine setup
- email and ID pattern setup
- tag management
- notifications
- appearance

### Institute Information Setup

Admin can maintain:

- institute name
- institute email domain
- contact information
- timezone
- address
- timetable display mode

### Admission Fee Configuration

Admin can define admission fee rules by class group.

This is useful because admission handling is often not the same across all classes.

The platform can then use these rules to support the admission process.

### Late Fee Configuration

Admin can define:

- late fee rules
- grace period for newly admitted students
- default due date behavior

This is a strong operational feature because new admissions often happen mid-cycle, and the platform avoids immediately treating such students unfairly as overdue.

### Sibling Discount Configuration

Admin can enable structured sibling discount logic based on guardian-linked children.

This is useful for institutes that want policy consistency in discounts.

### Library Fine Configuration

Admin can define overdue fine rules centrally so library handling follows policy rather than informal staff judgment.

### ID And Password Pattern Configuration

Admin can configure institutional identity standards for:

- students
- staff
- guardians

This includes pattern preview and password source logic.

This is one of the stronger professionalization features in the product.

### Security And MFA

Security settings help the institute use stronger account protection.

### Notifications

Notification preferences and mobile permission handling connect into the broader communication experience.

### Why This Matters

A strong ERP becomes more valuable when it is configurable without becoming chaotic.

Innovorix gives admin control over important institutional behavior without making daily users deal with configuration complexity.

### Marketing-Friendly Angle

`Strong operational settings that help the institute standardize how it works, not just store data.`

---

## Admin Role Summary In Plain Sales Language

The Admin role in Innovorix gives an institute a digital operating center for:

- people
- classes
- timetables
- fees
- attendance
- leave control
- exams
- results
- parent visibility
- promotion
- institutional standards

That is why the Admin role is one of the strongest product stories in the platform.

---

</details>

<details>
<summary><strong>Teacher Role, Teacher Pages, And Teacher Workflows</strong></summary>

# Teacher Role

## Teacher Role Summary

The Teacher role is designed to stay practical.

It is not overloaded with institute-wide controls.

Instead, it focuses on what teachers need most often:

- class visibility
- attendance
- assignments
- exam marks
- leave review
- timetable
- communication

This keeps teacher adoption easier.

---

## Teacher Dashboard

### What The Teacher Sees

- number of assigned classes
- number of own students
- number of assignments waiting for grading
- next exam visibility
- notices
- timetable summary

### Why This Matters

The teacher dashboard helps a teacher understand daily workload quickly.

It is a focused dashboard rather than a management dashboard.

### Strong Points

- class count stays clear
- student count stays clear
- grading workload stays visible
- schedule stays visible

---

## Teacher Attendance Page

### Main Capabilities

- mark attendance for assigned classes
- review previous attendance
- edit when needed
- download reports for own class context

Attendance can only be marked on the class's scheduled days; the date picker disables weekends and any weekday the class does not meet (and the rule is enforced on save).

### Useful Workflow Detail

Low attendance visibility helps teachers notice students who may need attention.

### Parent-Related Value

Attendance data later supports guardian visibility, which makes teacher work more meaningful institution-wide.

---

## Teacher Assessments Page

### Main Capabilities

- create assignments
- create quizzes
- edit assessments
- delete assessments
- review submissions

### Why Teachers Benefit

This keeps smaller academic evaluation work organized without needing separate tools.

### Strong Product Point

Teachers are not forced to work through an admin-heavy workflow to manage class tasks.

---

## Teacher My Students View

### Main Capabilities

- see students from assigned classes
- review class-linked student lists

### Why This Matters

This is especially useful for day-to-day teaching workflows where teachers need focused access without institute-wide exposure.

---

## Teacher Leave Requests

### Main Capabilities

- review leaves pending teacher approval
- see attachments
- see guardian approval state
- see comments and context
- approve or reject with comments

### Why This Matters

Teachers often become the final operational approver of student leave in a class-level workflow.

The product supports that directly.

---

## Teacher Exams Page

### Main Capabilities

- enter marks for assigned students
- work within relevant subject scope
- use structured grade entry
- benefit from mark validation
- see completion progress

### Why Teachers Benefit

Marks entry becomes cleaner and more guided.

### Important Quality Point

The system protects against invalid marks beyond allowed totals.

---

## Teacher Communication

### Main Capabilities

- communicate with guardians
- start conversation from class context
- read and reply in structured threads
- mute/unmute conversations

### Why This Matters

Teacher-parent communication becomes more institutional and less dependent on informal scattered messages.

---

## Teacher Timetable

### Main Capabilities

- view personal timetable
- see consolidated schedule across assigned classes

### Why This Matters

A teacher does not have to inspect each class manually.

The platform brings schedule visibility together.

---

## Teacher Settings

### Main Capabilities

- profile management
- password management
- security settings
- notification settings
- appearance settings

### Why This Matters

Teacher usability improves when account control is self-service instead of office-dependent.

---

## Teacher Role Summary In Plain Sales Language

The Teacher role in Innovorix helps teachers focus on teaching operations rather than admin clutter.

It gives them:

- the right academic tools
- the right class visibility
- the right communication access
- the right timetable access

without exposing them to unnecessary institute-wide controls.

---

</details>

<details>
<summary><strong>Student Role, Student Pages, And Student Experience</strong></summary>

# Student Role

## Student Role Summary

The Student role is designed around personal visibility.

It helps the student see:

- what they must do
- where they stand
- what is due
- what is scheduled
- what has been recorded about them

This reduces uncertainty and improves engagement.

---

## Student Dashboard

### Main Value

The student dashboard is a personal learning and record view.

### What The Student Can Understand Quickly

- notices
- timetable
- recent academic visibility
- attendance-related context

### Why This Matters

The student is not forced to depend on office staff or teachers for every basic update.

---

## Student Assessments Page

### Main Capabilities

- view assignments
- view quizzes
- submit assignment work where applicable
- understand due work in a structured way

### Why This Matters

The student side is not only about passive viewing.

It also supports participation in academic workflows.

---

## Student Attendance Page

### Main Capabilities

- view personal attendance history
- understand attendance status more clearly

### Why This Matters

The student can monitor their own record instead of waiting for result-time surprises.

---

## Student Leaves Page

### Main Capabilities

- apply for leave
- choose leave type
- choose date range
- provide reason
- attach documents where required
- route request into the proper approval flow

### Hidden And Useful Point

The leave system can support guardian approval before teacher approval.

That makes the student workflow more institutionally safe.

### Another Useful Point

Advance timing rules help prevent invalid late submission for planned leave types.

---

## Student Exams Page

### Main Capabilities

- view exams
- view datesheet
- see marks visibility

### Why This Matters

The student is not disconnected from the formal exam cycle.

They can see what is relevant to them.

---

## Student Marksheet Page

### Main Capabilities

- open own result view
- see report-card style outcome
- see transcript-oriented result access where supported

### Why This Matters

Result visibility becomes direct and easier.

---

## Student Fees Page

### Main Capabilities

- view challans
- view payment history
- see fee status
- upload payment proof where allowed

### Strong Product Point

The student fee page is more than a passive balance page.

It is part of a broader fee workflow connected to:

- payment proof review
- late fee logic
- status handling

### Useful Visibility

Statuses like:

- Due
- Overdue
- Paid
- Pending Review

help the student understand where the record currently stands.

---

## Student Timetable

### Main Capabilities

- view personal weekly timetable

### Why This Matters

Schedule visibility on the student side is a practical everyday need.

---

## Student Settings

### Main Capabilities

- profile
- password
- security
- notifications
- appearance

### Why This Matters

Students can manage core account behavior without depending on office help for everything.

---

## Student Role Summary In Plain Sales Language

The Student role makes Innovorix useful at the learner level, not only at the admin level.

It helps students:

- stay informed
- stay organized
- stay aware of attendance
- stay aware of fees
- stay aware of exams and results

---

</details>

<details>
<summary><strong>Guardian Role, Guardian Pages, And Parent Visibility</strong></summary>

# Guardian Role

## Guardian Role Summary

The Guardian role is one of the most commercially attractive sides of the platform.

Why?

Because parent visibility is a major buying driver for many institutes.

Guardians want more than fee messages.

They want meaningful visibility into the child’s institute life.

Innovorix supports that through:

- child attendance view
- child marksheet view
- child fees view
- leave approval workflows
- teacher communication
- dashboard summaries

---

## Guardian Dashboard

### What The Guardian Sees

- number of children
- average attendance
- academic performance
- total exams
- child-specific performance cards
- due fee visibility

### Why This Matters

The guardian does not need to explore many pages just to understand the child’s current status.

The dashboard provides useful summary visibility immediately.

### Strong Product Point

When multiple children exist, the guardian experience still remains usable.

---

## Guardian Communication

### Main Capabilities

- message teachers
- choose child context first
- continue structured conversation threads

### Why This Matters

This supports a more professional parent-teacher communication structure.

---

## Guardian Attendance Page

### Main Capabilities

- view attendance child by child
- enter deeper detail for a selected child

### Why This Matters

Attendance is one of the most requested parent-side visibility features in real institute use.

---

## Guardian Leaves Page

### Main Capabilities

- review pending leave requests from child side
- approve or reject child leave requests
- create leave directly on behalf of a child
- see bypass cases
- understand approval state

### Strong Workflow Point

Guardian-created leaves and student-created leaves are both handled meaningfully.

This supports real institute behavior instead of assuming only one submission path.

### Why This Matters

The guardian becomes part of the official leave flow rather than an informal outside confirmer.

---

## Guardian Marksheet Page

### Main Capabilities

- view marksheet for one child
- view marksheet for multiple children
- use latest-result preview before opening deeper marksheet

### Why This Matters

This increases academic transparency for families.

---

## Guardian Fees Page

### Main Capabilities

- view child challans
- view fee statuses
- upload payment proof
- follow dues more clearly

### Why This Matters

This reduces routine office calls about:

- whether a fee exists
- whether it is due
- whether proof has been reviewed

---

## Guardian Settings

### Main Capabilities

- profile
- password
- security
- notifications
- appearance

### Why This Matters

Guardians can maintain their own experience more independently.

---

## Guardian Role Summary In Plain Sales Language

The Guardian role turns Innovorix into a family-visible institute platform rather than an office-only system.

This is important for trust, convenience, and institute professionalism.

---

</details>

<details>
<summary><strong>Accountant Role And Finance-Focused Access</strong></summary>

# Accountant Role

## Accountant Role Summary

The Accountant role focuses on the financial operation side of the institute.

This role is intentionally more focused than the Admin role.

Instead of managing the entire institute, the Accountant role centers on:

- fee visibility
- fee processing workflows
- proof review workflows
- payment status handling

This is useful for institutes that want finance staff to work digitally without giving them broader academic control.

---

## Accountant Dashboard

### Main Value

The dashboard helps the accountant enter the finance side of the product quickly.

Even when a role has fewer modules than admin, a dedicated access path still matters for usability.

---

## Accountant Fees Page

### Main Capabilities

- access fee records
- review fee campaign outcomes
- handle collection-side visibility
- mark fee records as paid where role permissions apply
- review challans and statuses

### Why This Matters

For many institutes, the person handling fee collection should not also need full access to:

- class creation
- staff management
- institute settings
- promotion

The Accountant role solves that by staying finance-focused.

### Useful Finance Value

The Accountant can work inside a proper fee system that already supports:

- fee sessions
- fee campaigns
- challans
- statuses
- review-based payment updates

This is stronger than manually tracking collection updates in spreadsheets.

---

## Accountant Payment Proof Review Page

### Main Capabilities

- view pending proofs
- approve proofs
- reject proofs
- add notes
- review history
- filter reviewed records

### Why This Matters

For institutes using external or semi-external payment flows, this gives the finance side a proper approval station.

### Practical Benefits

- clearer accountability
- fewer “I already sent screenshot” disputes
- better review history
- cleaner paid versus pending distinction

---

## Accountant Role Summary In Plain Sales Language

The Accountant role gives finance staff a more disciplined digital collection workflow without opening up unrelated institute management areas.

That makes it easier to assign finance work safely inside the same platform.

---

</details>

<details>
<summary><strong>Librarian Role And Library Operations</strong></summary>

# Librarian Role

## Librarian Role Summary

The Librarian role focuses on running the library side of the institute cleanly.

Instead of giving librarians broad admin access, the role stays aligned to:

- book catalog handling
- circulation
- issue-return workflows
- overdue handling
- fine handling

This keeps library work efficient and secure.

---

## Librarian Dashboard

### Main Value

The dashboard acts as the entry point into the library workflow.

For a focused operational role, that matters because the role can move quickly into the relevant module without distraction.

---

## Librarian Library Page

### Main Capabilities

- manage book catalog
- add books
- edit books
- remove books
- issue books
- return books
- see currently borrowed books
- see overdue books
- use fine-aware return workflows
- manage circulation from one place

### Why This Matters

In many institutes, library work is either:

- barely digitized
- or managed in a tool disconnected from the main institute system

Innovorix improves that by keeping the library connected to the same broader environment.

### Fine Handling Value

Library overdue fine rules are not separate theory.

They connect into actual circulation handling.

That helps the librarian apply policy more consistently.

### Practical Benefits

- easier overdue tracking
- cleaner issue-return records
- more structured fine handling
- better member-level circulation awareness

---

## Librarian Role Summary In Plain Sales Language

The Librarian role gives an institute a real circulation workflow instead of a passive library register.

That strengthens the product’s image as a complete institute operations platform.

---

</details>

<details>
<summary><strong>Roles &amp; Permissions: Delegating Work A Job Role Does Not Cover</strong></summary>

# Roles &amp; Permissions

An institute's job roles are fixed, and the role a member of staff is created
with cannot be changed afterwards. Real institutes do not work that way: one
teacher runs exams for every class, another collects fees alongside the
accountant, a third is trusted to admit students and keep guardian records
straight. Before this there were only two answers, and both were wrong - make
the person an Admin and hand them everything, or leave them locked out.

**Settings → Roles &amp; Permissions** (Admin and SuperAdmin only) is where an
admin creates a **permission role**: a named bundle of extra abilities, such as
"Exam Controller" or "Fee Desk", that can then be given to whoever is doing that
work.

## The rule that makes it safe

A permission role **only ever adds**. It can never take an ability away from
anyone, so nothing that works today can stop working because a role was created
or assigned. Somebody holding one keeps everything their own job role allows and
gains what the role lists on top.

## Creating one

1. **What is it for** - a name staff will recognise, and a one-line description.
   The description is not decoration: it is what the person reads when a page
   they have never had before appears in their menu.
2. **What can it do** - a page-by-page grid, grouped into People, Academics,
   Money, Operations and Communication, with View / Create / Update / Delete
   boxes per page. Search, select-all and per-group counts keep it usable at
   twenty-one pages, on a phone as well as a desktop.

Every module carries a badge saying how much a tick is really worth:

- **Fully enforced** - Students &amp; Guardians, Fees and Exams. Every tick is
  checked on the server.
- **Page access only** - everything else. The tick adds the page and the menu
  entry; the buttons on that page still follow the person's own job role.

## Giving it to somebody

Two doors onto the same records, so they can never disagree:

- **Settings → Roles &amp; Permissions → Members** on the role itself, which also
  shows who else holds it.
- **Staff → edit a member of staff → Extra permissions**, right under the job
  role, which is locked after the account is created.

Only staff accounts can hold one. Students and guardians are refused on the
server, not only hidden in the picker, because giving a family the roster would
show them every other family's records.

**Pausing** a role (the Active switch) stops it granting anything while keeping
the list of who held it, so a delegation can be suspended for a term and handed
back untouched. **Deleting** one says how many people lose how many pages before
it does anything, and offers pausing instead.

## What the person sees

Pages their job role does not include appear in their own **Delegated to you**
block at the foot of the menu, with a key icon and an amber accent. Hovering one
says which role granted it and exactly what it allows - "Your administrator gave
you the Exam Controller role, which adds this page: full access. Your own Teacher
role does not include it."

Where they already had the page, nothing is duplicated; the page simply widens.
A teacher given Exams stays on the same Exams page but now sees every class in
the institute, can create an exam for any of them, and gets the datesheet and
history controls that were previously administrator-only. What they may **type
marks into** is unchanged: running an exam for a class is not the same as marking
a subject you do not teach.

A grant reaches the person within five minutes without them signing out, and is
withdrawn just as quickly.

## In the demo institute

- **Exam Controller** → Demo Teacher (`teacher@demo.innovorix.com`)
- **Fee Desk** → Nadia Aslam, working alongside the real accountant
- **Front Desk** → the librarian, admitting students
- **Exam Controller (last year)** → paused, so the paused state has an example

---

</details>

<details>
<summary><strong>Student Risk Detection, Early Warnings, And Child Wellbeing</strong></summary>

# Student Risk Detection

## Purpose

A dedicated early-warning page that proactively flags students who may need intervention, instead of leaving staff to notice problems by hand once they're already serious.

---

## How Risk Is Measured

Each student gets a 0-100 risk score blended from three factors, each weighted:

- **Attendance Risk (40%)** — low or declining attendance
- **Academic Risk (35%)** — low or falling grades, failed assessments
- **Financial Risk (25%)** — overdue fees and late payments

The score is banded as 0 No Risk, 1-24 Low, 25-49 Medium, 50-74 High, 75-100 Critical, shown with green through red badges.

A factor with no data is shown as "Insufficient data" and left out of the score, with the remaining factors reweighted, so missing data never inflates or lowers a student's risk.

Attendance follows the institute-wide rule: approved leave is excluded from the calculation entirely, so a student who was legitimately away is never counted as absent and is never flagged for it. A student with no countable attendance days simply has no attendance risk rather than a misleading zero.

The time range is adaptive (Last 7 Days / 30 Days and so on, based on institute age), and a previous-period comparison drives **alerts**: _Needs intervention_, _Newly flagged_ (became a concern this period), and _Escalating_ (risk rising).

---

## How A Reader Understands The Numbers

The page states the full formula in plain English above the table, and every risk badge explains itself on hover or keyboard focus: the band it falls in, the numeric range of that band, and the exact signals that produced it for that student.

---

## Who Sees What

- **Admin / SuperAdmin / Accountant / Librarian** — all students school-wide, in a filterable, sortable table (filter by class, section, risk level, and minimum score) with alert summary cards.
- **Teacher** — only students in their assigned classes, same table view.
- **Guardian** — only their own children, in a supportive card view ("Doing well" / "Needs attention") with a short "what you can do" hint per child, with no alarming wording.

The role used for that scoping is taken from the signed-in session, never from the browser, so no one can request a wider view than their role allows.

The whole page loads from a single backend request and refreshes in one request when the range changes.

---

</details>

<details>
<summary><strong>Merit List And Topper Management</strong></summary>

# Merit List

## Purpose

The toppers of an exam, worked out the way medals are actually awarded on result day: inside each class and section, inside each class, or across the whole exam, instead of comparing class marksheets by hand.

---

## How It Works

Pick an exam and the page brings up the classes that exam is linked to, every one ticked to start with. Untick a whole class or a single section to leave it out, then press **Generate**.

**Award positions** decides what a place is measured within:

- **Per class and section** (the default) gives every class-section box its own first, second and third place. This is what result day needs: with ten classes you no longer have to pick one class, generate, read the top three, and repeat ten times.
- **Per class** ranks inside each class with all of its sections together.
- **Whole exam** is the single combined leaderboard across everything ticked.

Every group is shown at once, each with its own ranking restarting at 1, and each heading explains on hover exactly what its places are measured within. Students in a class with no section assigned get a group of their own rather than disappearing.

**Places that count as a medal** is a box, three by default. It controls both the highlighting on screen and what goes into the download. Students level on score share a place, so a tie for second produces two second places.

**Download toppers** produces a printable sheet of the medal winners, grouped exactly as shown, ready to print and hand out. Each group is kept whole on a page rather than being cut in half across two.

---

## How The Ranking Is Calculated

A student's score is the marks they obtained across the exam's papers, out of the marks those papers were worth, and the list runs from the highest percentage down.

- **Missing papers are never scored as zero.** The percentage covers only the papers the student actually sat, and every row shows "papers sat of papers their class sat". Because three papers out of eight cannot be compared fairly with eight out of eight, those students are left out of the ranking by default; a switch brings them back in, flagged **Incomplete**, with the missing paper names on hover.
- **"Their class's papers"** means the papers that class actually sat in this exam, so a junior class taking fewer subjects is never wrongly marked incomplete against a senior one.
- **Ties share a rank and the next rank skips** (1, 2, 2, 4). Nothing breaks a tie; tied rows are simply listed by name.
- **Students admitted after the exam's last paper never appear at all** — they were never enrolled for it, so they are not ranked and not counted as absent.

Every one of those rules is printed in plain English above the table, and hovering or focusing a rank or a score explains that student in particular: their total, out of what, over how many papers, and the exact gap to the students above and below them.

---

## Who Sees What

- **Admin / SuperAdmin / Teacher / Accountant** — the full merit list for their own institute (SuperAdmin across institutes).
- **Student / Guardian / Librarian** — no access; the page exposes every listed student's marks.

The role and the institute are read from the signed-in session, never from the browser, so a request for another institute's merit list returns nothing.

The page is read-only: it never creates or changes a mark. Building a list costs a fixed number of database queries whether the exam has five students or five hundred.

---

</details>

<details>
<summary><strong>MCQ Arena: Daily Quizzes, Titles, Streaks And The Public Question Bank</strong></summary>

# MCQ Arena

## Purpose

A free practice ground using the saved multiple choice question bank (General Knowledge, Pakistan and World Current Affairs, Pak Study, Islamic Studies, Everyday Science, Computer, English, Past Papers), playable by anonymous visitors on the public site and by every signed-in role in the dashboard. Solving is a game: XP, an eight-step title ladder from Newcomer to Legend, and a daily streak that resets when a day is missed.

---

## The Public Side

The **MCQs** item in the site navigation opens the free practice pages. Every subject can be read through page by page with answers behind a "Show answer" reveal, or played as a ten-question quiz with no account. Visitors can leave an email to receive one reminder each afternoon, with a one-click unsubscribe link in every mail. Subjects whose content goes stale (General Knowledge, Current Affairs) are marked **Dated content** and show when their bank was last updated, because office holders and records change.

---

## The Dashboard Side (MCQ Arena)

Every role gets the arena page: solve quizzes by subject, watch a thirty-day chart of questions per day and accuracy, and see the school's student leaderboard. Signed-in users can switch on a daily reminder and pick the hour; it arrives as an app notification only on days they have not solved yet.

- **Students** earn XP and titles; the title and live streak appear next to their name on the attendance page, on their profile, and to their guardian.
- **Guardians** see each child's title, streak and activity chart first, with a nudge to trade social media minutes for one quiz a day. Guardians can solve too.
- **Teachers and admins** additionally see school participation numbers and can upload their own subject's questions as a CSV (a sample file is provided). Uploads stay private to the school and mix into that school's quizzes only.

---

## Monitoring And Moving To A New Machine

Super admins open **MCQ monitoring** in the platform menu to see all subscriptions, active questions, the last worker check and 30-day quiz activity. Institute admins open the same item in their institute menu and see only linked users and activity from their own institute. Search, subscription status and pagination make individual subscribers easy to find. Reminder checks record sent, skipped, unavailable and failed counts; individual failures include a subscription identifier in the server logs.

Reminders pause when no accessible category can supply ten active questions. Public email signup also pauses when the shared bank cannot supply a full quiz. The worker checks at startup and hourly, and emails active super admins at most once per recipient per Pakistan calendar day after a successful alert. Failed alerts remain eligible for retry. `/api/health` also checks the question bank and recent worker activity, so a connected but empty database cannot pass the MCQ health check.

MCQ reminder, welcome and alert emails use **Innovorix <mcqs@innovorix.com>**. Set `MCQ_FROM_EMAIL` to override that address and `MCQ_FROM_NAME` to override the display name. Add this address to Cloudflare Email Routing and verify it as a sending alias for the configured SMTP account before sending emails from it. Other email senders retain their existing settings.

The repository carries the real question source files in `prisma/data/mcqs/`. Each CSV uses `Question,Option A,Option B,Option C,Option D,Correct Answer`, with the correct answer as A, B, C or D. Keep questions containing commas inside quotes. The expected filenames are `general_knowledge_mcqs.csv`, `pakistan-current-affairs-mcqs.csv`, `world-current-affairs-mcqs.csv`, `pak-study-mcqs.csv`, `islamic-studies-mcqs.csv`, `everyday-science-mcqs.csv`, `computer-mcqs.csv`, `english-mcqs.csv` and `past-papers.csv`. Send these files together as a ZIP from the old machine. The files currently contain only headers; real content must be restored before seeding can succeed.

Run `npm run db:seed:mcqs` to add missing shared questions without changing users, subscriptions or quiz history. The full seed uses the same importer and validates the bank before changing demo data. Empty or invalid source files produce a clear failure rather than a misleading success. Question hashes and database duplicate checks make repeated imports safe. Existing questions are preserved; inactive or institute-private duplicates may need review before they can serve as shared questions. Commit the source CSV files with the project so they travel to the next machine.

---

## How Scoring Works

Each correct answer earns 10 XP and a perfect quiz adds 20 XP. Only the first three quizzes a day earn XP; after that, play is unlimited but unscored. Solving at least one quiz a day grows the streak; a missed day resets it to zero. Titles are unlocked at fixed XP thresholds and every derived number on the page explains itself on hover.

---

## Why Copying Does Not Work

Every attempt draws its own random questions from the bank and shuffles the answer order, and the grading happens on the server against the served set. Two students sitting together get different quizzes, so reading a neighbour's results is pointless, and the daily XP cap means one afternoon of grinding (or solving on a sibling's profile first) cannot buy a rank. An attempt started by one account can never be submitted by another.

</details>

<details>
<summary><strong>Student Fee History, Previous Balance, And Arrears Carried Forward</strong></summary>

# Student Fee History And Previous Balance

## Purpose

A student's page ends with a full fee ledger, so "what does this family still owe, and what have they already paid?" is answered on the student rather than by scanning the whole institute's fee list.

---

## What It Shows

Every fee challan ever issued to that student, oldest first, with the amount billed, the amount paid and the date it was paid, what is still owed on it, and a running **balance carried forward** so arrears from earlier months are visible at a glance.

Above the table sit four totals: total billed, total paid, outstanding balance, and the share collected. An overdue flag appears when an unpaid challan has passed its due date.

The section is read-only. It never creates, recalculates or settles a fee.

---

## Part Payments

A challan can now be paid in instalments. Each payment the office receives is stored on its own, so the "paid" figure on a row is the sum of the payments actually recorded against that challan and the row shows what is still owed. A part-paid challan is labelled **Part paid** and deliberately stays Due or Overdue, so it keeps appearing in defaulter follow-up until it is covered in full.

Challans settled before instalments existed carry no itemised payments and still count as paid in full, so nothing in this ledger changed for them.

A payment a family has reported but the office has not yet confirmed is still shown as owed, together with its reference number.

---

## How A Reader Understands The Numbers

The formula is stated in plain English under the heading: "paid" on a row is the sum of the payments recorded against that challan, so a challan can be part paid; it counts as fully paid only once those payments cover it or the office marks it paid outright, and waived when the school writes it off; outstanding balance is total billed minus total paid minus total waived; a challan turns overdue once its due date has passed and something is still owed.

Hovering or keyboard-focusing any total, badge or balance explains that specific value: which challans contributed, how much each still owes, and for an overdue one how many days past its due date it is.

---

## Who Sees What

- **Admin / Accountant** any student in their own institute.
- **SuperAdmin** across institutes.
- **Student** only their own ledger.
- **Guardian** only their own children.
- **Teacher / Librarian** no access, matching the fact that neither role has a Fees page today.

The role, the identity and the institute all come from the signed-in session on the server, and the requested student is re-checked against the caller before any figure is returned. Students and guardians keep the existing rule that challans belonging to a draft fee session stay hidden.

The whole section costs two database queries, never one per challan.

---

</details>

<details>
<summary><strong>Fee Instalments And Recording Part Payments</strong></summary>

# Paying A Fee In Instalments

## Purpose

Families often pay a challan in pieces. Before this, a challan could only be fully paid, fully waived, or fully owed, so an office taking half the money had nowhere to put it and had to either mark the whole challan paid or pretend nothing had arrived.

---

## How It Works

A challan still records what is **owed** and never changes. Every payment received against it is recorded separately with its amount, the date it came in, the method (cash, bank transfer, cheque, card, online, other), an optional reference or receipt number, and who in the office entered it.

"Paid so far" is always the sum of those payments, so there is no second total that can drift out of step with the receipts.

A challan is marked **Paid** only once the payments cover it in full. A part payment never settles a challan: it stays Due or Overdue so it keeps showing up in defaulter reports and reminders, and it gains a **Part paid** label so nobody mistakes it for untouched. A waived challan takes no payment at all, and a challan that is already settled refuses further payment.

Paying more than the challan is accepted and recorded in full, shown as an over-payment rather than a negative balance.

---

## Where To Do It

On the fee list for a class, the row menu (or the card button on a phone) has **Record Payment**. It opens the challan's payment history, shows the challan amount, what has come in and what is left, and pre-fills the amount with the outstanding balance so settling the rest is one click and an instalment is just a smaller number typed over it.

The fee list itself shows the split on any part-paid challan, so the state is visible without opening anything.

---

## How A Reader Understands The Numbers

The rule sits in plain English at the top of the dialog, and hovering or keyboard-focusing any figure explains that specific value: how much came in across how many payments, why the remaining amount is what it is, and why the challan has or has not moved to Paid.

---

## Who Can Do It

Admin, Accountant and SuperAdmin only. The role and the institute are read from the signed-in session on the server, never from the page, and every challan is re-checked against the caller's own institute before anything is written. Recording a payment and updating the challan happen together, so one can never land without the other.

Money is handled in whole paisa throughout, so no rounding error can leave a challan looking a paisa short of settled.

---

</details>

<details>
<summary><strong>Mobile App, Mobile Experience, And Notification Readiness</strong></summary>

# Mobile Experience In More Detail

## Why Mobile Matters So Much

A platform can have excellent features and still fail in day-to-day adoption if mobile usability is weak.

That is especially true in education environments because:

- teachers move around
- guardians prefer phones
- students often use phones first
- institute staff may need quick updates from outside office desks

Innovorix addresses this reality directly.

---

## Mobile Navigation

The product includes mobile-specific navigation behavior so users can reach the most important areas more quickly on smaller screens.

This is important because mobile usage should not feel like a shrunken desktop dashboard.

It should feel intentionally usable.

---

## Mobile Role Experience

### Student Mobile Experience

Students get fast access to:

- dashboard
- timetable
- assessments
- settings
- mobile menu

### Guardian Mobile Experience

Guardians get quick mobile access to:

- dashboard
- attendance/children view
- leaves
- menu
- settings

### Teacher Mobile Experience

Teachers get quick mobile access to:

- dashboard
- timetable
- attendance
- menu
- settings

### Admin And Operational Mobile Experience

Admin and operations-focused roles still benefit from a mobile-friendly dashboard and responsive layout even when they do more complex work on desktop.

---

## Mobile Notifications And Permissions

The project includes mobile permission and push-notification-aware flows.

This helps the product function as a more active institute app rather than a passive website.

Examples of where this matters:

- message alerts
- fee-related updates
- institute notices
- communication reminders

---

## Native Android App Direction

The platform includes Android build support with a native packaging flow.

This gives institutes a stronger app-story in sales and delivery discussions.

It means the product can be positioned not only as:

- a website
- or a browser dashboard

but also as:

- a native-style Android app experience

---

## Progressive App-Like Experience

The product also includes standalone application-style behavior through installed web experience support.

This helps users experience the system more like an app and less like a traditional tab-heavy website.

---

## Mobile-Friendly Product Positioning

For marketing teams, a strong positioning line can be:

`Innovorix is built for real institute usage across office desks, teacher routines, and guardian phones.`

Another good line can be:

`It is not only rich in features. It is usable in the places where institute work actually happens.`

---

</details>

<details>
<summary><strong>Hidden Strengths, Institute Value, Use Cases, Marketing Angles, And Sales Support</strong></summary>

# Hidden Product Strengths Worth Mentioning In Marketing

The following points are especially useful in marketing or sales explanation because they show the product is thoughtfully built.

## Hidden Strength 1: Fee Session Duplication

Recurring fee cycles can be duplicated from earlier sessions.

This reduces repeated setup work.

It is one of the most practical “double work reduction” features in the system.

## Hidden Strength 2: Draft Fee Sessions

Fees can be prepared first and activated later.

That gives the institute more control before making fee cycles live.

## Hidden Strength 3: Payment Proof Review Flow

The platform supports a controlled proof review process instead of leaving finance work to screenshot chaos.

## Hidden Strength 4: Fee Defaulter Recovery Page

Overdue recovery is not hidden inside general fee tables.

It has its own working page.

## Hidden Strength 5: Timetable Auto-Continuation

When adding timetable slots, the system can continue the next slot from the previous time structure.

This saves effort in repetitive timetable creation.

## Hidden Strength 6: Roll Number Conflict Resolution

The product supports both swap and auto-resolve logic.

This is a high-value operational convenience feature.

## Hidden Strength 7: Section-Aware Bulk Promotion

Promotion is not only class-level.

It supports section-level destination control too.

## Hidden Strength 8: Linked Institute Logic

Classes, teachers, attendance, exams, fees, and communication are connected.

This reduces repeated manual mapping across modules.

## Hidden Strength 9: Strong Parent Side

Guardian access is not an afterthought.

It includes fees, leaves, attendance, results, and communication.

## Hidden Strength 10: Institutional Credential Standards

The institute can define credential patterns for students, staff, and guardians.

This helps scale cleanly.

---

# Institute Value By Department

## Value For Institute Leadership

- better operational visibility
- stronger digital discipline
- better parent-facing professionalism
- more centralized oversight

## Value For Admissions Teams

- cleaner student creation
- linked guardian setup
- admission fee support
- credential generation

## Value For Academic Teams

- class and timetable structure
- assessment management
- exam workflow
- marksheet visibility
- promotion workflow

## Value For Finance Teams

- fee sessions
- fee campaigns
- challans
- payment proof review
- defaulter workflow
- late fee logic

## Value For Teachers

- class-focused pages
- attendance
- academic work handling
- marks entry
- timetable visibility

## Value For Guardians

- transparency
- easier follow-up
- child progress visibility
- communication access

## Value For Librarians

- circulation workflow
- overdue awareness
- fine-aware returns

---

# Institute Journey Through The Product

This section describes how an institute may naturally live inside Innovorix over time.

## At The Start Of The Session

- staff is created
- classes are set
- subjects are defined
- timetable is built
- students are admitted
- guardians are linked
- fee cycles are prepared

## During Daily Operations

- attendance is marked
- assignments are given
- fees are viewed
- notices are posted
- communication happens
- leaves are reviewed

## During Exam Periods

- exam sessions are created
- datesheets are visible
- marks are entered
- progress is monitored
- marksheets are later viewed

## During Fee Collection Periods

- challans are issued
- statuses are tracked
- payment proofs are reviewed
- defaulters are filtered
- reminders are sent

## During Year-End Transition

- results are checked
- promotions are prepared
- promotions are executed
- history remains attached to records

This is one of the easiest ways to understand the depth of the product:

it supports the institute across the whole operational cycle, not just one isolated office task.

---

# Practical Use Cases

## Use Case: A Monthly Fee Cycle

The institute creates a monthly fee session.

If it already created a previous month, it can duplicate that earlier session.

Campaign names, components, class selections, and due dates can already be suggested.

The institute then:

- reviews
- confirms
- activates if needed
- lets students and guardians view challans
- reviews payment proofs
- follows up on defaulters

This is a very strong sales story because it shows both planning and execution value.

## Use Case: Parent Asking About Child Progress

Instead of the office manually checking:

- attendance register
- fee note
- exam file

the guardian can often view:

- attendance
- fees
- marksheet
- leave status

directly.

This reduces friction.

## Use Case: Teacher Managing Daily Work

The teacher logs in and quickly sees:

- classes
- students
- timetable
- attendance
- grading work

The teacher does not need to navigate an admin-heavy environment.

## Use Case: Office Managing Promotions

At year end, the office can:

- run class-to-class promotions carefully
- or manage larger promotion operations in bulk

This saves time compared with manually editing student records one by one.

## Use Case: Library Running More Formally

The librarian can:

- issue books
- return books
- track overdue cases
- apply rule-based fine logic

This makes the library function look more professional and controlled inside the same institute system.

---

# Why The Product Feels More Mature Than A Basic ERP

There are many reasons, but these stand out:

- role-based clarity
- workflow states
- mobile thinking
- fee duplication logic
- proof review logic
- defaulter handling
- section-aware promotion
- guardian involvement
- integrated communication
- configurable identity standards

This means the product feels closer to an operational platform than a simple record database.

---

# Positioning Statements For Marketing Content

The following lines may help a marketing team create brochures, website copy, or pitch decks.

## Positioning Line 1

Innovorix helps institutes run academics, fees, communication, and daily operations from one connected platform.

## Positioning Line 2

Innovorix is built for institute management that is practical, parent-visible, and mobile-ready.

## Positioning Line 3

From admissions to promotion, Innovorix supports the full institute workflow.

## Positioning Line 4

Innovorix reduces paper work, repeated setup work, and scattered communication through one disciplined digital system.

## Positioning Line 5

It is not only an admin panel. It is a working digital ecosystem for institutes.

## Positioning Line 6

Innovorix gives management control, teachers focus, finance structure, and guardians transparency.

---

# Sales Talking Points By Feature Theme

## Theme: Efficiency

- recurring fee sessions can be duplicated
- timetable slots can be built faster with continuation logic
- import/export workflows reduce migration friction
- bulk actions reduce repetitive staff effort

## Theme: Transparency

- guardian visibility is meaningful
- fee statuses are clearer
- proof review states are clearer
- leave approval states are clearer

## Theme: Control

- role-based access
- draft and active fee states
- review history
- promotion tracking
- settings-driven institutional behavior

## Theme: Professionalism

- structured communication
- structured marksheet access
- structured approval flows
- structured library circulation

## Theme: Adoption

- mobile-friendly usage
- role-based simplicity
- focused pages for each operational user

---

# If Someone Asks “What Makes Innovorix Different?”

A strong answer would be:

Innovorix is different because it combines broad institute coverage with practical workflow intelligence.

It is not only broad.

It is operationally thoughtful.

That shows up in features like:

- duplicate next fee session wizard
- draft fee sessions
- proof review and defaulter handling
- timetable slot continuation
- section-aware promotion
- roll number conflict resolution
- guardian-integrated leave handling
- institutional ID and password pattern control

---

# If Someone Asks “Who Uses It Day To Day?”

The day-to-day users can include:

- admin officers
- branch operations staff
- teachers
- class in-charges
- finance staff
- librarians
- students
- guardians

This broad role support strengthens the business value of the platform because it drives use across the institute ecosystem.

---

# If Someone Asks “What Problems Does It Replace?”

Innovorix helps replace or reduce dependence on:

- paper fee registers
- manual result files
- scattered WhatsApp communication
- disconnected guardian follow-up
- repetitive monthly fee setup
- unclear leave approval processes
- weak class-level student visibility
- manual year-end promotion handling
- separate book issue notebooks

---

# If Someone Asks “What Is The Best Module To Demo First?”

That depends on the prospect.

## For Management

Start with:

- dashboard
- students and guardians
- fees
- promotion

## For Finance-Focused Prospects

Start with:

- fees
- payment proofs
- defaulters

## For Parent-Transparency-Focused Prospects

Start with:

- guardian dashboard
- child attendance
- child fees
- child marksheet
- communication

## For Academic-Focused Prospects

Start with:

- classes and timetable
- attendance
- assessments
- exams
- marksheet

---

# Expanded Summary Of Every Main Module

The following summaries are intentionally more descriptive for teams that want a longer reading version.

## Dashboard Summary

The dashboard is the first operational layer of the product.

It is where users land and where they understand the shape of their work.

Instead of presenting one generic dashboard to all roles, Innovorix adjusts the dashboard according to role context.

This matters because:

- management needs oversight
- teachers need class focus
- students need personal visibility
- guardians need child visibility

That role sensitivity improves usability and adoption.

## Staff Summary

The staff area is where institute personnel become digitally organized.

The institute can onboard teachers and non-teaching staff, maintain active and inactive states, and keep records centrally.

Because teacher timetable and class assignment become visible around this area, the page does not feel like a dead record table.

It stays operationally useful.

## Student And Guardian Summary

This is the heart of the user-side data structure.

A strong institute ERP needs more than student names.

It needs:

- linked family relationships
- class placement
- admission logic
- credential logic
- lifecycle updates

Innovorix supports that in a practical way.

## Classes And Timetable Summary

This is where academic structure is turned into usable institute operation.

Without this area being strong, teacher views, attendance, and exam logic all become weaker.

Innovorix strengthens it through section-aware logic, direct assignment, timetable building, and import/export support.

## Attendance Summary

Attendance is one of the highest-frequency workflows in any institute.

It must be:

- quick
- clear
- reportable
- role-aware

Innovorix gives the institute all of those.

## Leaves Summary

Leave handling is often messy in educational environments.

Innovorix formalizes it without making it rigid beyond practicality.

That is an important balance.

## Assessments Summary

Assignments and quizzes often create daily academic noise if not structured properly.

Innovorix gives teachers and students a cleaner workflow around them.

## Exams Summary

Formal evaluations need strong structure.

Session grouping, progress handling, grade validation, and datesheet visibility all make this module more credible and mature.

## Marksheet Summary

Results only become useful when they can be retrieved clearly.

Searchable marksheet access helps office teams, students, and guardians.

## Fees Summary

This is one of the strongest product areas.

The fee module is not only a payment list.

It is a true fee operations module.

That distinction matters in product quality.

## Library Summary

The library area extends Innovorix beyond mainstream basic institute ERP claims.

It helps the product feel more complete.

## Promotion Summary

Promotion support is a very important year-end capability that many institutes care about operationally.

Single and bulk modes make the product more practical.

## Communication Summary

Communication becomes more institutional and less fragmented.

That is valuable for discipline, record keeping, and professionalism.

## Settings Summary

A strong settings area turns a product into an institution-ready platform.

Innovorix gives the institute meaningful control over policies and patterns, not just cosmetic preferences.

---

# Recommended Marketing Themes For Innovorix

The marketing team can build campaigns around the following themes.

## Theme 1: Full Institute Control

Use when targeting leadership.

Suggested message:

Run admissions, academics, fees, communication, and year-end promotion from one connected institute system.

## Theme 2: Better Parent Transparency

Use when targeting family-oriented institutes.

Suggested message:

Give guardians clear access to attendance, fees, leave updates, marksheets, and communication.

## Theme 3: Less Repeated Office Work

Use when targeting admin-heavy pain points.

Suggested message:

Reduce double work through bulk actions, fee duplication workflows, templates, and smarter setup flows.

## Theme 4: Strong Mobile Experience

Use when targeting modern adoption.

Suggested message:

Innovorix is built for day-to-day institute use on desktop and mobile, not just back-office screens.

## Theme 5: Better Fee Discipline

Use when targeting finance pain points.

Suggested message:

From challans and payment proofs to defaulters and reminders, Innovorix helps institutes manage fees with more control.

---

# Recommended Sales Demo Order

If a full demo is too long, the strongest compact path may be:

1. dashboard
2. students and guardians
3. classes and timetable
4. fees
5. payment proofs
6. defaulters
7. guardian side
8. promotion
9. mobile story

If the audience is more academic, use:

1. classes
2. attendance
3. assessments
4. exams
5. marksheet
6. guardian visibility

If the audience is more finance-led, use:

1. fees
2. duplicate next session flow
3. payment proofs
4. defaulters
5. accountant role

---

# Final Product Understanding

Innovorix is best understood as a connected institute operating platform.

It is strong because it covers the major institute workflows across:

- management
- academics
- finance
- family visibility
- operations

It is attractive because it includes not only broad module coverage, but workflow intelligence.

It is practical because it supports:

- daily execution
- role-based usability
- mobile usage
- structured approval flows
- recurring operational tasks

It is commercially interesting because it gives a marketing team many real product stories to tell:

- institute control
- parent transparency
- teacher productivity
- fee discipline
- mobile readiness
- academic structure

And it is operationally meaningful because it can support the institute from:

- setup
- to daily usage
- to fee recovery
- to result handling
- to year-end promotion

That combination is what makes Innovorix more than a basic institute record system.

It makes it a working digital environment for institute operations.

---

## Closing Positioning Line

Innovorix helps an institute manage people, academics, finance, communication, and progress in one disciplined, mobile-ready, role-based platform.

</details>

<details>
<summary>Public landing and registration</summary>

The landing page uses the live campaign status for the free Starter offer. The availability strip starts at the owner-requested campaign counter of 491 and adds each real institute account, excluding branches and the demo institute. Two institutes display 493 of 500 filled and seven left. The information text explains the starting count. Each new institute account increments the total. It refreshes every 30 seconds and uses the same count as signup eligibility. A failed refresh retains the last confirmed count and offers a retry. The hero also counts the register cells visitors tick with their cursor, separately from registrations. Visitors can open the demo in one click, dismiss the scrolling offer for their browser session, and receive at most one desktop exit demo invitation per browser. Registration explains email verification, review and the currency and time zone already filled in. Regular monthly prices are Rs 2,999 for Starter, Rs 4,999 for Growth and Rs 5,999 for Pro. Pricing shows Starter for 200 students and 20 teacher accounts, Growth for 500 and 50, and Pro without those limits. While free places remain, Growth costs Rs 1,000 per month instead of Rs 4,999 and Pro costs Rs 1,200 per month instead of Rs 5,999 for a purchase made during the offer. Checkout uses the same prices. Enterprise is quoted separately below, and the live demo remains available outside the plan cards.

</details>

<details>
<summary>Loading feedback for account actions</summary>

Login, signup, the live demo and the contact form erase their own button labels while waiting; verification and password recovery also show loading feedback. Signup and login buttons rotate reassuring messages without claiming a completion percentage. Failed or stalled requests restore a retry, and navigation feedback clears on arrival, browser return or timeout.

</details>
