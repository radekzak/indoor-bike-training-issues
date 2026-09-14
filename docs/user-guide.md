# Indoor Bike Training — User Guide

This guide explains how to use the [Indoor Bike Training](https://github.com/radekzak/indoor_bike_training)
app: connecting your trainer, riding, building workouts, exporting rides,
and backing up your data. If something here doesn't match what you see in
the app, or you hit a bug, please [open an issue](../../issues/new/choose)
in this tracker.

## Getting started

The app has four tabs: **Ride**, **Routes**, **Workouts**, and **Settings**.
Everything is stored on your device — there are no accounts and no cloud
sync, so the app works fully offline except for Bluetooth (to your trainer)
and, optionally, Strava.

### Connecting your trainer and heart rate monitor

Go to **Settings → Bluetooth Devices**. The app scans for:

- **Smart trainers** that support the standard FTMS (Fitness Machine
  Service) Bluetooth profile.
- **Heart rate monitors** that support the standard Bluetooth Heart Rate
  Service (most chest straps and armbands).

Tap **Connect** next to a device once it appears. There's no ANT+ support —
only Bluetooth LE. On Android you'll be asked to grant Bluetooth and
location permissions the first time you scan; this is required by Android
for Bluetooth scanning and isn't used to track your location.

Once connected, the trainer can be driven in two ways depending on what
you're doing:

- **Simulation mode** — when you ride a route, the app sends the route's
  real gradient to the trainer so resistance changes with the terrain.
- **ERG mode** — when you ride a workout, the app sends a target power
  (in watts) to the trainer, which holds that resistance regardless of your
  cadence.

### Setting up your profile

Go to **Settings → User Profile** and **Settings → FTP Settings** to set:

- **Weight (kg)** — used to simulate your speed on routes (heavier riders
  need more power to hold the same speed/gradient).
- **FTP (Functional Threshold Power, in watts)** — used to calculate ERG
  targets for workouts (a workout interval at "80%" means 80% of your FTP)
  and to show your time spent in each power zone after a ride.
- **Birth year (optional)** — used to estimate your max heart rate, which
  drives the heart-rate zone breakdown shown after a ride.

These settings are saved on-device and don't require an account.

## Riding

There's no separate "start ride" button — picking a route or a workout
takes you to the Ride tab and starts recording immediately. If you want to
ride without a specific route or workout, the app records a "Free Ride."

While riding you'll see live tiles for **watts**, **W/kg**, **speed**,
**cadence**, **calories**, and **heart rate** (if a monitor is connected).
If you're on a route, you'll also see an elevation profile with a marker
showing your position and a small map of the route shape. If you're doing
a workout, you'll see the current interval, its target power, and time
remaining.

**Auto-pause**: if you stop pedaling (cadence drops to 0), the ride
automatically pauses — the route/workout progress and resistance control
freeze, though the total ride timer keeps running. Pedal again to resume.

You can pause manually at any time, and end the ride with the stop button
(you'll be asked to confirm). At the end you'll see a results screen with
your stats and options to export the ride.

> **Demo mode**: without the one-time in-app purchase to unlock the full
> version, rides and workouts automatically stop after 10 minutes. Unlock
> from **Settings → Unlock Full Version**.

## Routes

Open the **Routes** tab to either:

- **Generate a route** — pick a target distance, elevation gain, a loop or
  out-and-back shape, and a terrain style (flat, rolling, hilly,
  mountainous). The app builds a synthetic elevation profile for you to
  ride against; the map shape shown is cosmetic, not real GPS.
- **Import a GPX file** — bring in a real route you've recorded or
  downloaded elsewhere. Only `.gpx` files are supported. Rides done on an
  imported GPX route carry real GPS coordinates, which is what allows the
  exported TCX file to include a map track (see below).

## Workouts

Open the **Workouts** tab to ride a structured interval session. Workouts
always drive your trainer in **ERG mode** — each interval sets a target
power as a percentage of your FTP, regardless of terrain.

- **Provided workouts**: 20 built-in workouts (Recovery, Endurance, Tempo,
  Sweet Spot, Threshold, VO2 Max, Anaerobic, Tabata, Over-Unders, Pyramid,
  Ladder, Hill Repeats, Criterium Simulation, Cadence Builder, an FTP Test,
  and more), ranging from 30 to 90 minutes. These can't be edited or
  deleted.
- **Your own workouts**: use the workout builder to drag interval blocks
  (Warmup, Work, Rest, Cooldown) onto a timeline, or add/edit intervals
  individually, setting each one's duration and target power. Save it with
  a name and it's added to your personal workout list.

There's currently no way to import workout files from other platforms
(such as Zwift `.zwo` or TrainerRoad `.erg`/`.mrc` files) — workouts are
either built in-app, chosen from the provided library, or restored from
this app's own JSON backup.

You can ride a route and a workout at the same time: the route's elevation
still scrolls by and is shown on screen, while the trainer's resistance is
controlled by the workout's ERG targets rather than the route's gradient.

## Exporting a ride to TCX

Every finished ride can be exported as a **TCX file** (Garmin Training
Center XML — a widely supported activity file format). You'll find an
**Export TCX** button on:

- The ride results screen (right after finishing a ride)
- Each entry in **Ride History**
- A ride's detail screen (opened from history)

Exporting opens your device's normal share sheet, so you can save the file,
AirDrop/send it, or hand it directly to another app.

**What's in the file**: total time, distance, calories, average/max heart
rate (if recorded), and a trackpoint for every second of the ride with
time, distance, heart rate, cadence, and power (watts). If the ride was on
an imported GPX route, trackpoints also include GPS position and altitude;
generated routes and free rides don't include GPS data since it isn't
real.

**What you can do with a TCX file**: it's a standard format accepted for
manual upload by most training/fitness platforms, including **Garmin
Connect**, **Strava**, **TrainingPeaks**, and **intervals.icu** — upload it
there to log the ride, analyze power/HR curves, or add it to your training
history on that platform.

**Direct Strava upload**: the app also has a built-in "Send to Strava"
option that uploads the same data straight to your Strava account without
handling a file yourself, via Strava's API. This requires connecting your
own Strava account in **Settings → Strava** first. Note that this feature
may not be turned on in every build of the app — if you don't see a
"Strava" option in Settings, use the manual TCX export/upload instead.

## Backing up and restoring your data

Since everything lives only on your device, it's worth backing up before
switching phones or reinstalling the app. Go to **Settings → Backup &
Restore**:

- **Export Backup** creates a JSON file containing your **profile**
  (weight, FTP, birth year) and your **own saved workouts**, and opens the
  share sheet so you can save it somewhere safe (Files, iCloud, Google
  Drive, email, etc.).
- **Import Backup** lets you pick a previously exported JSON file and
  restores your profile settings and merges the saved workouts back in
  (a workout already in the file replaces the matching one in the app;
  everything else is added — nothing you currently have gets deleted).

**What's not included in a backup**: your routes (generated or imported)
and your ride history are deliberately left out — this backup is meant as
a quick safety net for the two things that take real effort to redo (your
FTP/weight tuning and hand-built workouts), not a full clone of the app's
data. If you want to preserve individual rides, export each one as a TCX
file (see above) and/or upload them to a training platform before
switching devices.

## Ride history and stats

The **Ride History** list (reachable from the Ride tab) shows every
completed ride with distance, duration, average speed, average power, and
average heart rate. Swipe a ride to delete it, or tap it to see full
details, including:

- **Time in power zones** (if FTP is set) and **time in heart rate zones**
  (if birth year is set), using the standard 7-zone power model and a
  5-zone heart rate model.
- The same Export TCX (and, if enabled, Send to Strava) actions available
  from the results screen.

## Good to know

- The app is fully offline-capable — the only network use is Bluetooth to
  your trainer/HR monitor, and, only if you choose to use it, Strava.
- There's a single rider profile per install (one weight, one FTP, one
  birth year) — no multiple bike or rider profiles, and no accounts/login.
- The app uses one fixed dark theme; there's no light-mode toggle.
- The screen is kept awake automatically while you're riding.
- There's no leaderboard, best-effort, or personal-record tracking built
  in — use an exported TCX file on a platform like Strava if you want
  that.
