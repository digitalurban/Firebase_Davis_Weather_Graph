# Weather Data Visualization

This project visualizes weather data stored in a Firebase Realtime Database using Chart.js from a Davis weather station  'Loop' MQTT file.

The graph dynamically updates and displays live weather data, including wind speed, pressure, and rainfall. A responsive toolbar allows switching between different time ranges.

![Weather Graph](https://github.com/digitalurban/Firebase_Davis_Weather_Graph/blob/main/screenshot.png)

## Features

- **Real-time Updates**: Automatically fetches and displays live weather data from Firebase.
- **Responsive Design**: Optimized for various screen sizes.
- **Interactive Toolbar**: Switch between last 1, 6, or 12 hours of data.
- **Status Indicator**: Green dot pulses when new data is received; turns red if no updates in the last 10 seconds.

## How to Set Up

1. **Clone or Download** this repository.
2. **Set up Firebase**:
   - Visit [Firebase Console](https://console.firebase.google.com/).
   - Create a new project and enable the Realtime Database.
   - Add weather data to a node named `loopData`. Data format example:
     ```json
     {
       "loopData": {
         "unique-id-1": {
           "timestamp": 1637592000000,
           "windSpeed_mph": 5.2,
           "pressure_mbar": 1013.4,
           "dayRain_mm": 2.1
         },
         ...
       }
     }
     ```
      - Go to **Project Settings > General** and scroll down to the **Your Apps** section.
   - Select **Add App** and choose **Web**.
   - Copy the Firebase configuration snippet and replace the placeholder `firebaseConfig` object in the HTML file with your Firebase credentials.

3. **Host the App** (optional):
   - You can use Firebase Hosting, GitHub Pages, or any web hosting service to host this HTML file.
   - For Firebase Hosting:
     - Install Firebase CLI: `npm install -g firebase-tools`
     - Initialize Firebase in your project: `firebase init hosting`
     - Deploy your app: `firebase deploy`

4. **Open the HTML file** in a browser:
   - Double-click the file to open it locally, or upload it to a web server for public access.

## Data Requirements

The Firebase Realtime Database must have a node named `loopData` containing weather data. Each entry should include the following fields:
- `timestamp`: Unix timestamp in milliseconds.
- `windSpeed_mph`: Wind speed in miles per hour (numeric).
- `pressure_mbar`: Atmospheric pressure in millibars (numeric).
- `dayRain_mm`: Daily rainfall in millimeters (numeric).

These can be edited depending on what data you want to display from the Loop Packet.

Example entry:
```json
{
  "timestamp": 1637592000000,
  "windSpeed_mph": 7.5,
  "pressure_mbar": 1012.6,
  "dayRain_mm": 3.2
}

