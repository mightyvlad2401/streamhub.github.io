# StreamHub — Google Play Data Safety Form

**App name:** StreamHub  
**Package name:** `com.emergent.allstreamsone.b3kpre`  
**Version at time of submission:** 1.0.0  
**Contact email:** vladut.toader@gmail.com  
**Privacy Policy URL:** https://mightyvlad2401.github.io/streamhub.github.io/Google_Play_Data_Safety_Form.md

## How to use this document

Google Play Console → App content → **Data safety** → "Manage" → fill each section using the answers below. Every question in the wizard is mapped one-to-one under its section heading.

---

## Section 1 — Data collection and security

| Question | Answer |
| --- | --- |
| Does your app collect or share any of the required user data types? | **Yes** |
| Is all of the user data collected by your app encrypted in transit? | **Yes** — all requests to the StreamHub backend and to TMDB / JustWatch travel over HTTPS/TLS. |
| Do you provide a way for users to request that their data be deleted? | **Yes** — users can tap **Profile → Delete my data** in-app, and can also email vladut.toader@gmail.com to request deletion. Uninstalling the app also removes all locally stored preferences. |

**Committed to Play Families policy?** No — the app is not primarily targeted at children.

---

## Section 2 — Data types collected, shared and processed

Google groups data into 14 categories. Only the categories that actually apply to StreamHub are declared below; **every other category should be marked "No" in the wizard.**

### 2.1 App activity — *Collected: YES, Shared: NO*

| Data type | Collected? | Shared? | Optional? | Ephemeral? | Purposes | Why |
| --- | --- | --- | --- | --- | --- | --- |
| **Other user-generated content** — Watchlist / Favorites (movie & TV IDs, watched flag, 1-10 personal rating, per-item "notify me" toggle) | Yes | No | Yes (the entire feature is opt-in — nothing is collected until the user taps "Save") | No | App functionality, Personalization | Lets the user sync their watchlist across app re-installs on the same device, mark titles as watched, rate them, and get local reminders. |
| **Other actions** — Region selection, subscribed streaming services, global notification toggle | Yes | No | Yes | No | App functionality, Personalization | Powers the "what's new on services you actually pay for" feed and the region-specific streaming deep-links. |

### 2.2 App info and performance — *Collected: NO*

No crash logs, diagnostics or performance data are collected or sent to any analytics service.

### 2.3 Device or other IDs — *Collected: YES, Shared: NO*

| Data type | Collected? | Shared? | Optional? | Ephemeral? | Purposes | Why |
| --- | --- | --- | --- | --- | --- | --- |
| **Device or other IDs** — a random UUID generated on-device the first time the app opens and stored in Expo SecureStore. Not the Android Advertising ID, not the device serial, and not linked to a Google account. | Yes | No | No (required for the app to function without an account system) | No | App functionality | Acts as an anonymous key so the watchlist can be stored server-side without requiring the user to create an account with an email or password. |

### 2.4 All other categories — *NOT collected*

Explicitly answer **No** for every data type inside these Google categories:

- Location (approximate, precise) — **No**
- Personal info (name, email address, user IDs, address, phone, race/ethnicity, political/religious beliefs, sexual orientation, other personal info) — **No**
- Financial info (payment info, purchase history, credit score, other financial info) — **No**
- Health and fitness — **No**
- Messages (emails, SMS/MMS, other in-app messages) — **No**
- Photos and videos — **No**
- Audio files (voice recordings, music, other audio) — **No**
- Files and docs — **No**
- Calendar — **No**
- Contacts — **No**
- App activity → App interactions, In-app search history, Installed apps, Other actions (other than what's listed above) — **No**
- App activity → Web browsing history — **No**
- Web browsing — **No**

---

## Section 3 — Data usage and handling declarations

For each data type declared as "collected", the wizard asks the same follow-up questions. Answer them as follows:

### Watchlist / Favorites (Other user-generated content)
- **Is this data collected, shared, or both?** Collected
- **Is this data processed ephemerally?** No
- **Is collecting this data required for your app, or can users choose whether it's collected?** Users can choose
- **Why is this user data collected?** App functionality, Personalization

### Region + Services + Notification toggle (Other actions)
- **Collected, shared, or both?** Collected
- **Ephemerally processed?** No
- **Required or optional?** Users can choose (region defaults to `US` until the user changes it)
- **Purpose?** App functionality, Personalization

### Anonymous device UUID (Device or other IDs)
- **Collected, shared, or both?** Collected
- **Ephemerally processed?** No
- **Required or optional?** Data collection is required (no account system exists — the UUID replaces it)
- **Purpose?** App functionality

---

## Section 4 — Third-party data recipients

StreamHub calls three third-party services. **None of them receive the user's UUID, watchlist, region choice, or any other user-scoped data.** They only receive anonymous catalog queries (e.g. "give me the trending movies for region RO"), so nothing needs to be declared as "Shared" in the wizard.

| Service | What we send | What we receive | Docs |
| --- | --- | --- | --- |
| The Movie Database (TMDB) | Region code, genre IDs, TMDB IDs — no user identifier | Titles, posters, cast, ratings, provider availability | https://www.themoviedb.org/privacy-policy |
| JustWatch (via TMDB `watch/providers`) | Region code, TMDB IDs — no user identifier | Deep-link URLs into streaming apps | https://www.justwatch.com/us/privacy-policy |
| YouTube (embedded trailers) | YouTube video ID that TMDB returned | Video stream + YouTube's own cookies inside the trailer webview | https://policies.google.com/privacy |

---

## Section 5 — Security practices declarations

- **Is all data encrypted in transit?** Yes (HTTPS/TLS between the app and our backend, TMDB, JustWatch and YouTube).
- **Do you provide a way for users to request that their data be deleted?** Yes — in-app via Profile → Delete my data, and by email to vladut.toader@gmail.com.
- **Have you committed to follow the Google Play Families Policy?** No.
- **Has your app been independently validated against a global security standard (MASA)?** No.

---

## Section 6 — Ads declaration

Under App content → **Ads**, select **No, my app does not contain ads**.

---

## Section 7 — Permissions rationale (for the Play Store listing)

The app declares the following runtime permissions in `app.json`. This is not part of the Data Safety form itself, but Google reviewers frequently ask about them, so keep this note ready:

| Permission | Why StreamHub needs it |
| --- | --- |
| `android.permission.INTERNET` | To call TMDB, JustWatch and the StreamHub backend over HTTPS. |
| `android.permission.POST_NOTIFICATIONS` | To fire the local "your watchlist title just landed on Netflix" reminder. Notifications are generated on-device — there is no push server. |
| `android.permission.SCHEDULE_EXACT_ALARM` | Needed by `expo-notifications` on Android 12+ to schedule the same local reminder at a specific time. |

---

## Section 8 — Quick copy-paste summary for the "Data safety" section preview card

> StreamHub is a free discovery app that helps you find what's new on the streaming services you already pay for. We do **not** sell your data, we do **not** run ads, and we do **not** require an account. The only things we store on our servers are an anonymous device ID (so your watchlist survives a re-install), your chosen region, the streaming services you toggled on, your watchlist, and your personal per-title ratings. Everything is transmitted over HTTPS and can be deleted from the Profile tab at any time.

---

*Last reviewed: June 2026 — update the "Version at time of submission" field on every Play Store release.*
