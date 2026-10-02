# AD400 PM Rotation Tracker

Static page for GitHub Pages. Checkmarks, PM swaps and the current week are shared live through Firebase Firestore (free Spark plan).

## One-time setup (about 10 minutes)

1. Go to https://console.firebase.google.com and create a project (turn Google Analytics off).
2. Build > Firestore Database > Create database > start in production mode, any region.
3. Firestore > Rules tab, replace the rules with the following and click Publish:

       rules_version = '2';
       service cloud.firestore {
         match /databases/{database}/documents {
           match /tracker/main {
             allow read, write: if true;
           }
         }
       }

   This lets anyone who has the page's URL edit the one tracker document and nothing else.
4. Project settings (gear icon) > Your apps > Web (</>) > register an app. Copy the config object into `firebase-config.js`.
5. Push these files to a GitHub repo, then Settings > Pages > Deploy from branch `main`, folder `/ (root)`.
6. Share the Pages URL with the team.

## Changing the rotation

Edit the `CYCLES` block near the top of the script in `index.html`: one list of four names per cycle, for weeks 1-4, 5-8 and 9-12.
