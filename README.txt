CHUD ZONE 6.1.1 — getting it onto your phone
======================================

What's in this folder (this IS the whole app):
  index.html              the app shell + storage layer
  app.js                  the app itself (React + charts, bundled, no internet needed)
  sw.js                   service worker — makes it work offline in the gym
  manifest.webmanifest    tells your phone it's an installable app
  icon-192.png            home screen icon
  icon-512.png            home screen icon (large)
  icon-512-maskable.png   Android adaptive icon

IMPORTANT: it will NOT work if you just open index.html from your phone's
Files app. Service workers and installability require it to be served over
https. Hosting it is free and takes about two minutes — see below.


OPTION 1 — Netlify Drop (easiest, no account needed to start)
-------------------------------------------------------------
1. On a computer, go to  https://app.netlify.com/drop
2. Drag this entire folder onto the page.
3. Wait ~15 seconds. You get a URL like  https://shiny-name-123abc.netlify.app
4. Open that URL on your phone.
5. Install it (see "PUT IT ON YOUR HOME SCREEN" below).

Make a free Netlify account when prompted, otherwise the site expires after
a day or so and your URL dies. The account is free forever at this size.


OPTION 2 — GitHub Pages (free, permanent, you already know git)
---------------------------------------------------------------
1. Make a new public repo, e.g.  chud-zone
2. Upload every file in this folder to the repo ROOT (not in a subfolder).
   Web upload works fine: repo > Add file > Upload files > drag them all in.
3. Repo > Settings > Pages
4. Under "Build and deployment", Source = "Deploy from a branch",
   Branch = main, Folder = / (root). Save.
5. Wait 1-2 minutes. Your URL is:
      https://YOUR-USERNAME.github.io/chud-zone/
6. Open it on your phone and install it.


OPTION 3 — Cloudflare Pages (free, permanent, fastest)
-------------------------------------------------------
1. Sign in at https://dash.cloudflare.com > Workers & Pages > Create > Pages
2. "Upload assets", name the project, drag this folder in, Deploy.
3. You get  https://chud-zone.pages.dev  — open it on your phone.


PUT IT ON YOUR HOME SCREEN
---------------------------
iPhone (must be Safari — Chrome on iOS cannot install web apps):
  1. Open your URL in Safari.
  2. Tap the Share button (square with the up arrow).
  3. Scroll down, tap "Add to Home Screen".
  4. Name it "Chud Zone", tap Add.
  It now opens full screen with no browser bars, like a normal app.

Android (Chrome):
  1. Open your URL in Chrome.
  2. Tap the three-dot menu.
  3. Tap "Install app" (or "Add to Home screen").
  4. Confirm.

After installing, open it ONCE while you still have signal. That first run
caches everything. After that it works with no signal at all.


WHERE YOUR DATA LIVES
----------------------
On the phone itself, in that browser's storage. It never leaves your device
and there is no account or server. Two consequences:

  - It does not sync between your phone and computer. Separate logs.
  - Clearing your browser data, or deleting the app, erases your log.

So: Setup tab > "Save a backup file" every few weeks. It downloads a small
JSON file. "Restore from a backup" loads it back, on any device.


USING IT
---------
First launch walks you through units, experience level and picking a split.

TODAY     Three stages, in order.
          PLAN — pick the day, then pick the movements you actually want
          for each muscle. Sets and weights are pre-filled from your last
          session or the coach's suggestion; change any of it. Then hit
          Start.
          WORKOUT — a separate full-screen view, one movement at a time,
          with a strip along the top to jump between them. Tabs and nav get
          out of the way. Swap a movement or add a set mid-session. Reps in
          reserve, pump and joint pain are asked per movement, right after
          you finish it. Hit End when you're done.
          SUMMARY — sets, reps, weight moved, any personal bests, and what
          the coach changed for next time.
          A CHECK-IN appears at the top of Plan a day or two after a
          session, asking how sore that training left you. That is what
          moves your weekly volume, because soreness peaks well after you
          train rather than right before the next session.
LOG       Anything outside the plan. Does not feed the coach.
STATS     Progress (overlay up to 5 movements), Volume, Cardio, Calendar
          and History.
SETTINGS  A menu: Your split, Movements, Appearance (six accent colours,
          true-black option), Training rules, Gym setup, Preferences, Your
          data, How this works.

ODDS AND ENDS
--------------
  * Hold the + or - on any number field to run it up fast.
  * Long-press the home screen icon for Start workout / Log cardio / Stats.
  * "Repeat my last session" reloads your previous workout as a starting
    point.
  * Setup notes per movement (seat height, pin, grip) show while you train.
  * Warm-up ramps are suggested on your first set. Never logged, never
    counted as volume.
  * Deleting a session leaves an Undo strip for a few seconds.
  * Share a finished session as text, or export everything to CSV.
  * Stats > Balance shows your push/pull/legs split and flags a lopsided
    ratio.
  * Milestones and a seven-day recap live in Stats.

