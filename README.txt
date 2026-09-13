CHUD ZONE
=========

A lifting app that adjusts itself. You log what you did and how it felt,
and it works out what you should do next time.

Everything lives on your phone. No account, no sign-in, nothing gets sent
anywhere, and it works with no signal once it's installed.


PUTTING IT ON YOUR PHONE
------------------------

This folder is the whole app. Opening index.html straight off your phone
won't work though, it has to be served over https first. Hosting it is
free.

Easiest option is Netlify Drop. Go to app.netlify.com/drop on a computer,
drag this folder onto the page, wait about fifteen seconds, and you get a
URL. Make the free account when it asks or the site disappears after a day.

If you'd rather use GitHub Pages: new public repo, upload every file in
this folder to the root, then Settings > Pages, deploy from main branch,
root folder. Your URL ends up as username.github.io/whatever-you-called-it.

Cloudflare Pages works too. Dashboard > Workers & Pages > Create > Pages >
Upload assets.

Then on your phone:

Android, open the URL in Chrome, three dots, Install app. You get a real
app drawer entry and its own window.

iPhone, it has to be Safari, Chrome can't do this. Share button, Add to
Home Screen.

Open it once while you still have signal so it can cache everything. After
that it runs offline.


HOW IT WORKS
------------

HOME is the landing screen. Date, what's up next in your split, how the
week's going, and what you did last time with how long ago it was.

TRAIN is where the work happens, in three parts.

First you plan. Pick the day, pick the movements you actually feel like
doing for each muscle. Sets and weights fill in from your last session or
from what the coach suggests. Change whatever you want.

Then you hit start and get a clean screen, one movement at a time, with a
strip up top to jump around. After each movement it asks how many reps you
had left, how the pump was, and whether anything hurt. Hit end when you're
done and you get a summary with any personal bests and what changed for
next time.

A day or two later it asks how sore that session left you. That's the bit
that sets your volume, and it's asked then rather than before your next
workout because soreness peaks well after you train.

Cardio gets its own screen. Hit log cardio from home or from the train
tab, put in the time and distance and how hard it was, save, and it closes
itself. Easy sessions count as recovery. Anything harder counts as
training, and a hard run in the last day or two pulls back your leg sets to
match.

STATS has progress charts you can stack several lifts onto, weekly volume
against your floor and ceiling, cardio, a consistency calendar and your
full history.

SETTINGS covers your split, movements, how it looks, training rules, what
your gym actually has, and backups.


SMALLER THINGS WORTH KNOWING
----------------------------

Hold the plus or minus on any number to run it up fast.

Long press the app icon for start workout, log cardio, or stats.

"Repeat my last session" pulls your previous workout in as a starting
point.

You can leave a note on any movement, seat height and pin number and so
on, and it shows up while you're training.

It suggests a warm-up ramp on your first set. Those aren't logged and don't
count toward volume.

Delete a session by mistake and there's an undo for a few seconds.

You can share a finished session as text or dump everything to a CSV.

Home shows which muscles are overdue against your split, which are still
recovering, and which lift you're closest to beating.

Stats > Balance tells you if you're pressing way more than you pull.


YOUR DATA
---------

It sits on your phone in that browser's storage. Nothing syncs, so your
phone and your computer would be separate logs.

Clearing Chrome's site data wipes it. So does uninstalling. So go to
Settings > Your data and save a backup every few weeks. It's a small file
that lands in Downloads and restores on any device.

The other thing that wipes it is moving the app to a different web
address, because the storage is tied to the exact URL. Pick one before you
share it around and stay there.


UPDATING IT
-----------

Replace the changed files in your repo, same names, same folder. Then bump
CACHE at the top of sw.js, for example chud-zone-6.3.0 to chud-zone-6.3.1.
If you skip that step phones just keep serving the old copy.

Don't rename the repo. Don't touch start_url or scope in
manifest.webmanifest and don't add an id field. Those three are how Android
knows it's the same app. Change one and phones treat your update as a
different app, so a second icon shows up and the original keeps all the
data.

Nobody needs to reinstall. Next time they open it the app notices the new
version and shows a banner. They tap it and everything's still there.

Training logs live in a different place from the app files, so updates
never touch them. The save also carries a format version, and on launch the
app runs whatever migrations it needs and writes the result back. Someone
who skipped four releases lands on the current format with their history
intact. It saves a copy of the old data first, and there's a roll back
button under Settings > Your data if something goes sideways.

If the icon still looks like the old one after an update, that's normal.
Android baked it into the shortcut and Chrome only re-reads the manifest
about once a day. It'll sort itself out. Don't uninstall to hurry it along,
that's the one thing that actually loses a training log.


WHAT'S IN HERE
--------------

  index.html              the shell and storage layer
  app.js                  the app itself, bundled, no internet needed
  sw.js                   makes it work offline
  manifest.webmanifest    tells your phone it's installable
  icon-192.png            home screen icon
  icon-512.png            larger icon
  icon-512-maskable.png   Android adaptive icon


Not medical advice. Lifting carries real risk and this can't see your form.
If something hurts, stop.
