# RFID Card Review & Attendance Dashboard

A static Firebase web dashboard for reviewing RFID UIDs uploaded by an ESP32. Users can approve/reject each UID and save student name, roll number, department, year/class and notes.

## Firebase setup
1. In Firebase Authentication, enable Email/Password and create a dashboard user.
2. Copy the Web API key from Project settings > General and replace `YOUR_FIREBASE_WEB_API_KEY` in `index.html`.
3. Configure Realtime Database rules to allow authenticated dashboard users to read `/scannedUIDs` and `/cards`, and write `/cards`. Allow the ESP32 device account to write `/scannedUIDs`.
4. Upload these files to GitHub and import the repository in Vercel. No build command is needed.

## Data flow
- ESP32 writes only `{ "uid": "04A12BC3" }` under `/scannedUIDs`.
- Dashboard writes human-reviewed card metadata separately under `/cards/{UID}`.
- Approve/reject status does not automatically change what the ESP32 accepts. If access decisions must affect hardware, firmware/backend logic must check approved status before treating a card as accepted.

## Security
Use restrictive rules and appropriate accounts. Do not put Firebase passwords or service-account credentials in the repository. For production, enforce roles and approval permissions in database rules or a trusted backend.
