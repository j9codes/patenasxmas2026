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
7. Open `index.html` and find the `firebaseConfig` block. Replace only the text between the quotes for `apiKey`, `authDomain`, `projectId` and `appId`. **Do not paste Firebase's whole code box** (its `<script>` tags, `import` lines or `const app = initializeApp(...)` line); that breaks the page. Leave the `TITLE`, `GROUP`, `EVENT_NAME`, `EVENT_DATE`, `MAX` and `DOMAIN` lines as they are.
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

## If something doesn't work
- Blank page or no title: the script has an error. Press F12 -> Console and read the red message. Usual cause: a mistake while pasting the Firebase config (see step 7).
- "Could not join (permission-denied)": check the invite code (step 5: document ID `app`, field `code`, type string) and that the rules are published (step 4).
- Sign-in fails on the live site: the domain is missing from Authorized domains (step 12).
- Group notes show a red "Can't load" message: publish the latest `firestore.rules` (step 4), then reload.
