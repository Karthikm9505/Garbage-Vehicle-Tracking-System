# Garbage Vehicle Tracking System (GVTS)

A mini end-to-end tracking system built as a personal project.

## Overview

- **Driver Android App (Kotlin)** – sends live GPS coordinates to Firebase and triggers "truck started" events.
- **Citizen GVTS App (Flutter)** – shows garbage vehicle info and receives push notifications when the truck starts.

## Tech Stack

- **Mobile**:
  - Android (Kotlin, Foreground Service, FusedLocationProvider)
  - Flutter (Dart, Flutter Local Notifications)
- **Cloud**:
  - Firebase Realtime Database
  - Firebase Cloud Messaging (FCM)
  - AWS API Gateway, Lambda, SNS, DynamoDB

## Features

- Driver app:
  - Start/Stop buttons to control foreground tracking service
  - Sends GPS every ~5s to Firebase
  - Calls AWS `/driver/start` once per 12 hours per truck

- Citizen app:
  - Auto-registers device FCM token with AWS `/register`
  - Subscribed to SNS topic and receives "Truck G123 started" push

## Project Structure

```text
gvts/
  driver-android/      # Android Studio project (Driver app)
  gvts-flutter/        # Flutter project (Citizen app)
  docs/                # (optional) screenshots, diagrams
