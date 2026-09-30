# Google Classroom connection setup

The app uses Google OAuth and the official Google Classroom API with read-only scopes for courses, coursework, materials, and announcements. The app never requests or stores a Google password.

1. In Google Cloud Console, create a project and enable **Google Classroom API**.
2. Configure the OAuth consent screen. Add the student account(s) under **Test users** while the app remains in testing mode.
3. Create an OAuth client ID of type **Web application**.
4. Add this authorized redirect URI: `http://localhost:4173/auth/google/callback`.
5. From the `outputs` folder, copy `.env.example` to `.env` and enter the OAuth client ID and secret there. The local server reads this file on startup; `.env` is excluded by `.gitignore` and blocked from the static file server. Alternatively, start the app with the OAuth client values in the server environment, for example in PowerShell:

   ```powershell
   $env:GOOGLE_CLIENT_ID = 'your-client-id.apps.googleusercontent.com'
   $env:GOOGLE_CLIENT_SECRET = 'your-client-secret'
   node .\server.cjs
   ```

   If you use another callback address, also set `GOOGLE_REDIRECT_URI` to that exact URI and add it to the Google OAuth client.
6. Restart the local server after configuring the values. Sign in to the student portal, choose **Attendance**, and connect Google Classroom. Google handles the sign-in and consent page. Use **Sync now** to refresh imported assignments, materials, and announcements.

Imported coursework with a due date is also included in the deadline planner. Manual attendance data is saved in that browser per student account; it is not read from Google Classroom or from SRM AP’s private student dashboard.
