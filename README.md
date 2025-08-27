# Uber Ride Data Collector

A one-click web application for Uber drivers to capture real-time ride data—including timestamps, geolocation, and fare information—directly into a Google Sheet. This project is designed to enable a more accurate calculation of a driver's true hourly earnings by accounting for all segments of the ride cycle, from searching for a fare to its completion.

---

### 📍 [Live Application Demo](https://your-username.github.io/your-repository-name/)

*(**Note:** Replace the link above with your actual GitHub Pages URL after you deploy it.)*

---

## ✨ Features

-   **One-Click Data Capture:** Log different stages of a ride (`Looking for Rides`, `Driving to Pickup`, `Waiting`, `Completed`) with a single button press.
-   **Accurate Timestamps:** Captures the timestamp the *instant* a button is clicked, ensuring data integrity even if there's a delay in entering subsequent information.
-   **Geolocation Stamping:** Automatically records the device's latitude and longitude for each event, allowing for spatial analysis.
-   **Dynamic Fare Input:** Prompts for "Upfront Fare" on ride acceptance and "Realized Fare" on ride completion.
-   **Serverless & Free:** Built with a serverless architecture using Google Apps Script and hosted for free on GitHub Pages.
-   **Centralized Data:** All data is securely and neatly stored in a private Google Sheet, acting as a simple, effective database.

---

## 🏗️ System Architecture

The application operates on a simple, three-part serverless architecture:

1.  **Frontend (Client):** A static `index.html` file containing HTML, CSS, and JavaScript. This is the user interface you interact with on your phone's browser. It is hosted on **GitHub Pages**.
2.  **Backend (API Bridge):** A **Google Apps Script** deployed as a web app. It acts as a secure intermediary, receiving data from the frontend via an HTTP POST request.
3.  **Database:** A **Google Sheet** serves as the data store. The Google Apps Script has permission to append new rows to this sheet, effectively making it a simple, no-cost database.

```
[ Frontend: Web App on Phone ] --- (sends data via POST request) ---> [ Backend: Google Apps Script URL ] --- (writes data) ---> [ Database: Google Sheet ]
```

---

## 🛠️ Technology Stack

-   **Frontend:** HTML5, CSS3, JavaScript (ES6)
-   **Backend:** Google Apps Script (JavaScript-based)
-   **Database:** Google Sheets
-   **Hosting:** GitHub Pages

---

## 🚀 Setup & Installation Guide

To deploy your own instance of this tracker, follow these steps:

### 1. Google Sheet & Script Setup

1.  **Create a Google Sheet:**
    -   Go to [sheets.google.com](https://sheets.google.com) and create a new blank spreadsheet.
    -   Add the following headers in the first row (A1 to H1):
        `Timestamp`, `Ride ID`, `Status`, `Latitude`, `Longitude`, `Address`, `Upfront Fare`, `Realized Fare`.

2.  **Create the Google Apps Script:**
    -   In your sheet, navigate to `Extensions` > `Apps Script`.
    -   Delete any existing code and paste in the full contents of the `Code.gs` file from this repository.
    -   Click the **Deploy** button, select **New deployment**, and configure it as follows:
        -   **Type:** Web app
        -   **Execute as:** Me
        -   **Who has access:** Anyone
    -   Click **Deploy**, authorize the script's permissions, and **copy the generated Web app URL**.

### 2. Frontend Setup

1.  **Clone or download this repository.**
2.  **Edit `index.html`:**
    -   Open the `index.html` file in a text editor.
    -   Find the following line of JavaScript:
        ```javascript
        const webAppUrl = "PASTE_YOUR_GOOGLE_SCRIPT_WEB_APP_URL_HERE";
        ```
    -   Replace `PASTE_YOUR_GOOGLE_SCRIPT_WEB_APP_URL_HERE` with the URL you copied from your Google Apps Script deployment.

### 3. Deploy to GitHub Pages

1.  **Create a new public repository** on your GitHub account.
2.  **Upload the edited `index.html` file** to this repository.
3.  **Enable GitHub Pages:**
    -   In the repository, go to `Settings` > `Pages`.
    -   Under the "Branch" section, select `main` and `/root`.
    -   Click **Save**. Your site will be live at the provided URL within a few minutes.

---

## 📈 How to Use

1.  **Open the Web App:** Navigate to your GitHub Pages URL on your phone's browser. It's recommended to "Add to Home Screen" for quick access.
2.  **Set Daily Ride ID:** At the start of your shift, enter a unique ID for the day (e.g., `2025-08-27`).
3.  **Log Your Activity:**
    -   Tap **Looking for Rides** when you start searching.
    -   Tap **Accepted Ride** when you accept a trip. A prompt will appear to enter the **Upfront Fare**.
    -   Tap **Waiting for Passenger** if you arrive at the pickup and have to wait.
    -   Tap **Ride Completed** at the end of the trip. A prompt will appear to enter the **Realized Fare**.
4.  **Analyze Your Data:** All data is now available in your Google Sheet for analysis and visualization.

---

## 🔮 Future Improvements

-   **Reverse Geocoding:** Integrate a service like the Google Maps API to convert the captured latitude and longitude into human-readable street addresses.
-   **Data Dashboard:** Connect the Google Sheet to a BI tool like Google Data Studio (Looker Studio) to create a dashboard for visualizing earnings, time spent per ride stage, and profitability heatmaps.
-   **Offline Functionality:** Implement a Service Worker to cache data entries when offline and sync them to the Google Sheet once an internet connection is restored.
-   **Ride ID Management:** Automatically generate or increment Ride IDs to reduce manual input.

---

## 📄 License

This project is licensed under the **MIT License**. See the `LICENSE` file for details.
