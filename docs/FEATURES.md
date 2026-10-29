# SimeTown features, role by role

Every screen, tab and action in SimeTown, grouped by who uses it. For a short overview see the
[README](../README.md); to try these with demo accounts see [DEMO_TESTING.md](DEMO_TESTING.md).

Items marked **(simulated)**, **(preview)** or **(planned)** are labelled the same way in the app.

**Contents:** [Every role](#every-signed-in-role) · [Resident](#resident) · [Shop and home-service business](#shop-and-home-service-business-merchant) ·
[Sponsor](#sponsor) · [Gate guard](#gate-guard) · [Guardhouse staff](#guardhouse-staff) ·
[Courier and courier-company manager](#courier-and-courier-company-manager) ·
[SDP console: staff, admin, HQ](#sdp-console-township-staff-township-admin-hq-admin) ·
[Public pages](#public-and-signed-out-pages) · [Background jobs](#background-jobs) · [Archived](#archived-features)

---

## Every signed-in role

- **EN / BM switch** in the top bar. The choice is saved to the account and restored on every device.
- **Notifications bell**: an unread count and a preview panel, refreshed every 30 s.
- **Sign-in timeouts**:
  - A sign-in ends after 15 min idle for staff, admins and HQ, and after 30 min for everyone else.
  - Guards and guardhouse staff have no idle limit on shift, so an SOS is never missed.
  - Everyone is signed out after 12 h at most.
  - A warning with *Stay signed in* comes 2 min before. Activity in one tab keeps the other tabs signed in.
- **Profile completion**: anyone missing a phone number or address, or the current Terms and Privacy acceptance, is asked for it after signing in.
- **Account page**:
  - Profile: the email is read-only.
  - Change password: other devices are signed out.
  - *Download my data* and *Delete my account* (PDPA).
  - Terms status, and sign out.
- **Forgot password**: an emailed single-use link that lasts 30 min. The same answer is given whether or not the account exists, and every device is signed out after the reset.
- **"See how it works" walkthroughs**: short animated guides. They pause on hover or focus, never play under reduced motion, and never change data.
- **Layout-matched loading skeletons**: shown only after 150 ms, then kept at least 600 ms.

---

## Resident

Menu groups: *Overview · Recycle & move · Around the township · Home & deliveries · Help & account*.
On a phone, the bottom bar holds Home, Points & XP, Kitar and Lapor.

### Home (`/app`)
- **Today card**: up to four items that change through the day:
  - your zone's flood level;
  - a walk-in waiting at the gate (*Expected / Not expected / Call me*);
  - parcels at the guardhouse;
  - a visitor expected today;
  - a Shop Offer you can use;
  - recycling collection today or tomorrow;
  - a morning walk prompt.
- **Figure tiles**:
  - SimeTown Points, split into cash-backed and offer-backed;
  - Impact XP with level and progress;
  - *You saved*.
- **Confirm at the counter**: approve or decline a shop's request to use your points.
- **Home status banners**: home waiting for confirmation, or rejected. Owners also see tenants' requests to confirm or decline.
- **Other sections**:
  - Funded challenges.
  - 11 shortcuts.
  - Street league: this month's XP by street, never by person.
  - One banner, always labelled *Sponsored*. It never appears on the safety screens.
- **Simple Mode home**:
  - Four big tiles: Help (SOS), Visitors, Flood and My points.
  - A *More services* grid.
  - Read-aloud, and a switch to the full app.

### Points & XP (`/app/wallet`)
- Balance in points and ringgit (100 points = RM1), split by backing, with notice of points about to expire.
- **Show my code**: member QR and code, used at the cashier, at a kiosk camera, for carer invites and as a courier delivery code.
- **History** tab: earned, spent, expired, taken back, returned and corrections, paged.
- **Shop Offers** tab:
  - Every offer, with availability and terms.
  - The monthly pledges that back offer points ("No pledge, no points").
  - Each offer-backed point lot, with its backing and expiry.
- **Badges** tab: badges earned, and progress bars for the rest.
- **Rules & limits** tab: how points work, and today's and this month's earning limits.

### Kitar: recycling (`/app/kitar`)
- **Recycle now**: choose a site, then a bin (open, full or offline), then a material. Scan the bin's rotating screen code, or show your member QR to the bin's camera.
- **Live machine session** (`/app/kitar/machine`): each item appears as it is weighed. An item counts only when the camera, barcode and scale agree.
- **Guest claim codes**: recycle without an account and claim the XP within 14 days.
- **Can I recycle this?**: search in English or Malay (e.g. "minyak", "pizza box").
- **Book a collection**:
  - Choose materials, collector, day and slot. The collector's gate pass is made automatically.
  - Cancel, *The collector came*, or enter the weight.
- **Transaction** tab:
  - This month's kg by material, your street's total, points and XP, and the next goal.
  - Challenges, and the rate per kg by material.
  - Recent drop-offs.
- **Map** tab: recycling places, with *Recycle here*. Some are marked *Coming soon*.
- **About** tab: how Kitar works, accepted items, spending points, why an item didn't count, and limits.
- **Report a problem**: bin, weight, points or the page, with a screenshot. Followed in Lapor.
- **Test mode only** (simulated): *Manual recycle (practice)*, and the demo buttons for collections.

### Gerak: walk, run, cycle, wheelchair (`/app/gerak`)
- **Track** tab:
  - Figures: distance and loops this month, all loops, and checkpoints today.
  - Live map tracking with *Start / Finish*. Checkpoints tick themselves, with fair-play speed bands. A step-by-step version is used in Simple Mode.
  - Privacy: location is used only between Start and Finish. The first and last 200 m are never stored, and routes are deleted after 30 days.
  - Scan a checkpoint poster as a backup. The QR fills in the code.
  - Challenges you are automatically entered in.
  - **Test playback** (simulated): replays a route instead of GPS outside production.
- **Loops** tab: each loop's mode, distance, checkpoints, today's progress and history, *Show on map*, and *Directions to start* (Google Maps).
- **About** tab: ways to take part, fair play, location and privacy, and why a loop didn't count.
- **Basemap**: Google Maps when a key is set, otherwise the township's own privacy-preserving map.
- **Report a problem**: with a screenshot.

### Lapor: reports (`/app/lapor`)
- **New report**:
  - Fields: what, where, area, and a required photo (JPG/PNG, at most 10 MB, at least 400 px; avoid faces and number plates).
  - *Suggest for me* proposes a type and urgency, using AI or keyword rules.
  - In Simple Mode it is a 5-step wizard. The form reminds you to call 999 first.
- **Duplicate prevention**:
  - *Already reported?* shows similar open problems with **Me too**.
  - After sending, a likely duplicate asks *Add my report* or *It is different*.
- **Quality filter**: junk text and rude words, including disguised spellings and slang, are refused politely.
- **Community reports** tab:
  - Only your own reports: search, type chips, Ongoing / Finished, late and following badges.
  - Each detail shows progress, how many residents are affected against the threshold for neighbours to see it, the staff note, and the photo of the fix.
- **Reports around the township** (`/app/lapor/around`):
  - Only problems that 5 or more residents reported, with neutral titles in English and Malay.
  - Township figures: being handled, fixed in 30 days, residents affected, typical days to fix.
  - Group by type, filter by status or *Following*, and *Me too* or unfollow.
- **Parcel, Gate, Kitar and Gerak report** tabs:
  - Search by INC reference, and filter by *Needs your answer*.
  - A conversation with staff, reply, and *Not fixed? Reopen it*.
  - Parcel problems that belong to a courier company are listed separately (simulated).
- **Home service reports** tab: private reports about home-service jobs, with progress and replies.

### Komuniti: neighbours and sharing (`/app/komuniti`)
- Figures: community XP, events joined, items shared and neighbours helped.
- Tabs: All, Activities, Help, Give & Lend. Search, and *Only mine*.
- **Posts**: an event (with date and places), ask for help, give an item, or lend an item. Each can have an optional photo.
- **Neighbours respond**:
  - *I'm coming*, *I can help*, *I'd like this*, or borrow.
  - The author accepts or declines, and sets a return date for loans. Overdue loans are flagged, and *Borrow again* is offered after a return.
- **XP**: given only when the organiser or asker confirms it happened.
- **Reporting**: report a post. A photo reported by 2 residents is held until staff check it.

### Banjir: floods (`/app/banjir`)
- **Zone cards**:
  - Water level, the last 6 hours, and a rising-fast warning.
  - Status: Normal, Unconfirmed warning (amber), Warning or Danger.
  - The official message, with the next update time or *Update overdue*.
  - Safe route and assembly point.
- **Check in**: *I'm safe* or *I need help* when your zone is not Normal.
- **Danger takeover**: a full-screen alert with the safe route, check-in straight from it, and a banner until it clears. It flashes, vibrates and reads aloud if set in Akses+.
- A link to the public status page (`/status`), and large cards with read-aloud in Simple Mode.

### Akses+: accessibility (`/app/akses`)
- **My access needs**:
  - Private, kept only with consent: the needs checklist.
  - *Simple Mode*.
  - *Read alerts aloud*, with *Try it*.
  - *Flash and vibrate for alerts*.
  - The *Priority help list for floods*, with a note for staff.
  - *Delete my access needs*.
- **Accessible view** (separate from Simple Mode): larger text and tap targets, switched on automatically when you have saved needs.
- **Carers**: invite someone by their member code, or end a link. Carers see the zone status and check-in of the people they care for.
- **Step-free and accessible places**:
  - Places are shown as verified or available today.
  - Add a place (staff check it), report a blockage with a photo, follow a place.
  - Confirm *Yes, it is clear* or *Still blocked*.
- **My accessibility reports**: a timeline, the photo of the fix, confirm or reopen with *The problem is back*.

### Tamu: visitors (`/app/tamu`)
- **New visitor pass**:
  - Kinds: one visit, delivery, event guest, regular helper, contractor or carer, each with its own limits.
  - *Who fills in the IC or passport number*: you now, or the visitor on their link.
  - Transport, vehicle number and driving-licence expiry. An expired licence cannot drive in.
  - Reason and dates.
- **Pass delivery**: by email, with a QR, a code and a link to copy. *Send again* replaces the old link, and *Cancel* revokes it.
- **Walk-in at the gate**: answer *Expected*, *Not expected* or *Call me*. "Not expected" never blocks lawful access.
- **SOS to the guardhouse**: one confirmation, then live status.
- **Visit history**: in and out times, and the last 4 characters of the ID. Deleted after 90 days.
- *Report a gate problem*, and read-aloud.
- The host gets an email and a notification when the visitor arrives. Visitors' ID numbers are encrypted.

### Parcels (`/app/parcels`)
- **Parcel lockers** tab:
  - Your home's own private door, and a one-time PIN and QR (never stored).
  - *Get a new code*: the old code stops working and your household is told.
  - *Open my door* with the station code, and keypad lockout help.
  - Confirm *I have my parcel and the door is shut*. Simulated station buttons stand in for the hardware.
- **Guardhouse** tab:
  - Open or closed now, with hours.
  - Collection code QR, shelf, and days waiting, with an overdue status.
  - *Share the code* with whoever collects.
  - *I didn't collect this*: *It was someone in my home*, or *Please investigate*.
  - *My late collections*.
- **About** tab and *How to collect* guide: doors, the guardhouse, reminders and late collections.
- **A parcel hasn't arrived?**: enter the tracking number.
  - If the courier company confirms it is on its way, you get the company's support channel instead of a township case.
  - *Send it to them for me* files a simulated ticket.
- **Report a problem**: a locker door that won't open, a guardhouse problem or a delivery problem. SimeTown shows *what the township's records show* first, and the report is followed in Lapor.
- **Parcel bar**: a strip on every page when parcels are waiting. It can be hidden until the next parcel.
- **Emails**: in your door, at the guardhouse, the weekly overdue reminder, and a door opened without a code. You can switch these off under *Account › Emails*.

### SimeTown Home: home services (`/app/home-services`)
- **Book a service**:
  - Six categories: plumbing, electrical, air-conditioning, cleaning, repairs and renovation.
  - Compare approved companies by rating, jobs done, reviews, pricing model and call-out fee.
  - Book with the problem, date, slot and an optional photo.
- **My bookings**:
  - See the registered worker who is coming, and call the company.
  - An automatic Tamu gate pass for the worker; *Make a new gate pass* if needed.
  - Confirm *The job is done*, or cancel. Review with 1 to 5 stars.
  - *Report a problem privately*: harassment, no-show, poor work or pricing.
- **Home logbook**: every confirmed job at the home, shared with the household. A service that is due or overdue (e.g. air-con every 180 days) offers *Book again*.
- **Payment**: prices are agreed in person, and SimeTown takes no payment.
- **(preview)**: SDP warranty and defect records, and resale and rental listings.

### Assistant (`/app/assistant`)
- **Asking**: questions in English or Malay, with suggested questions.
- **Answers**: drawn from your own data (points, passes, parcels, requests, flood) and from checked facts about City of Elmina, with sources and a *checked* date.
- **Actions** such as *make a visitor pass for Ali tomorrow*, or *send this to the township office*: only after you confirm with *Yes, Change or No*.
- **History**: past chats are kept 90 days; delete one, or all. Staff replies arrive in the chat.
- **Options**: read-aloud per answer, and share.
- **Without AI**: when the AI is off or the daily limit is reached, fixed rules answer from the same tools.

### My requests (`/app/requests`)
- One list of everything your household is waiting on (reports, parcels and collections), each with its status and next step. The Assistant can read it.

### Notifications (`/notifications`)
- Search, category chips, All / Unread, *Mark all as read*, dismiss, and pages.
- Categories: Parcels, Home services, Community, Points & XP, Reports & requests, Kitar, Gerak, Township alerts, Account.
- Each notification links to the exact record. Shared with every role.

### Account (`/app/account`)
- Home address (owner or tenant, which needs re-confirmation), and parcel and visitor email switches.
- Everything listed under [Every signed-in role](#every-signed-in-role). Simple Mode has step-by-step versions of the forms.

---

## Shop and home-service business (Merchant)

One business account can be a **shop**, a **home-service company**, or **both**. The menus follow what it offers.

### Joining
- Apply at `/join` as a shop, home services, or both. You can sign in at once and set up while you wait for approval.
- **Waiting for approval**: shops cannot record sales, and service companies are hidden from residents until approved. A **suspended** state is shown the same way.

### Counter (`/merchant`, shops)
- **This week**:
  - Reward pool, with a low-pool warning ("No pool, no points").
  - Due to you this week.
  - Sales in 7 days.
  - Points given, and the service fee.
- **New sale**:
  - Enter the member code and the bill.
  - *Customer wants to use points*: capped at a share of the bill, with quick-pick chips.
  - *Customer wants to use your Shop Offer*: checked against the offer's hours, budget and minimum spend.
- **Before sending**: a live breakdown of what the customer pays, the points accepted, the offer and the points you give.
- **Confirming**: the customer confirms on their own phone, and the counter updates by itself. A retried press records the sale only once.
- **Results**: recorded, declined, expired or refunded.
  - Clear badges for "pool empty, no points given" and "customer reached their earning limit".
- **Customers, last 30 days**: new, returning, and Shop Offers used.

### Shop Offers (`/merchant/offers`)
- **One live offer at a time**:
  - Discount in whole ringgit, optional minimum spend and a monthly budget.
  - Days of the week, and a time window.
  - Pause, resume or end.
  - It pauses itself when the budget runs out and resets each month.
- **This month**: offers used, discounts given, and the 10% success fee (taken at the next settlement).
- Past offers, and the **Akses-friendly badge** switch (step-free entry, wheelchair space, staff help).

### Sales (`/merchant/sales`) and Statements (`/merchant/statements`)
- **Sales**: a paged sales table. A **refund** reverses earned points to the pool, returns used points to the customer, and shows the cash to give back.
- **Statements**: *Due to you this week* and a weekly settlement table: sales, points, fees, offer discounts, and paid on. Payments are recorded, not sent (simulated).

### Bookings (`/merchant/bookings`, home services)
- **Lists**: *Open* (with a count of new requests) and *Finished*. *Waiting over a day* is flagged.
- **Accept**:
  - Set a visit time, optionally assign a worker now and add a note.
  - The resident's **address and phone are revealed only after you accept**.
- **Decline**: with a reason.
- **Assign or change the worker**: a new gate pass is issued and the old one is revoked.
- **During the job**:
  - *Worker has arrived*.
  - *Work is finished*, with a note such as the agreed price. The resident then confirms.
  - *Cancel*: the reason is shown to the resident.
- **What you see**: a history timeline, the worker's gate pass code, and the resident's review.

### Services & workers (`/merchant/services`)
- **What we do**: choose trades.
  - **Licensed trades** (plumbing, electrical, air-con, renovation) need a licence number (SPAN, Suruhanjaya Tenaga, CIDB) and a check by the township office: pending, approved, or declined with a reason.
- **Listings**: one per trade, with a description, a pricing model (fixed, after inspection, or quotation), the call-out fee and a price note. Hide or show each.
- **Workers**: a name and phone, never an IC number. See upcoming visits and jobs done. Make a worker active or inactive.
- **About your company** text.

---

## Sponsor

- **Tier card**:
  - The tier: Rakan Komuniti, Township Partner, Green Champion or Title Partner, or one-off campaigns with no tier.
  - Benefits.
  - Challenges this year against the allowance.
  - The banner tagline, always labelled *Sponsored*.
- **Totals**: live campaigns, budget committed, given as rewards, and left in pools (refunded on close).
- **Campaign cards**:
  - Status: waiting for payment, live, funded but not started, ended or closed.
  - The budget split between the reward pool, the campaign fee and running costs.
- **Results**: grouped totals only, hidden until a minimum group size is reached.
  - Residents rewarded, points given, spent at township shops, expired and refunded.
- **Privacy**: campaigns are created by the township team. Sponsors never see individuals, and never appear on safety screens.

---

## Gate guard

The gate screen (`/guard`) refreshes every 5 s. Township staff and admins can cover a shift.

- **Scan a visitor pass** with the camera, or type the code.
  - The screen shows full visitor details: the ID to compare with the card, transport, plate, licence expiry and reason.
  - If anything is missing, a form asks for only that.
  - An expired licence needs a new valid expiry before *Let in*. The host is notified.
- **Walk-in visitor**:
  - Name, citizenship, MyKad or passport number, transport, plate, licence expiry and reason.
  - *Ask the household*. If nobody has the app, the guard is told to call the house.
- **Gate log** (last 24 h, kept 90 days): the host's answer (*Expected / Not expected / Call the host / Waiting*), and *Left* to log the exit.
- **SOS alerts** from residents: *On my way*, then *Close*.
- **Flood duty**: the task list per zone at Warning or Danger, and *Reach [resident]* cards from the priority list with tap-to-call, ending with *Reached them*.
- **Patrol round**: today's points and a code check. A scanned patrol poster fills in the code.
- **Accessibility issues for the guard's team**: acknowledge, and submit a fix with a photo.
- Walkthroughs: *How the gate works*, and *How flood duty works*.

---

## Guardhouse staff

The guardhouse parcel counter (`/guardhouse`) has its own account. Staff and admins can cover a shift.

- **Overview**:
  - Parcels held against the room available (warned at 80%), overdue parcels and calls to make.
  - Arrived today, and collected in 30 days with the average days held.
  - Disputed handovers, and the opening hours.
- **Courier drop-offs**: locker parcels that would not fit a door, with the reason. *Confirm receipt* sends the household a pickup code.
- **Hand over a parcel**:
  - Scan or type either kind of code.
  - Shelf parcels show their photo. Locker parcels need *I have checked the person's ID*.
- **Log a parcel**: house, courier (from a list, or typed), shelf, tracking number, note and photo. The household gets a one-time code the guard never sees.
- **Guardhouse register**:
  - Search by tracking number, resident, house or courier.
  - Filter by status, arrival route, courier and dates. Sort by longest waiting or newest. Paged.
- **Parcel history**: a full timeline and *Note after calling*.
  - *Send back to the courier* always needs a reason; a parcel is never sent back just for waiting.
  - *Keep it at the guardhouse*.
- **Rules**: overdue after 7 days, a weekly reminder, a call to the household at 14 days, and no fees.

---

## Courier and courier-company manager

### Getting access
- **Apply** at `/courier-apply` under an authorised company. The township approves and assigns stations.
- **Added by the company's manager**: a one-time set-password link that lasts 7 days.
- **Sign in with your courier company**: OpenID Connect with PKCE and RS256 ID tokens. An account is created on first sign-in (simulated company, `/sim-idp`).
- **Locker station poster** (`/locker/[code]`): *I am collecting a parcel* or *I am a courier*.

### Deliver (`/courier`)
- **Stations**: free doors per size (S/M/L/XL), and offline or maintenance status.
- **Scan the label** with the camera or a USB scanner. The company confirms the shipment (simulated).
  - *Verified* comes with **High** or **Medium** assurance.
  - The recipient is matched by delivery code, phone, name, address or postcode, and **shown masked**.
- **Refusals**, each with its reason:
  - already delivered (replays are logged as incidents);
  - carried by another courier;
  - unknown tracking number;
  - recipient not living there;
  - unregistered home;
  - signature needed;
  - too big;
  - assurance too low.
- **Company outage fallback**: use the resident's delivery code. This is recorded as low assurance.
- **Opening a door**: the household's own private door opens. The courier shuts it with the parcel inside, and the household is told.
- ***It will not go into this door***:
  - Reasons: too big, full, didn't open, damaged, or other.
  - The courier is offered the guardhouse (if open, with hours), *Keep it for my next round*, or *Not delivered today*.
- **Account states**: pending approval, suspended, the company's agreement ended, or no stations yet.
- **Report a problem**: locker not working, turned away at the gate, or other.
- **My deliveries** (`/courier/history`): the last 50 deliveries.
- **Demo labels** (`/demo/labels`, simulated): printable fictional labels with barcodes for every demo case.

### Team (`/courier/team`, managers)
- **Company card**: sign-in method, stations and agreement end date.
- **Couriers**: status, last sign-in, deliveries and refused scans in 30 days.
- **Actions**:
  - Add a courier with a staff number.
  - **Reconfirm** every 90 days, or their access pauses.
  - **Suspend** ends their sessions at once. Reactivate, or remove permanently.

---

## SDP console: township staff, township admin, HQ admin

Menu groups: *Overview · Operations · Community & partners · Money & governance*. Who can do
what is summarised at the end of this section.

### Insights (`/console`)
- 30-day group totals:
  - active homes, kg recycled, shop sales, points given and spent locally;
  - loop km, open reports and blocked access places;
  - a chart of verified actions.
- **Reward float**: matched to the sen or not, with recent checks.
- **Smart township figures**: machine uptime, guests, GPS trips, visitors, flood alerts, access fixes on time, and shop pledges.
- **Flood readiness KPIs**.
- **Printable monthly impact report**.

### Assistant questions (`/console/assistant`)
- Questions residents chose to hand over. *Send answer* replies into the resident's chat. Staff never see the rest of the chat.

### Lapor (`/console/reports`)
- **Needs attention**: problems that reached the public threshold, and anything urgent.
  - Set the status, team, target date and note for every linked report at once.
  - Correct the public title in English and Malay, and choose or hide the public photo. Both are logged.
- **Community reports**:
  - KPIs: open, late, duplicates avoided, and median time to fix.
  - Status pills; ordered late first, then most affected, then most urgent.
  - **Correct the AI or keyword suggestion** (the correction is logged).
  - Assign, set a target date, and upload a photo of the fix.
  - A *Time to fix by type* table.
- **Gate & community cases** and **Parcel & locker cases**: the **case board**.
  - Queues: Open, Unassigned, Mine, Past deadline, Resolved.
  - Filters and search.
  - *I'll handle this*: only one person can claim a case.
  - Investigating, Waiting for someone, Ask the resident, Update the resident, Escalate to an admin, Resolve with an outcome.
  - Internal notes, the activity timeline, and a *history intact* check.
  - The related parcel's door commands.
- **Deadlines**: cases nobody takes, or that run late, escalate automatically, and admins are told once.

### Parcels (`/console/operations`)
- **Today**: calls due, couriers bringing parcels, overdue parcels and doors to check.
- **Guardhouse**: the same register and handover as the guardhouse account, with figures on top.
- **Smart lockers › Parcels**:
  - A parcel record with its custody chain and notes.
  - Return or keep.
  - Request staff access to a locker, and settle exceptions (admins).
- **Smart lockers › Door access**:
  - **Maintenance sessions** across several doors need one second-admin approval, last 30 minutes, and every removed parcel is scanned.
  - **Exceptional door openings** need a second admin, who can never be the person who asked.
  - *Report a locker problem*.
- **Performance**: door states per station, 14-day arrivals and collections, and guardhouse figures. *Unlock keypad* is here.
- **Manage**:
  - **Stations**: add a station (simulator or hardware gateway), set its status, see its doors, and *Free this door* for a home that moved out. Also the command log and new device secrets.
  - **Guardhouses**: opening hours, room, and taking parcels on or off.
  - **Courier companies**:
    - Onboard, approve or suspend a company, and set its stations.
    - Record the agreement and minimum assurance.
    - Manage representatives, the integration (OIDC or simulated) and the support channel.
    - *Simulate an outage*.
  - **Courier accounts**: approve, or withdraw access.
  - **Parcel check history**: every scan and its outcome, repeated scans after delivery, and each company's system health.
  - **Locker policy**: reminder, overdue and call timings, and quiet hours.
    - **(planned)**: a late-collection charge, door-alert links, a one-tap call outcome, and a monthly HQ report.
  - **Case deadlines**: claim and resolve targets per priority, working hours, holidays and the reopen window. *Run the deadline checks now*.
  - **Simulated courier companies**: act as the company, changing a shipment's status or suspending its staff.
- **Locker simulator** (`/console/lockers/simulator`, simulated):
  - Shut a door with or without a parcel.
  - Force a door, jam it, fault it or take it out of use.
  - Keypad PIN entry, and *Replay a used command* (refused).

### Flood dashboard (`/console/banjir`)
- **Live map**: zone shading, sensor pins, and data sources marked Live or Prototype.
- **Agent queue**, per zone:
  - Each signal, the agent's verdict and the trend.
  - **One-signal drafts** count down 3 or 5 minutes. Send now, or cancel or edit (with a reason).
  - **Confirm the warning**: must be a different staff member.
  - *Duty officer: set the level by hand*.
- **Test signals** (simulated): a sensor slider, CCTV test pictures, a drain-photo upload, and rain-gauge buttons. Also a table of the camera test set's accuracy.
- **Sensors**:
  - Register a sensor (its signing key is shown once), calibrate it, and set thresholds.
  - Log maintenance.
  - Simulated faults: power cut, battery drain and a stuck value.
- **Priority help**: send a guard to a resident on the list (the task appears on the gate screen), reassign, and mark reached.
- **Check-ins and messages**: messages sent, in four-line form with an update every 15 minutes. SMS is recorded, not sent (simulated).
- **Events**: a post-event report with KPIs and a timeline, a false-alarm review, and printing.

### Kiosks, trails & patrol points (`/console/places`)
- **Kiosk bins**: status and today's use. *Open kiosk bin screen* is a tablet page with a rotating QR, guest mode, sensor buttons and Online/Full/Offline (simulated hardware, signed records).
- **Recycling kiosks**: add a kiosk, and print its QR poster.
- **Gerak loops**:
  - Map view, and *New loop* with 2 to 12 checkpoints.
  - Checkpoint posters.
  - Hide or show a loop to residents (with a reason, audit-logged).
- **Patrol points**: posters.

### Recycling collections (`/console/recycling`)
- **Needs attention**: weights to approve, disputes and collectors to watch.
  - Approve a weight, mark a collection missed, or reject.
  - Call, or pause a collector.
  - A list of what was *handled automatically*.
- **History**: filter by outcome, collector, material and period.
- **Collectors**: add a collector (days, times, materials), pause or resume. *Today's collections* sheet to copy or print.
- **Material accepted**: kg by month, and why machines turned items away.

### Access places (`/console/access`)
- **To do**: issues with no team, stuck issues, and places to check on site, plus an automation log.
- **All issues**: by stage, priority and provider.
  - Confirm fixed or not fixed.
  - Acknowledge, or submit a fix for a team.
  - Assign or move to another team (admin).
- **Places**: add a checked place, record an inspection, archive or restore.
- **Configuration**: service providers and responders, assignment rules with a test tool, a default team, service levels, and a simulated provider (admin).

### Home service reports (`/console/home-services`)
- **Reports** residents filed privately: open or closed, with harassment flagged. Filter by company, service and status.
- **Each report** names the worker assigned at the time, with the full booking history. *Send update to resident*, and *Close report*. The company never sees it.

### Komuniti (`/console/komuniti`)
- **Reports waiting**: review, or *It is fine: keep it*.
- **Moderation**: hide while checking, remove (with a note), or restore.
- **All posts**, and suspensions: *Suspend from Komuniti* and lift a suspension (admin).

### Campaigns & sponsors (`/console/campaigns`)
- **Campaigns**:
  - Needs action, Running and Closed. *New campaign*: funder, goal, points, caps, budget and dates.
  - *Record payment*, close and refund, cancel, or close early (admin). Results for anyone.
- **Sponsors & tiers**: over allowance, expiring, no tier. Add a sponsor (admin). *Record tier payment* (HQ).

### Shops (`/console/shops`, admins)
- **Status**: approve, suspend or restore.
- **What the business offers**: shop, services or both, and its trades.
- **Licence requests**: approve, or decline with a reason.
- **Money**: a money summary, and *Record deposit* with a bank reference.

### People (`/console/people`)
- **Resident verification**: waiting, confirmed and rejected. Confirm, or reject with a reason.
- **Staff & partner access** (admins):
  - Create accounts with a one-time set-password link, resend an invite, or reset a password.
  - *Waiting for a second admin*: new admin accounts and resets of accounts already in use. Nobody can approve their own request.

### Float & payments (`/console/finance`)
- **Float check**: the float's position and recent checks. *Run check*, with an optional bank statement figure (admin). Points pause automatically if a check fails.
- **Payments to shops**: what is owed and the settlement history. *Run settlement* (admin). Recorded, not sent (simulated).
- **Corrections** (admins): add or take away points with a reason. A **second admin** must approve.

### Audit trail (`/console/audit`, admins)
- Search, filter by area (Money, People, Parcels, Reports, Places, Rules), who and period, with readable detail.

### Rules (`/console/settings`)
- **Programme rules**: earning and spending rates, limits and expiry, Shop Offers, and safety and privacy (e.g. the 5-resident threshold for public reports).
- **Who can change them**: HQ edits, and can resume points. Everyone else sees them read-only.

### Who can do what

| | Township staff | Township admin | SDP HQ admin |
| --- | --- | --- | --- |
| **Day-to-day operations** | Work Lapor and cases, verify residents, flood drafts and second checks, sensors, guardhouse handovers, loops, collections, Komuniti moderation, create campaigns, locker exception requests | Everything staff can do | Everything admins can do, across all townships |
| **Approvals and settings** | – | Approve shops, licences, couriers and companies. Assign cases, set deadlines, locker policy, kiosks, collectors, stations and guardhouses | Programme rules and *Resume points* |
| **Money** | View the float and payments | Float check, settlement, campaign payments and refunds, corrections (second admin) | Sponsor tier payments |
| **People and accounts** | – | Staff, guard, guardhouse and merchant accounts; second approver for door access, corrections and admin resets | Create admin and sponsor accounts |
| **Shops and audit trail pages** | No | Yes | Yes |

---

## Public and signed-out pages

| Page | What it is |
| --- | --- |
| `/` | Landing page: hero, an animated *How it works* story, modules, audiences, FAQ |
| `/offer` | *What we offer*: all 17 modules, "No pool, no points", and screens per role |
| `/shops` | Shop directory, and how earning and spending work |
| `/challenges` | Live public challenges, and actions that always earn XP |
| `/sponsorship` | Sponsors, how sponsorship works, tiers and partners (`/partners` redirects here) |
| `/status` | Official flood status per zone: message, next update, safe route, meeting point, share, call 999 |
| `/guest` | For visitors: passes, recycling as a guest, flood status, arriving at the gate |
| `/pass/[token]` | The visitor's pass: QR, give your own ID details with consent, Waze / Google Maps directions |
| `/locker/[code]` | Locker station poster: collect a parcel, or deliver one |
| `/login`, `/register`, `/join`, `/invite` | Sign in (including courier-company sign-in); resident sign-up against a real home; business application; set a password from an invite |
| `/forgot-password`, `/reset-password` | Emailed single-use reset link (30 min) |
| `/courier-apply` | A courier asks for locker access under an authorised company |
| `/sim-idp/[code]/authorize` | The simulated courier company's sign-in (demo only, refused in production) |
| `/demo/labels` | Printable fictional shipping labels (demo only) |
| `/terms`, `/privacy` | Terms of Use and Privacy Notice; changing their version asks everyone to accept again |

---

## Background jobs

Run with `npm run job -- <name>`, or over HTTP with `CRON_SECRET`. Every job is safe to run twice.

| Job | What it does |
| --- | --- |
| `expire-points` | Expires old points and Shop Offer points, and reminds residents before points expire (daily) |
| `float-check` | Reconciles the reward float against points held; pauses points if anything is off (daily) |
| `settle` | Weekly shop settlement |
| `cleanup` | Retention deletes: visitor and parcel records after 90 days, Gerak routes after 30 days, raw sensor readings (daily) |
| `flood-agent` | One-signal drafts past their deadline and the 15-minute updates (every minute or two; runs by itself in development) |
| `lockers` | Unanswered door commands, doors left open, door reminders, guardhouse rules, telling courier companies about deposits, sending emails (every few minutes) |
| `parcel-reminders` | Guardhouse parcels: overdue at 7 days, weekly reminders, calls at 14 days (also run by `lockers`) |
| `couriers` | Pauses couriers their company has not reconfirmed; flags and stops ending agreements (daily) |
| `incidents` | Escalates cases nobody took or that ran past their deadline (once each); closes resolved cases after the dispute window |
| `access` | Akses+ reminders and escalations, stalled verifications, inspection reminders, messages to responsible parties |
| `recycling` | Day-before collection reminders, collections that did not happen or were never weighed, homes or collectors to check (nightly) |
| `emails` | Sends the email outbox (only with SMTP configured; test addresses are never sent to) |

---

## Archived features

Removed from the app for now. Each folder has a README and a restore patch.

| Feature | What it did | Restore kit |
| --- | --- | --- |
| Guided parking | Car park occupancy, *Guide me there* directions, bay booking up to 7 days ahead | [docs/archive/parking/](archive/parking/) |
| Jimat and solar sites | Residents' energy and water bill reader, tips and leak alerts, *Ask about solar*; rooftop ranking for solar studies | [docs/archive/jimat-and-solar/](archive/jimat-and-solar/) |
| Greener materials | Staff comparison of greener building materials and a waste-derived edging trial | [docs/archive/greener-materials/](archive/greener-materials/) (restore after Jimat and solar) |
