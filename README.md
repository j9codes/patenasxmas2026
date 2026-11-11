# The Patenas Christmas 2026 - wishlist
Designed by J9. Static site (GitHub Pages) + Firebase (free plan) for logins and data.

## Part 1: Firebase
1. https://console.firebase.google.com -> **Add project** -> name it `patenas-christmas-2026` -> turn Analytics off.
2. **Build -> Authentication -> Get started -> Sign-in method -> Email/Password -> Enable -> Save.**
3. **Build -> Firestore Database -> Create database** -> **production mode** -> pick the nearest region.
4. **Firestore -> Rules** -> delete everything, paste the contents of `firestore.rules` -> **Publish**.
5. **Firestore -> Data -> Start collection** -> collection ID `settings` -> Document ID `app` (type it; do not use Auto-ID) -> field `code`, type **string**, value = your family invite code.
6. **Project settings (gear) -> General -> Your apps -> Web (</>)** -> nickname `wishlist` -> Register (no hosting) -> copy the `firebaseConfig` values.

## Part 2: The page
7. Open `index.html`, replace the `PASTE` values in `firebaseConfig` with your 4 values (apiKey, authDomain, projectId, appId).
8. Optional: edit `EVENT_DATE` if the date isn't 25 Dec 2026.

## Part 3: GitHub
9. github.com -> **New repository** -> name e.g. `patenas-xmas-2026` -> **Public** -> Create.
10. **Add file -> Upload files** -> drag in `index.html`, `firestore.rules`, `README.md` (top level, no folders) -> **Commit changes**.
11. **Settings -> Pages -> Build and deployment -> Deploy from branch -> main / (root) -> Save.** After 1-2 minutes the site is at `https://YOUR-GITHUB-USERNAME.github.io/patenas-xmas-2026/`.

## Part 4: Connect them
12. Firebase -> **Authentication -> Settings -> Authorized domains -> Add domain** -> `YOUR-GITHUB-USERNAME.github.io` (domain only).
13. Open the site, hard-refresh (Ctrl+Shift+R / Cmd+Shift+R), check the small "v1" next to the title.
14. Sign up with your invite code. Share the link and code with the family.

Never put your invite code in a file in the public repo. Forgotten password: delete the user in Firebase -> Authentication -> Users; they sign up again.
