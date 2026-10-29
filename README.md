# RFID Smart Attendance Dashboard

Static HTML dashboard for Firebase project `smartattendance-7923a`.

## Features
- Live scan UID list and approve/reject workflow
- Student name, roll number, department, year/class and notes
- Scan history view
- Individual student scan-event history and counts
- Firebase email/password authentication
- Vercel static deployment

## Data paths
- ESP32 scan events: `/scannedUIDs`, each record should contain `{ "uid": "04A12BC3" }`
- Student/card information: `/cards/{UID}`

## Deploy
Upload `index.html`, `README.md`, `vercel.json`, and `.gitignore` to the root of a GitHub repository and import it into Vercel. No build command is needed. Check that the Firebase Web API key in `index.html` is the one from your Firebase project.

## History limitation
The ESP32 currently sends only the UID, so no timestamp is saved. History shows Firebase event keys and scan-event counts, not verified daily attendance. To report date/time or daily present/absent status, the ESP32 must send a timestamp or a trusted server must add one, and class/session rules must be defined.

## Security
Use Firebase Authentication and restrictive Realtime Database rules. Do not publish device passwords or service-account credentials. The web API key identifies the Firebase project; it is not a substitute for database security rules.
