# Player of the Match

Parents vote for a weekly Player of the Match. Parents see only the winner; vote counts and season totals are admin-only.

- `index.html`: the parents' page (share this link)
- `admin.html`: your page (open votes, manage players and photos, reveal the winner)
- `firebase-config.js`: your Firebase project settings
- `firestore.rules`: the security rules that do the real protection

## One-time setup

1. **Create a Firebase project** at console.firebase.google.com. The free Spark plan is enough.
2. **Add a web app** (Project settings > General > Your apps > Web). Copy the config into `firebase-config.js`.
3. **Turn on sign-in methods** (Build > Authentication > Sign-in method): enable **Anonymous** and **Email/Password**.
   Then in the Users tab, **Add user** with your email and a password. That's your admin login.
4. **Create the database** (Build > Firestore Database > Create database), production mode, location `europe-west2` (London).
5. **Authorised domain** (Authentication > Settings > Authorised domains): add `deanodealo.github.io`.
6. **Push this folder to GitHub** and turn on Pages (Settings > Pages > main / root).
7. **Open `admin.html`** on the live site and sign in. It shows your user ID. Paste it into `firestore.rules`
   in place of `PASTE_YOUR_ADMIN_UID`, then deploy the rules from this folder:
   ```
   firebase login
   firebase use --add        (pick your project)
   firebase deploy --only firestore:rules
   ```
   Or paste the rules into Firestore > Rules in the console and click Publish.
8. **Reload `admin.html`.** In Settings, set the team name and team code. Add players in Players.

## Each week

1. `admin.html` > Vote: type the opponent, check the ballot and the closing time, tap **Open voting**, share the link.
2. After it closes: **Pick the winner**, untick any comments you don't want shown, **Reveal**.
3. Share the winner graphic to the group if you like.

## Safeguarding

- First names only. Photos only with parental consent (the Photo consent toggle gates uploads, and turning it off deletes the photo).
- Photos live in Firestore behind the team code, never in this repo.
- Both pages ask search engines not to index them.
- Delete photos (or players) when a player leaves or at the end of the season.
