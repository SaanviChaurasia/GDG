# Evently — SRM AP

Evently is a local prototype for coordinating student assignments, campus events, and attendance. It includes separate Student, Faculty, and Campus Team portals, deadline prioritization, an attendance dashboard, event/class conflict warnings, and an optional Google Classroom read-only sync.

## Run locally

Requires Node.js 18 or newer. From this folder, run:

```powershell
node .\server.cjs
```

Open [http://localhost:4173](http://localhost:4173). Runtime records are written to local JSON files and are excluded from Git.

## Google Classroom

Google Classroom requires an OAuth web client. Follow [google-classroom-setup.md](google-classroom-setup.md), add your OAuth client values to a local `.env` copied from `.env.example`, restart the server, then connect from the Student portal’s Assignments view. Do not commit `.env` or share its client secret.

## Hosting

This project includes a Node.js backend, so GitHub Pages alone cannot run the complete app. Deploy the Node server to a compatible host and update the OAuth redirect URI to match that host before enabling Classroom sign-in.
