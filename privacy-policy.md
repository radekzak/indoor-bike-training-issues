# Indoor Bike Training Privacy Policy

*Effective 2026-09-13 · App version 1.0.0 · cz.radeck.IndoorBikeTraining*

Indoor Bike Training is built to run on your device, not on our servers. This policy explains, in plain terms, exactly what the app touches, what it stores, where that data goes, and the couple of places a bundled component asks for a permission the app itself never actually uses.

## Contents

1. [Bluetooth & sensor data](#01-bluetooth--sensor-data)
2. [Ride, route & workout data](#02-ride-route--workout-data)
3. [Location, camera & photos](#03-location-camera--photos)
4. [Strava export](#04-strava-export)
5. [In-app purchase](#05-in-app-purchase)
6. [Storage & retention](#06-storage--retention)
7. [Data sharing](#07-data-sharing)
8. [Children's privacy](#08-childrens-privacy)
9. [Your choices](#09-your-choices)
10. [Changes to this policy](#10-changes-to-this-policy)
11. [Contact](#11-contact)

## 01 Bluetooth & sensor data

The app uses Bluetooth Low Energy to connect directly to your own equipment: a smart trainer speaking the **FTMS** (Fitness Machine Service) protocol, and optionally a separate heart-rate strap or monitor. This connection is peer-to-peer between your phone or computer and your equipment — it never passes through our servers, because we don't have any.

Data read over this connection — power (watts), cadence, speed, resistance level, and heart rate — is used only to drive the live ride screen and, if you complete a ride, to build the local history record described below.

## 02 Ride, route & workout data

The app stores the following **on your device only**:

- **Ride history** (Local) — Duration, distance, average power/speed/heart rate, and per-second samples for every completed ride.
- **Routes** (Local) — GPX files you import and procedurally generated routes you create.
- **Workouts** (Local) — Structured interval workouts you build in the app.
- **Rider profile** (Local) — Weight, FTP, and birth year (used only to estimate a max heart rate for training zones).

None of this leaves your device unless you explicitly export or upload it yourself — see [Strava export](#04-strava-export) below.

## 03 Location, camera & photos

The app requests three permissions on iOS that it does not actually use: **location**, **camera**, and **photo library** access. This isn't an oversight we're glossing over — the app has no GPS tracking, takes no photos, and never opens your photo library.

These prompts exist because two bundled, third-party components — the system file picker used to import `.gpx` route files, and a Bluetooth-permission helper library — link to system frameworks that reference these APIs, even though the code paths that would use them are never called. Apple and Google both require an explanation to be present for any linked API regardless of whether it's reached at runtime, so the descriptions are shown, and this paragraph is the explanation.

## 04 Strava export

The app can optionally send a completed ride to your own Strava account, entirely at your initiative:

- You connect your Strava account yourself, through Strava's own login screen in your system browser (OAuth) — the app never sees your Strava password.
- Nothing is sent automatically. Each upload happens only when you tap "Send to Strava" on a specific ride.
- What's sent is a standard activity file (power, heart rate, speed, and GPS track if the ride used an imported route) for that one ride, via Strava's own API.
- Once it's on Strava, Strava's own privacy policy governs it — we don't retain a copy or see what happens to it afterward.

## 05 In-app purchase

The app offers a single one-time purchase to unlock unlimited ride time. Payment is handled entirely by the App Store or Google Play — we never see or store your card details, billing address, or any other payment information. We only receive confirmation that the purchase succeeded, which we store on your device to remember that you've unlocked the app.

## 06 Storage & retention

All app data described above lives in your device's local app storage. It is never backed up to a server we operate, because none exists. Deleting the app deletes this data along with it. You can also delete individual rides or routes at any time from within the app itself.

## 07 Data sharing

We do not sell, rent, or share your data with third parties. The only data that ever leaves your device is the ride you explicitly choose to send to Strava, sent directly to Strava's servers under your own Strava account. There is no analytics tracking, no advertising SDK, and no crash-reporting service bundled into the app.

## 08 Children's privacy

Indoor Bike Training is not directed at children and is not knowingly used to collect data from anyone under 13.

## 09 Your choices

- Disconnect your trainer or heart-rate sensor at any time from the Bluetooth Devices screen.
- Delete any ride or route permanently from Ride History / My Routes.
- Disconnect your Strava account from Settings → Strava, at any time.
- Uninstall the app to remove all locally stored data at once.

## 10 Changes to this policy

If this policy changes, the effective date at the top of this page will be updated. Since the app doesn't collect contact details from you, we can't notify you directly — check back here if you'd like to review it.

## 11 Contact

Questions about this policy or how the app handles your data: [radek@radekzak.cz](mailto:radek@radekzak.cz)

---

Indoor Bike Training · cz.radeck.IndoorBikeTraining · Last updated 2026-09-13
