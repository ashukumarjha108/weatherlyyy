# 🌦️ Weather App

A modern Android weather application built using **Kotlin** and **Jetpack Compose**, integrating **Retrofit** for network calls, **Room** for local storage, and **WorkManager** for background tasks. The app displays current weather and maintains a history of queries locally.

---

## 🧩 Features

- View current weather information for a location.
- Light/Dark mode UI with gradient background.
- Toggle between Celsius and Fahrenheit.
- View weather search history (locally saved).
- Fetch data via a weather API using Retrofit.
- Background weather updates using WorkManager.
- Modular architecture following best practices.

---

## 🏗️ Project Structure

### 📁 `api/`
Handles networking and data models:
- `WeatherAPI.kt`: Retrofit interface defining API endpoints.
- `RetrofitInstance.kt`: Singleton for Retrofit setup.
- `Constants.kt`: Base URL, API key, etc.
- `WeatherModel.kt`, `ForecastModel.kt`, `Location.kt`, `Condition.kt`, `Current.kt`: Data classes modeling the API response.
- `NetworkResponse.kt`: Wrapper for managing API success/failure responses.

---

### 📁 `data/`
Room database setup:
- `AppDatabase.kt`: Defines the Room database.
- `WeatherDao.kt`: Interface for database operations (insert, fetch, delete).
- `WeatherEntity.kt`: Represents a weather record stored in the DB.
- `DatabaseModule.kt`: Provides Room-related dependencies (likely using Hilt/DI).

---

### 📁 `ui.theme/`
Custom Jetpack Compose theming:
- `Theme.kt`: Defines `WeatherAppTheme`, toggles dark/light modes.
- `Color.kt`: Holds color definitions.
- `Type.kt`: Typography styles.

---

### 📁 `work/`
Handles background tasks:
- `WeatherWorker.kt`: A `Worker` that fetches and stores weather data periodically using WorkManager.

---

### 📄 `MainActivity.kt`
- The app's main entry point.
- Hosts the main UI using `Jetpack Compose`.
- Manages dark mode toggle and unit switching.
- Launches `HistoryActivity` (and previously `SettingsActivity`, now removed).

---

### 📄 `HistoryActivity.kt`
- Displays previously searched weather data from the local Room database.

---

### 📄 `SettingsActivity.kt` *(Deprecated / To Be Removed)*
- Originally designed to host app settings (theme, units).
- Can be safely deleted if no longer needed.

---

## 🚀 Getting Started

### ✅ Prerequisites
- Android Studio Bumblebee or higher
- Kotlin 1.7+
- Gradle configured with:
  - Jetpack Compose
  - Retrofit
  - Room
  - WorkManager

### 🔧 Setup
1. Clone the repository.
2. Replace the API key in `Constants.kt`:
   ```kotlin
   const val API_KEY = "addbbfce35204e2495b160613250105"
