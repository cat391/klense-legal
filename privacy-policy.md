# Klense Privacy Policy

**Effective date:** July 11, 2026
**Last updated:** July 27, 2026

Klense is a personal hygiene system for iOS, operated by Cole Thapanawat, sole proprietor ("Klense," "we," "us"). This policy explains what information the Klense app collects, how it is used, who processes it, and the controls you have over it.

The short version:

- Klense is **local-first**: your data lives on your device and is synced to your private account in our cloud backend so it can be restored across devices.
- We collect only what the app needs to work: your **email address**, your **hygiene personalization profile**, your **routine and completion history**, and your **subscription status**.
- **Your AI chat history never leaves your device**, and it is never stored on our servers. When you send a message to the AI coach, the content needed to answer it is processed by Google Gemini — only after you have explicitly agreed, and never with your name, email, or account ID attached.
- We show **no ads**, do **no cross-app tracking**, and **never sell or rent your personal information**.

## 1. Who this policy covers

This policy applies to the Klense iOS app and the account you create in it. It does not cover Apple's own processing of your App Store purchases (see Apple's privacy policy) or third-party websites we link to.

## 2. Information we collect

### 2.1 Account information

When you create an account or sign in we collect:

- **Email address** — via Sign in with Apple or Google sign-in. If you use Apple's "Hide My Email," we receive the private relay address Apple generates.
- **Authentication identifiers** — a random account ID (UUID) and, for Apple/Google sign-in, the provider's account identifier.
- **Name (incidental)** — Apple and Google may transmit your name as part of sign-in. Klense does not ask for, display, or use your name anywhere in the app; if a provider sends one, it may sit unused in your authentication record and is deleted with your account.

Klense does not offer password-based sign-up, so we never receive or store a password; sign-in is performed by Apple or Google and handled by our backend provider (Supabase). Your sign-in session is stored securely in the iOS Keychain on your device.

### 2.2 Hygiene personalization profile

During onboarding you answer questions that tailor your routine. We collect exactly these attributes:

- Skin type, skin sensitivity, and skin goals
- Hair pattern, hair thickness, and hair goals
- Scalp concerns
- Shaving frequency
- Dental appliances (e.g. retainer, aligners, braces) and dental goals
- Budget preference
- Self-assessment answers (four attitude questions, a mindset selection, and the resulting score)
- Your time zone and preferred "start of day"
- Whether your routine is paused (travel/pause mode) and when the pause began
- Account metadata — when your account was created and when records were last updated

These are preference and lifestyle attributes used solely to personalize your hygiene routine. Klense does not collect medical records, diagnoses, medications, age, gender, or any clinical health data, and the app is not a medical service.

### 2.3 Your routine and activity

- **Tasks** — the hygiene tasks on your schedule, including their frequency, priority, and on/off state. If you create custom tasks or accept AI-suggested edits, the task names, "why it matters" text, and step-by-step instructions you or the AI wrote are stored too.
- **Completion history** — timestamps of when you complete tasks, which logical day they count toward, and whether they were overdue.
- **AI usage counters** — a per-day count of AI conversations and requests (numbers only, never message content), used to enforce fair-use limits.

### 2.4 Subscription information

Apple processes your payment; we never receive your payment card details. We store your subscription **status, plan (monthly/annual), start and expiry dates, and the Apple transaction identifier**, plus a log of subscription lifecycle events (e.g. started, renewed, expired), so your subscription works across your devices.

### 2.5 AI chat (stored on your device only)

Your conversations with the AI coach are stored **only on your device**. There is no chat-message table in our cloud backend, and we cannot read your chat history. See Section 4 for what is transiently processed when you send a message.

### 2.6 Analytics and diagnostics (pseudonymous)

To understand feature usage and fix crashes we collect:

- **Usage events** — e.g. "onboarding completed," "task completed (category, priority)," "paywall viewed," "AI message sent." Events describe *that* an action happened, never its content: no message text, task names, or profile answers are included.
- **Crash and error reports** — crash stack traces, error types, and device metadata (model, OS version).

Both are keyed to a **one-way SHA-256 hash of your account ID** — a pseudonym that lets us count unique users and follow a crash across sessions without exposing who you are. Your email, name, and IP address are actively stripped from crash reports before they are sent.

### 2.7 What we do not collect

Klense requests **no** access to your camera, photos, microphone, location, contacts, motion data, or Apple Health. The app contains no advertising SDKs, does not access the advertising identifier (IDFA), and does not track you across other companies' apps or websites. Notifications are generated locally on your device; we operate no push-notification server.

Like any online service, the servers listed in Section 5 technically observe your device's IP address when the app connects; we do not use IP addresses to identify or profile you.

## 3. Where your data lives

All reads happen from a local database on your device. Sections 2.1–2.4 sync to your private account in our cloud backend (Supabase, hosted in the United States — AWS US East, North Virginia) so your data restores if you reinstall or switch devices. Access is enforced per-account with row-level security: your data is readable and writable only by your authenticated account. Data stored only on your device and never synced: AI chat history, your AI data-sharing consent choice, and notification preferences.

## 4. The AI coach and Google Gemini

The AI coach is powered by Google Gemini. Before your **first** message is sent, the app shows a disclosure and asks for your explicit permission; nothing is shared until you agree, and you can decline and still use the rest of the app.

When you send a message, the app transmits the following through our backend to Google's Gemini API to generate a reply:

- **Your message text** and the **prior turns of the current conversation**
- **Your hygiene profile** (the attributes in Section 2.2 that tailor advice: skin/hair/scalp/dental attributes, goals, sensitivity, budget)
- **Your routine snapshot** — your tasks (including any custom task names and instructions you wrote), their frequency and timing, and a coarse recent-adherence signal ("consistent," "spotty," or "lapsed")

Equally important, what is **not** sent to Google: your name, email address, account ID, device identifiers, subscription details, or completion timestamps. Google receives the content above with no identifier linking it to you as a person. Klense does not store your messages or the AI's replies on its servers — only the daily usage counters in Section 2.3. Google processes this data as our service provider to generate the response, subject to [Google's Gemini API terms](https://ai.google.dev/gemini-api/terms); Klense does not permit its use for advertising.

The AI coach is an automated assistant, not a human, and its guidance is educational — not medical advice. You can report any objectionable AI response by touch-and-holding the reply and choosing **Report**.

## 5. Service providers

We share personal information only with the service providers below, only so they can run the app for us, and never for their own advertising:

| Provider | Role | Data processed |
|---|---|---|
| **Supabase** | Backend: authentication, database, sync, serverless functions | Email, account ID, and the synced data in Sections 2.1–2.4 |
| **Google (Gemini API)** | Generates AI coach replies | The per-message content in Section 4, with no account identifiers; only after your explicit consent |
| **Apple** | Payments, subscriptions, sign-in | Handled under Apple's own terms; Apple does not give us your payment details |
| **Superwall** | Hosts and configures the paywall; runs paywall experiments | Your subscription status and the outcome of each purchase or restore, keyed to an identifier Superwall generates for your device — we never send it your email, name, or account ID |
| **Mixpanel** | Usage analytics (US-hosted) | Pseudonymous usage events (Section 2.6) keyed to a hashed account ID |
| **Sentry** | Crash and error reporting (US-hosted) | Crash/error reports (Section 2.6) keyed to a hashed account ID; IP addresses suppressed |

We do not sell personal information, do not share it for cross-context behavioral advertising, and do not disclose it to anyone else except: (a) at your direction, (b) to comply with law or valid legal process, (c) to protect the rights, safety, or security of Klense or its users, or (d) in a merger, acquisition, or sale of assets — in which case this policy continues to apply until you are notified otherwise.

## 6. How we use your information

- **Provide the service** — personalize your routine, compute your hygiene score on-device, sync your data across devices, and operate the AI coach (contractual necessity).
- **Process your subscription** — recognize your purchase across devices (contractual necessity).
- **Improve and secure the app** — pseudonymous analytics, crash diagnosis, and abuse/rate-limit enforcement (legitimate interests).
- **Communicate with you** — service emails about your account and replies to support requests (contractual necessity / legitimate interests).
- **AI data sharing** — solely with your prior, explicit **consent**, which you give once before first use. You can withdraw it by not using the coach, by deleting the app (your consent choice is stored only on your device and is cleared with it), or by contacting us.

We do not use your personal information to train AI models, and we do not permit our providers to do so on our behalf.

## 7. Data retention

- **Account and synced data** (Sections 2.1–2.4) are retained while your account exists and are **hard-deleted immediately** when you delete your account (Section 8). Residual copies in encrypted database backups are purged on a rolling basis within 30 days.
- **AI chat history** exists only on your device; delete a conversation in-app or delete the app to remove it.
- **Analytics and crash data** are pseudonymous and retained per our providers' schedules — crash/error reports for up to 90 days (Sentry), usage events for up to 2 years (Mixpanel) — after which they are deleted.
- **Support emails** you send us are retained as long as needed to resolve your request.

## 8. Your rights and controls

Built into the app, no support ticket required:

- **Export your data** — Settings → **Export My Data** produces a JSON file of your profile, tasks, completion history, assessment answers, and subscription history, delivered via the iOS share sheet.
- **Delete your account** — Settings → **Delete Account** permanently deletes your account and all synced data from our servers, immediately and irreversibly, and wipes the app's local data. (Cancel your subscription separately in Settings → Apple Account → Subscriptions — deleting your account does not cancel Apple billing.)
- **Correct your data** — edit your profile and routine at any time in the app.
- **AI consent** — the coach sends nothing to Google until you agree; declining leaves the rest of the app fully usable.
- **Notifications** — controlled entirely by you in iOS Settings and in-app preferences.

Depending on where you live (e.g. the EEA/UK under GDPR, or California under the CCPA/CPRA), you may also have rights to access, correct, delete, port, or restrict processing of your personal information, to withdraw consent, to opt out of "sale"/"sharing" (we do neither), and to complain to your data-protection authority. To exercise any right, use the in-app tools above or email **klensebusiness@gmail.com**.  We will not discriminate against you for exercising your rights.

## 9. Security

Data in transit is protected with TLS. Cloud data is protected with per-account row-level security so only your authenticated session can access your records. Sign-in sessions are stored in the iOS Keychain. The AI provider key is held server-side and never shipped in the app. No system is perfectly secure, but we design so that a breach of any one component exposes as little as possible.

## 10. International transfers

Our service providers process data in the United States. If you use Klense from outside the U.S., your information will be transferred to and processed in the U.S. under this policy and appropriate safeguards with our providers.

## 11. Children

Klense is not directed to children under 13, and we do not knowingly collect personal information from them. If you believe a child has created an account, contact us and we will delete it.

## 12. Changes to this policy

We will post any changes here and update the date at the top. For material changes we will notify you in the app before they take effect. Your continued use after notice means you accept the updated policy.

## 13. Contact

Cole Thapanawat, sole proprietor
169 Wishbone Bnd, State College, PA 16801
**klensebusiness@gmail.com**
