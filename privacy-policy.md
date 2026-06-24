---
layout: default
title: DutyTracker Privacy Policy
---

# DutyTracker Privacy Policy

*Last updated: 2026-06-24*

DutyTracker ("the app") is an iOS application that helps surgery
residents log duty hours, track ACGME compliance, and submit hours
to MedHub. This policy describes what data the app collects, where
it stores it, and who it's shared with.

## Summary (TL;DR)

- **The app does not track you.** No advertising SDKs, no third-party
  analytics services, no data brokers.
- **Data stays on-device by default.** Shift records, MedHub
  credentials, and location history live on your iPhone, protected
  by iOS's standard disk encryption and Keychain / Secure Enclave
  protection.
- **iCloud sync is optional** and uses your own iCloud account. No
  DutyTracker-operated servers see your data.
- **The only outbound network traffic** is HTTPS to MedHub (for
  submission), Google Sheets + GitHub (for public call-schedule
  data), and Apple iCloud (for optional sync).

## What the app collects

### Location
The app uses CoreLocation geofencing to detect arrivals at and
departures from the hospitals you configure. Location data is used
locally on the device to start and end shifts. **Location data
never leaves your device.**

### MedHub credentials
If you connect the MedHub integration, your MedHub username and
password are stored in the iOS Keychain, encrypted via the Secure
Enclave. Credentials are only sent over HTTPS to your institution's
MedHub server during submission. The app offers an optional iCloud
Keychain sync (off by default on device-only mode) so your login
carries across your own Apple devices.

### Shift records
Each shift you log (arrival time, departure time, hospital ID) is
stored in App Group UserDefaults on the device and optionally
synced to your personal iCloud account via CloudKit. Records are
submitted to MedHub only when you tap Log Now yourself — the app
reminds you each Sunday to do so. The app does not aggregate shift
data across users.

### Nothing else
The app does not collect your name, email address, phone number,
contacts, health data, advertising identifier, or any other
personally identifying information beyond what you have entered
yourself.

## Third parties

DutyTracker contacts the following external services. For each, we
list exactly what leaves the device:

| Service                                          | What's sent                                              | Purpose                         |
|--------------------------------------------------|----------------------------------------------------------|---------------------------------|
| Your institution's MedHub instance               | Your MedHub credentials + the week's shift times         | Weekly duty-hour submission     |
| Google Sheets (a specific public sheet)          | Nothing — we only READ the public Christ call schedule   | Display who's on call at Christ |
| raw.githubusercontent.com (a specific public JSON) | Nothing — we only READ the public Lutheran call schedule | Display who's on call at LGH    |
| Apple iCloud (your own iCloud account)           | Shift records + Keychain credentials, if iCloud-sync on  | Cross-device sync               |

No other endpoints are contacted. The app declares no advertising
tracking in its Privacy Manifest.

## Your rights

- **Delete your data**: uninstalling the app deletes all on-device
  data. To delete iCloud copies, turn off iCloud sync in iPhone
  Settings → Apple ID → iCloud → Manage Storage → DutyTracker →
  Delete Data.
- **Disconnect MedHub**: Settings → MedHub → Disconnect MedHub
  clears credentials from your Keychain immediately.
- **Control reminders & submission**: the app sends weekly Sunday
  reminders (9 AM / 10 AM / noon) prompting you to submit; you can turn
  these off in Settings. Hours are only ever submitted to MedHub when
  you tap Log Now yourself — nothing is sent automatically.

## Security

The app has been reviewed for security practices as of 2026-04-23.
Notable choices:

- App Transport Security is strict — every endpoint is HTTPS with
  no exceptions.
- WKWebView navigation is allowlisted to the `medhub.com` domain
  only. Redirects to third-party origins are cancelled.
- Credentials auto-injected into MedHub login forms are gated on
  the domain to prevent auto-fill on a spoofed login page.
- No third-party SDKs. No embedded secrets or API keys.

A more detailed security model is maintained at
[docs/SECURITY.md](SECURITY.md) inside the app's source repository.

## Contact

For questions, concerns, or data-access requests, email:

**martin.walsh28nd@gmail.com**

## Changes

This policy may be updated. The "Last updated" date at the top
reflects the most recent revision. Material changes will be
announced inside the app via a notification banner on launch.
