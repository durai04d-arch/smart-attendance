# RFID Smart Attendance Dashboard

Static HTML/CSS/JavaScript dashboard for an ESP32 MFRC522 RFID reader, using Firebase Authentication and Realtime Database.

## Setup

1. In Firebase Console, enable Authentication > Email/Password and create a dashboard user.
2. Copy the Web API key from Project settings > General.
3. Open `index.html` and replace `YOUR_FIREBASE_WEB_API_KEY`.
4. Ensure Realtime Database rules allow the signed-in dashboard user to read `/scannedUIDs`, and the ESP32 device account to write to it.
5. Commit these files to a GitHub repository and import the repository into Vercel. No build command is needed.

## Expected data

The ESP32 posts records such as:

```json
{ "uid": "04A12BC3" }
```

The dashboard listens to `/scannedUIDs` and displays up to the latest 500 records.

## Security

Do not commit passwords or service-account credentials. Use Firebase Authentication and restrictive Realtime Database rules. This dashboard uses the Firebase Web SDK; the API key identifies the project and is not a password.
