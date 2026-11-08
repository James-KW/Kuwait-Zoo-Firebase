# Kuwait Zoo Firebase site

A public population view and Firebase-authenticated admin editor for the Kuwait Zoo species collection.

## Files
- `index.html` — public real-time view.
- `admin-login.html` — Firebase Email/Password sign-in.
- `zooinfo.html` — authenticated editor; saves documents under `species/{speciesId}`.
- `firebase-config.js` — Firebase web app configuration.

## Firebase requirements
1. Enable **Authentication → Email/Password** and create the admin account.
2. In Firestore Rules, allow public reads of `species` documents and allow writes only when the authenticated UID is your admin UID. Do not use a rule that allows all signed-in users to write.
3. The web config is public client configuration, not a private key. Restrict its API key to your site domains in Google Cloud; never commit passwords or service-account keys.
4. Open the pages through a web host (GitHub Pages, Vercel, etc.) rather than `file://`, because browser ES modules need HTTP(S).

The editor works with documents in `species`. It seeds the listed species with zero counts when no matching document exists. The existing image assets can be added later; these pages do not require them.
