# Demo guide: accounts, a guided tour and what to try

Every page has sample data for every kind of account. This guide has three parts:

1. **[Accounts](#accounts)**: who to sign in as.
2. **[Guided tour](#guided-tour)**: a scripted walk through the township in about 30–45 minutes.
3. **[What to try, role by role](#what-to-try-role-by-role)**: a checklist per account.

The full list of features is in [FEATURES.md](FEATURES.md).

## Set up

```bash
npm install
cp .env.example .env
npm run db:setup      # = db:migrate + db:seed
npm run dev           # http://localhost:3000
```

- `db:seed` only **adds** what is missing, so it is safe to run again. It refuses to run when `APP_ENV=production`.
- Every demo account uses **one password**: the one `db:setup` prints, or `SEED_DEMO_PASSWORD` from your `.env`.
- Sign in at <http://localhost:3000/login>. Every email ends in **`@demo.kita.test`**.
- Use two browser windows (one normal, one private) to be two people at once, e.g. the resident and the shop.
- Switch language with **EN / BM** in the top bar. Every screen should read fully in Malay.
- Staff, admin and HQ sign-ins end after 15 minutes idle (30 for other roles; none for guard and guardhouse). Sign in again if a long demo pauses.

## Accounts

| Role | Sign in as | Who it is |
| --- | --- | --- |
| Resident (main) | `aisyah` | Aisyah Rahman, owner of No. 1 Jalan Metafasa U16/171, Elmina Valley 1 |
| Resident | `daniel` | Daniel Tan, a neighbour; a walk-in visitor waits at the gate for his answer |
| Resident (Simple Mode) | `zainab` | Zainab Yusof; Simple Mode, on the flood priority help list, Mei Ling is her carer |
| Resident (carer) | `meiling` | Lim Mei Ling; cares for Zainab |
| Residents | `priya`, `hafiz`, `siti`, `arjun`, `karyan` | Neighbours with reports, *Me too*s, parcels and posts |
| Residents (Elmina West) | `izzah`, `rajesh` | Nurul Izzah Kamal and Rajesh Pillai, flats in Pangsapuri Harmoni Elmina (Locker C) |
| Resident (tenant, pending) | `imran` | Imran Hakim, a tenant of Aisyah's home; Aisyah confirms him |
| Resident (not yet confirmed) | `grace` | Grace Chong; waits for the township office and is asked to add a phone number |
| Shop | `kafe`, `kedai` | Kafe Seri Pagi, Kedai Runcit Mesra |
| Shop (not yet approved) | `bengkel` | Bengkel Basikal Roda |
| Home services | `plumber` | Elmina Plumbing Co. (workers Ahmad and Lim); its electrical licence check waits for staff |
| Home services | `aircon` | Sejuk Aircon Services |
| Shop and home services | `kemas` | Kemas Home Care |
| Sponsor | `sponsor` | Tan Hui Min, Solar Cerah (Green Champion tier) |
| Gate guard | `guard` | Azman Shah, the main gate |
| Guardhouse staff | `guardhouse` | Nur Aina, the guardhouse parcel counter |
| Courier, J&T Express (simulated) | `courier`, `hairul` | Faizal Rahman (JT-1001), Hairul Azman (JT-1002) |
| Courier, Ninja Van (simulated) | `nurul` | Nurul Ain (NV-2001) |
| Courier, Pos Laju | `poslaju` | Rahim Osman, approved by the township for every locker bank |
| Courier (suspended) | `courier2` | Ahmad Zaki; suspended by Ninja Van, cannot deliver |
| Courier-company manager | `jnt-manager`, `ninjavan-manager` | Kavitha Raman (J&T), Tan Wei Ming (Ninja Van) |
| Courier via company sign-in | staff no. `SPX-3001` | Lim Wei Jie, Shopee Express (simulated sign-in); `SPX-3002` (Rosli Osman) is refused by the company |
| Township staff | `staff`, `staff2` | Ravi Kumar, Mei Chen |
| Township admin | `admin`, `admin2` | Nurul Huda, Jason Lee (the second approver) |
| SDP HQ admin | `hq` | Farah Aziz, all townships |

Aisyah's member code is printed by `db:setup`, and shown in her wallet under **Show my code**.
Kiosk, checkpoint and patrol codes are in the console under *Kiosks, trails & patrol points* (each has a poster).

---

## Guided tour

### Part 1: one day in the Township of Tomorrow

1. **Kitar: the smart recycling bin.**
   - As **staff**, open *Kiosks, trails & patrol points → Kiosk bins → Open kiosk bin screen* (a tablet in a real demo).
   - As **Aisyah**, *Kitar → Recycle now*: choose the site and bin and scan the bin's code. Or type her member code under the bin's test controls and press *Read code*.
   - Drop items with the sensor buttons, try a mismatched material, then *Finish*. Aisyah's Kitar screen follows item by item, and the session earns XP and offer-backed points.
   - *Recycle as guest* gives a claim code instead.
2. **Gerak.** In *Gerak*, switch on *Test mode: play back a route instead of GPS* and tap *Start*.
   - The trip follows the Elmina Central Park Walk; checkpoints tick themselves, then *Finish*.
   - On a phone outdoors, leave test mode off and real GPS is used. Scanning a checkpoint poster also works.
3. **Shops and points.**
   - As **kafe**, enter Aisyah's member code and a RM20 bill: she earns 20 points.
   - As **kedai**, enter RM20 and switch on *Customer wants to use points* → 300. Aisyah's phone asks her to confirm, the counter updates by itself, and the statement shows RM3 due this week.
4. **Shop Offers.** As **kedai**, switch on *Customer wants to use your Shop Offer* (RM2 off). Aisyah confirms, pays RM18 of a RM20 bill, and the statement shows the 10% success fee. *Shop Offers* in the shop's menu sets terms and budgets.
5. **Lapor.**
   - As Aisyah, *New report*: a broken street light, with a photo. *Suggest for me* sorts it as Lighting, medium urgency.
   - Write about a problem already reported (e.g. *"Street lights out on Jalan Frekuensi U16/115"*): you are offered **Me too** instead of a duplicate.
   - Open *Reports around the township* to see problems 5+ residents share.
   - As **staff**, *Lapor → Needs attention*: correct the suggestion (it is logged), set who fixes it and by when, and add a photo of the fix.
6. **Komuniti.** Join the gotong-royong, give away an item and confirm the handover: XP is given only on confirmation.
7. **Banjir.**
   - As **staff**, *Flood dashboard → Agent queue*. Move a zone's sensor past 75%: one signal only, so a draft waits for the officer and residents see an amber *Unconfirmed warning*.
   - Click a CCTV test picture near the warning line: two signals agree and the warning goes out.
   - *Confirm the warning* must be done by a different staff member (`staff2`).
   - Push the sensor past 90%: a danger draft counts down 3 minutes, then Aisyah's screen is taken over with the safe route.
   - Residents check in *I'm safe / I need help*. The priority help list sends the **guard** a *Reach Zainab* task. The public page is `/status`.
8. **Insights.** As **admin**, *Insights*: the dashboard has changed all day, with the float matched to the sen. *Monthly impact report* prints it.

### Part 2: people at home

9. **Tamu.**
   - As Aisyah, *New visitor pass*. Choose whether she or the visitor fills in the IC or passport, add the transport and licence expiry, and the pass is emailed. Open the pass link in a private window: that is the visitor's view.
   - As the **guard**, scan or type the code; missing details are asked for there, and Aisyah is told her visitor arrived.
   - As **Daniel**, answer the walk-in waiting at the gate. Try *SOS to the guardhouse* with the guard signed in elsewhere.
10. **Akses+ and Simple Mode.** Sign in as **Zainab**: Simple Mode's four big buttons, read-aloud, and her carer Mei Ling. As **meiling**, see Zainab's zone and check-in.
11. **Assistant.**
    - Ask *"What homes is Sime Darby selling in Elmina?"* or *"Make a visitor pass for Ali tomorrow"*; it acts only after you confirm.
    - Hand a question to the office, then answer it as **staff** under *Assistant questions*.
12. **SimeTown Home.**
    - As Aisyah, *SimeTown Home → Plumbing*: compare companies and book Elmina Plumbing Co. with a photo.
    - As **plumber**, *Bookings*: the address appears only after you accept. Accept with a time and assign Ahmad; a gate pass is made automatically.
    - Mark him arrived and the work done. As Aisyah, confirm and review, or report a problem privately.
    - As **staff**, *Home service reports*: the report names the worker assigned at the time, and the company never sees it.
    - Aisyah's *Home logbook* shows the air-con service due soon: *Book again*.
13. **Licence check.** As **admin**, *Shops* → Elmina Plumbing Co.: it asked to add electrical work with a licence number. Approve or decline it with a reason; the plumber's *Services & workers* shows the outcome.
14. **Recycling guide and collections.**
    - In *Kitar*, type "minyak" or "pizza box" under *Can I recycle this?*, then *Book a collection*.
    - As **staff**, *Recycling collections*: approve weights and handle disputes. The collector's gate pass is made automatically.
15. **One list for everything.** As Aisyah, *Notifications → My requests*: every report, parcel and collection, with where it stands.

### Part 3: parcels and smart lockers

Every home has **its own private door** in the bank serving its precinct:

- *Elmina Valley Locker A* (Elmina Valley 1–3)
- *Elmina Gardens Locker B*
- *Elmina West Locker C*

A parcel that cannot go into the door waits at the **Main guardhouse** (open 8:00 am – 10:00 pm).

Every guardhouse parcel follows the same rules:

- overdue after 7 days;
- a reminder once a week;
- a call due at 14 days;
- never sent back by itself;
- no fees.

16. **The guardhouse.**
    - As **guardhouse**, *Log a parcel* for No. 1 Jalan Metafasa U16/171 with a shelf and a photo. Aisyah's *Parcels → Guardhouse* shows the one-time code and QR.
    - Scan or type it at the counter, check the photo and hand it over: the code stops working.
    - In the **register**, Hafiz's and Priya's parcels have waited over 14 days, so a call is due: add a note. Siti's parcel was sent back on request, with the reason in its history.
17. **Deliver (barcode first).**
    - As **courier** (Faizal), *Deliver → Elmina Valley Locker A*, then scan or type `JTSIM10000001`. J&T (simulated) confirms the shipment with high assurance, and Aisyah is matched and shown masked.
    - Her door opens. Tap *Shut the door with the parcel inside*, and Aisyah is told (and emailed, if SMTP is set).
    - Labels for every case are at `/demo/labels`.
18. **Collect.** As Aisyah, *Parcels → Parcel lockers*: her door, the PIN and the QR. Enter the station code and tap *Open my door*, then *Take it and shut the door*. *My late collections* lists a parcel she collected after 9 days.
19. **The door cannot take it.** Deliver a second parcel for Aisyah, or an M parcel too big for a door.
    - The courier is told why and offered the guardhouse; after 10 pm, they keep it for the next round.
    - *It will not go into this door* lets them choose a reason.
20. **Refused scans.** Each of these is refused for its own reason:

    | Tracking number | Why it is refused |
    | --- | --- |
    | `JTSIM10000001` again | Already delivered (logged as an incident) |
    | `JTSIM10000009` | Already in a locker |
    | `JTSIM10000008` | Carried by another courier (high severity) |
    | `JTSIM99999999` | Unknown to J&T |
    | `JTSIM10000004` | Hairul's delivery |
    | `JTSIM10000005` | Recipient doesn't live there |
    | `JTSIM10000006` | Unregistered home |
    | `JTSIM10000007` | Needs a signature |
21. **Medium assurance and outages.**
    - As **nurul**, `NVSIM20000001` is verified for Daniel by address and name, at medium assurance.
    - As **admin**, *Parcels → Manage → Courier companies → Ninja Van → Simulate an outage*. Then Nurul scans `NVSIM20000003`, and may use Mei Ling's delivery code instead (recorded as low assurance).
22. **Companies manage their couriers.**
    - As **jnt-manager**, *Team*: add a courier with a staff number (they get a set-password link), suspend Hairul (his session ends at once), and reconfirm Faizal.
    - As **courier2**, *Deliver* says Ninja Van has suspended him.
23. **Company sign-in.**
    - Signed out, choose *Shopee Express (simulated sign-in)* and pick `SPX-3001` with the demo password. SimeTown checks the company's signed token and creates the account. `SPX-3002` is refused by the company.
    - `SPXSIM30000001` is matched by the delivery code Zainab gave the shop.
24. **Operations centre.** As **admin**, *Parcels*:
    - *Today*: what needs action.
    - *Performance*: all three banks and the guardhouse.
    - *Manage → Stations → Doors*: which home has which door.
    - *Locker policy*: features marked *Planned · not active*.
    - In the **simulator**, jam a door or take the station offline, then try a delivery: nothing is confirmed. *Replay a used command* is refused.

### Part 4: incidents and cases

25. **A late parcel belongs to the courier.**
    - As Aisyah, *Parcels → A parcel hasn't arrived?* → `JTSIM10000002`. J&T (simulated) confirms it is on its way, so SimeTown shows J&T's support channel; no township case is opened.
    - *Send it to J&T for me* files a simulated ticket.
26. **A door will not open.** As Aisyah, on a parcel in a locker, *Report a problem → The door will not open*. It becomes a township case at once, with the door's history attached, under *Lapor → Parcel & locker cases*.
27. **A critical case escalates.**
    - As **admin**, the door forced open at Locker A is critical, nobody has taken it, and the admins were already told.
    - *Manage → Case deadlines → Run the deadline checks now* does not tell them twice.
28. **"I didn't collect this."** As Aisyah, on a collected parcel, *Report → I didn't collect this*. SimeTown first shows what its records say; *Please investigate* opens a case. An earlier dispute is resolved under *My reports*, with *Not fixed? Reopen it*.
29. **Moving a case.**
    - Daniel's locker case is being investigated by Ravi (`staff`). As **admin**, *Reassign* it to Mei Chen with a reason; she is told.
    - On a new case, *I'll handle this*: if two staff press it at once, only one gets it.
30. **Two-person controls.** As **admin**, *Float & payments → Corrections*: request +100 points for Aisyah. It shows *Needs a second admin*; approve it as **admin2**. Exceptional locker door openings and admin password resets work the same way.

### Emails (optional)

Add `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS` and `SMTP_FROM` to `.env` and restart (Gmail App Passwords: [EMAIL_DESIGN.md](EMAIL_DESIGN.md) §7). These are sent:

- welcome and password-reset emails;
- parcel emails;
- the visitor's pass, and the host's visitor notices.

`@demo.kita.test` addresses are never sent to. To try it, register a resident with your own email, have staff confirm the home, and deliver a parcel or create a pass. You can also try *Forgot password* on the sign-in page.

---

## What to try, role by role

### Resident (`aisyah`, then `daniel`, `zainab`)

| Page | What to try |
|---|---|
| **Home** | Today card, the three figure tiles, shortcuts, challenges, street league. As `imran`'s owner, confirm or decline the tenant. |
| **Points & XP** | Balance and backing, *Show my code*, History, Shop Offers, Badges, Rules & limits. |
| **Kitar** | Recycle now, the live bin session, guest claim code, *Can I recycle this?*, book or cancel a collection, Map, About. **Report a problem** with a screenshot, then **Follow it in Lapor**. |
| **Gerak** | Test-mode playback, loops and the map, checkpoint codes, challenges. **Report a problem** works the same way. |
| **Lapor → Community reports** | Only your own reports. Ongoing / Finished, type chips, search, *"2 of 5 residents"*. **New report**: try junk (“asdfgh”) or a rude word, and it is refused politely. Try a duplicate and choose *Yes, add my report* or *No, it is different*. |
| **Lapor → Reports around the township** | Problems 5+ residents share, grouped by type with **See all**. **Me too**, then **Following** to undo. |
| **Lapor → Parcel / Gate / Kitar / Gerak reports** | *Needs your answer* items (reply to the office's question), outcomes, and **Not fixed? Reopen it**. |
| **Lapor → Home service reports** | Private reports about home-service jobs. |
| **Komuniti** | Create each kind of post with a photo, respond, accept, confirm handovers, lend and return, report a post. |
| **Banjir** | Zones, history, safe route, check-in; the takeover during a danger alert. |
| **Akses+** | Access needs, Simple Mode, read-aloud, flash alerts, priority help, carers, step-free places, report a blockage. Toggle **Accessible view** separately. |
| **Tamu** | Create, resend and cancel passes; answer a walk-in (`daniel`); SOS; visit history. |
| **Parcels** | Parcel lockers (own door, PIN, QR, *Get a new code*, *Open my door*, *My late collections*), Guardhouse (open / closed, code, *Share the code*), About, *A parcel hasn't arrived?*, *Report a problem*. |
| **SimeTown Home** | Compare companies, book, booking detail (worker, gate pass, confirm, review, private report), Home logbook, *Book again*. |
| **Assistant** | Questions in both languages, confirmed actions, sources, past chats, handing over to staff. |
| **Notifications** | Category chips, search, All / Unread, Mark all as read, pages; *My requests*. |
| **Account** | Home address, email switches, password, *Download my data*, *Delete my account*. |

`grace` shows what an unconfirmed resident sees, and is useful for the staff verification queue.

### Shops and home services (`kafe`, `kedai`, `bengkel`, `plumber`, `aircon`, `kemas`)

| Page | What to try |
|---|---|
| **Counter** | Aisyah's member code and a bill; *use points* (she confirms on her phone); the Shop Offer; *Next customer*. |
| **Shop Offers** | The live offer and its budget, days and hours, pause / resume / end, the Akses-friendly badge. |
| **Sales**, **Statements** | Paged history, refund a sale, weekly statements. |
| **`bengkel`** | The *waiting for approval* notice; sales are blocked until approved. |
| **Bookings** (`plumber`, `aircon`, `kemas`) | Accept with a visit time, assign a worker, mark arrived and done, decline, cancel, see the review. |
| **Services & workers** | Pick trades (a licensed trade asks for a licence number), add or hide listings, add workers, *About your company*. |
| **`kemas`** | Both menus on one account. |

### Sponsor (`sponsor`)

The tier card and allowance, campaign cards with their budget split, and **View results** (grouped totals only).

### Gate guard (`guard`)

Scan a visitor pass and complete missing details. Log a walk-in with ID, transport and licence, and log their exit. Answer an SOS (*On my way*, *Close*), the patrol round (three scans already recorded), flood *Reach* tasks, and accessibility issues for the team. Walkthroughs: *How the gate works*, *How flood duty works*.

### Guardhouse (`guardhouse`)

Overview tiles, confirming courier drop-offs, handover for either kind of code (with an ID check for locker parcels), logging a parcel with a photo, the register (search, filters, sort, history, notes, send back with a reason, keep), and the *How the guardhouse works* walkthrough.

### Couriers (`courier`, `nurul`, `poslaju`, `courier2`, `jnt-manager`)

Deliver to a locker, refused scans, *It will not go into this door*, *My deliveries*, *Report a problem*. `courier2` shows the suspended state. Managers add, suspend, reconfirm and remove their own couriers under *Team*.

### Township office (`staff`, `staff2`, `admin`, `admin2`, `hq`)

| Page | What to try |
|---|---|
| **Insights** | Hero figures, tiles that open their pages, the float card, the monthly impact report. |
| **Assistant questions** | Answer a question a resident handed over. |
| **Lapor** | **Needs attention**: open one to see every resident's report and photo, correct the public title, set status, team, date and note for every report at once. *Community reports*: status pills, update, assign, photo of the fix. *Gate & community cases* and *Parcel & locker cases*: take a case, ask the resident, resolve; admins reassign. HQ can change the threshold of 5 in **Rules → Safety and privacy**. |
| **Parcels** | *Today*, *Guardhouse* (register and handover), *Smart lockers* (parcels, door access), *Performance*, *Manage* (stations and doors, guardhouses, courier companies and accounts, parcel check history, locker policy, case deadlines, simulated companies), and the simulator. |
| **Flood dashboard** | Live map, agent queue (drafts, second check, test signals), sensors (nine simulated), priority help, events and post-event reports. |
| **Kiosks, trails & patrol points** | Kiosk bins and the bin screen, kiosks and posters, Gerak loops (new loop, hide / show), patrol posters. |
| **Recycling collections** | Needs attention, History, Collectors, Material accepted. |
| **Access places** | To do, All issues, Places, Configuration. |
| **Home service reports** | Open / closed reports, the worker at the time, update the resident, close. |
| **Komuniti** | Reports to review, hide / remove / restore, suspensions (admin). |
| **Campaigns & sponsors** | Needs action / Running / Closed, new campaign, record payment and close (admin), Sponsors & tiers. |
| **Shops** (admin) | Approve `bengkel`, set what a business offers, the plumber's licence request, record a deposit. |
| **People** | Resident verification (Grace is waiting); Staff & partner access and the second-admin queue (admin). |
| **Float & payments** | Float check, payments to shops, corrections with a second admin (admin). |
| **Audit trail** (admin), **Rules** (HQ edits) | Search and filter every recorded action; programme rules. |

`hq` sees the same as an admin across townships, plus editing **Rules** and recording sponsor tier payments.

## Flows that cross accounts

1. **Kitar report:** `aisyah` reports from Kitar with a screenshot → `staff` asks a question in console Lapor → `aisyah` replies under *Kitar reports* → `staff` resolves → `aisyah` sees the outcome and can reopen.
2. **Shop sale with points:** `kafe` enters a sale using points → `aisyah` confirms in her wallet → both see it in their history.
3. **Home-service booking:** `aisyah` books → `plumber` accepts and assigns a worker (gate pass made) → `aisyah` confirms and reviews.
4. **Visitor:** `aisyah` creates a pass → the visitor completes their details on the link → `guard` scans it → `aisyah` is told.
5. **Resident verification:** `staff` confirms or rejects Grace in *People*; `aisyah` confirms tenant `imran`.
6. **Locker parcel:** `courier` delivers → `aisyah` collects with her PIN → `guardhouse` handles anything that did not fit.
7. **Flood:** `staff` raises a one-signal draft → `staff2` confirms → `aisyah` is taken over → `guard` reaches `zainab`.
8. **Correction:** `admin` requests → `admin2` approves.

## If something looks empty

- Run `npm run db:migrate` and then `npm run db:seed` again; both only add what is missing.
- Most demo items are dated around when you seeded. Time-based lists (today, this week) fill up again after a fresh seed: delete `.data` and run `npm run db:setup`.
- With the default PGlite database, stop `npm run dev` before running `db:*` or `job` scripts.
