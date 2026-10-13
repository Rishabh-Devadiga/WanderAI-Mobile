# WanderAI — AI-Powered Travel Planning App

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android" />
  <img src="https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/TypeScript-Strict-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Capacitor-Android-119EFF?style=for-the-badge&logo=capacitor&logoColor=white" alt="Capacitor" />
</p>

**WanderAI** is an AI-powered travel planning application designed to make trip planning more personalized, intuitive, and convenient. Travelers can describe their travel preferences, explore destinations, generate itineraries, and manage their travel plans through a mobile-friendly interface.

The mobile application connects to the WanderAI backend, which provides trip-related APIs and AI-powered functionality. It is part of a broader travel platform that also includes an operator dashboard for managing trips and travel operations.

## 📲 Download the Android App

**Latest release: v1.0.0**

[![Download WanderAI APK](https://img.shields.io/badge/Download-WanderAI%20APK-2ea44f?style=for-the-badge&logo=android&logoColor=white)](https://github.com/Rishabh-Devadiga/WanderAI-Mobile/releases/download/v1.0.0/app-debug.apk)

**[Download WanderAI for Android](https://github.com/Rishabh-Devadiga/WanderAI-Mobile/releases/tag/v1.0.0)**

### Installation

1. Download the APK using the link above.
2. Open the downloaded APK on your Android device.
3. Allow installation from this source if Android requests permission.
4. Tap **Install** and launch WanderAI.

> **Note:** The published APK is a development/debug build. The application requires a reachable backend to use server-dependent functionality. The backend URL must be configured for the network where the app is being used.

## ✨ Features

### 🧠 AI-Powered Travel Planning
- Describe your travel plans using natural language.
- Extract travel preferences such as destination, duration, budget, interests, and companions where supported.
- Generate personalized travel itineraries.
- Adapt trip suggestions to the traveler's requirements.

### 🗺️ Interactive Itineraries
- View trip destinations, schedules, and activities.
- Explore day-by-day travel plans.
- View destination imagery and place-related media when available.
- Review itinerary details, estimated budgets, and transportation information.
- Modify travel arrangements through supported itinerary controls.

### 🏨 Travel Discovery
- Discover hotel options through the connected backend.
- Explore activities and destinations.
- Research transportation options for supported routes.
- Review available pricing and provider details where supplied by connected services.

### 🔄 Connected Travel Platform
- Communicate with the WanderAI backend through REST APIs.
- Persist and retrieve trip information through backend services.
- Connect traveler trip planning with the operator's trip-management workflow.
- Support a shared trip lifecycle between traveler and operator experiences.

*Feature availability depends on backend connectivity, configured providers, and available inventory.*

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| React 19 | User interface |
| TypeScript | Type-safe application development |
| Vite | Development server and production bundling |
| Tailwind CSS | Styling and responsive UI |
| Capacitor | Native Android application wrapper |
| React Router | Client-side navigation |
| Leaflet | Interactive maps |
| Lucide | Interface icons |
| jsPDF | PDF generation where implemented |
| FastAPI | Backend API |
| PostgreSQL | Persistent backend data |

## 🏗️ System Architecture

WanderAI uses a client-server architecture.

```text
┌──────────────────────────────┐
│       WanderAI Mobile        │
│       React + TypeScript     │
│       Capacitor / Android    │
└──────────────┬───────────────┘
               │
               │ REST API / JSON
               ▼
┌──────────────────────────────┐
│       WanderAI Backend       │
│          FastAPI             │
│                              │
│  Authentication              │
│  Trip Management             │
│  AI Travel Services          │
│  Itinerary Operations        │
└──────────────┬───────────────┘
               │
       ┌───────┴────────┐
       ▼                ▼
┌──────────────┐  ┌────────────────┐
│ PostgreSQL   │  │ AI / External  │
│ Database     │  │ Travel Services│
└──────────────┘  └────────────────┘
```

The backend acts as the central source of truth for persisted trip data. The separate Operator-Web application consumes the same backend so that traveler trips can be managed through the operations workflow.

## 📂 Project Structure

```text
WanderAI-Mobile/
├── android/                 # Native Android project
├── public/                  # Static assets and API config
│   └── api-config.json      # Shipped backend URL configuration
├── src/
│   ├── api/                 # API client and service modules
│   ├── pages/               # Application pages
│   ├── components/          # Reusable UI components
│   └── ...                  # Application source code
├── capacitor.config.ts      # Capacitor configuration
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

*Some generated or platform-specific files may vary depending on the current checkout.*

## 🚀 Getting Started

### Prerequisites

Install the following tools before running the project:

- [Node.js](https://nodejs.org/) — compatible with the project's dependencies
- npm
- [Android Studio](https://developer.android.com/studio) — required for Android builds
- Android SDK — required for compiling and installing the Android application
- A running or deployed WanderAI backend

### 1. Clone the Repository

```bash
git clone https://github.com/Rishabh-Devadiga/WanderAI-Mobile.git
cd WanderAI-Mobile
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure the Backend URL

Open:

```text
public/api-config.json
```

Configure it with the URL of your running backend:

```json
{
  "apiUrl": "http://YOUR_BACKEND_HOST:8000"
}
```

Replace `YOUR_BACKEND_HOST` with the appropriate hostname or IP address.

**Important:**
- For local development, use an address reachable from the device or browser.
- `localhost` inside an Android emulator or on a physical phone refers to that device, not automatically to your development computer.
- For a physical device, the computer's LAN IP can work when both devices are on the same network and the backend allows connections.
- For public distribution, configure a publicly reachable HTTPS backend.

Do not put private API keys or database credentials in the frontend configuration.

### 4. Start the Development Server

```bash
npm run dev
```

Open the local URL printed by Vite in your browser.

### 5. Run Type Checking and Build

```bash
npm run lint
npm run build
```

The production frontend bundle is generated in the `dist/` directory.

## 📱 Building the Android APK

WanderAI uses Capacitor to package the web application as a native Android app.

### 1. Build the Web Application

```bash
npm run build
```

### 2. Synchronize the Android Project

```bash
npm run android:sync
```

### 3. Open Android Studio

```bash
npm run android:open
```

If the Android platform has not yet been added to the project, initialize it using the appropriate Capacitor command before syncing.

### 4. Generate the APK

In Android Studio:

1. Wait for Gradle synchronization to finish.
2. Select **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
3. Wait for the build to complete.
4. Locate the generated debug APK.

The usual output path is:

```text
android/app/build/outputs/apk/debug/app-debug.apk
```

You can install the APK on a compatible Android device for testing.

## 🔌 Backend Integration

The mobile application depends on the WanderAI backend for server-side features.

The backend repository is maintained separately:

**[WanderAI Backend](https://github.com/Rishabh-Devadiga/WanderAI-Backend)**

The backend is responsible for API operations such as authentication, trip persistence, itinerary-related functionality, and AI-powered services.

To run the backend locally, follow its own README and environment configuration instructions. Never commit `.env` files, API keys, database passwords, or other secrets.

## 🔐 Configuration and Security

Before distributing a public build:

- Use HTTPS for the deployed backend.
- Ensure the API URL is configured for the intended environment.
- Do not embed private AI-provider keys in the mobile application.
- Keep secrets in backend environment variables.
- Review Android network security and cleartext traffic settings before production release.
- Test authentication, API failures, and offline/network-loss scenarios.

## 🗺️ Related Project

WanderAI is part of a broader travel platform.

| Component | Description |
|---|---|
| **WanderAI-Mobile** | Traveler-facing Android application |
| **WanderAI-Backend** | Central API, trip state, and AI services |
| **Operator-Web** | Operator dashboard for trip and travel operations |

## 🔮 Future Improvements

Potential areas for further development include:

- Production-signed Android releases
- Improved offline and network recovery behavior
- More robust live hotel and transportation integrations
- Enhanced itinerary personalization
- Better traveler notifications and trip updates
- Expanded AI-assisted travel and disruption workflows

These are possible improvements rather than a claim that every item is already implemented.

## 👨‍💻 Author

**Rishabh Devadiga**

GitHub: [@Rishabh-Devadiga](https://github.com/Rishabh-Devadiga)

## 📄 License

No license is specified here. Add a `LICENSE` file and update this section if you intend to publish the project under an open-source license.

---

<p align="center">
  <strong>WanderAI</strong><br/>
  Plan smarter. Explore further. Travel better.
</p>