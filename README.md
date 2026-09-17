# Smart India Hackathon Workshop

## Date:

17 09 2026

## Register Number:

212224040049

## Name:

Bhuvaneshwaran TU

# Problem Title

**SIH 1710: Enhancing Navigation for Railway Station Facilities and Locations**

## Problem Description

Railway stations are large and complex environments containing platforms, ticket counters, restrooms, food courts, waiting halls, lifts, escalators and other facilities. Passengers who are unfamiliar with a station may spend considerable time searching for their destination, particularly when the station has multiple floors, entrances or platforms.

The problem becomes more challenging when a route is temporarily unavailable because of maintenance, crowding, platform changes or facility closures. Passengers with accessibility requirements may also need routes that avoid stairs and prioritize lifts, ramps and accessible pathways.

The proposed solution is a **context-aware indoor railway station navigation system** that does more than display a static map. It combines station maps, facility information, route preferences, accessibility requirements and real-time station updates to generate an appropriate route for each passenger.

---

# 1. Idea

### RailGuide – Context-Aware Railway Station Navigation

**RailGuide** is a multi-platform indoor navigation system designed to help passengers find facilities and reach platforms efficiently inside railway stations.

Instead of providing the same route to every passenger, the system considers the passenger's **current location, destination and navigation preferences** before generating a route.

For example:

* A normal passenger can receive the shortest available route.
* A wheelchair user can receive a route avoiding stairs and prioritizing lifts and ramps.
* A visually impaired passenger can enable voice-guided navigation.
* If a corridor or facility becomes unavailable, the system can recalculate the route.
* If a destination such as a restroom or food court is crowded or temporarily closed, the system can display an alternative.

### Core Concept

**Passenger Input → Context Analysis → Dynamic Route Calculation → Step-by-Step Guidance**

The system can be accessed through a mobile application and railway-station kiosks, allowing passengers to use the service even when they do not have the application installed.

---

# 2. Proposed Solution / Architecture Diagram

## Proposed Solution

RailGuide consists of multiple layers that work together to provide context-aware indoor navigation.

### 1. User Layer

Passengers interact with the system through:

* Mobile application
* Digital railway-station kiosks
* Accessibility-focused interface

The passenger can search for a destination such as:

* Platform
* Ticket counter
* Restroom
* Food court
* Waiting hall
* Lift
* Escalator
* Exit
* Help desk

The passenger can also select route preferences such as:

* Shortest route
* Accessible route
* Avoid stairs
* Avoid crowded areas

### 2. Application Layer

The application layer handles passenger-facing functionality:

* Destination search
* Facility discovery
* Route preference selection
* Indoor map visualization
* Step-by-step navigation
* Voice guidance
* Crowd and facility alerts

### 3. Core Services Layer

The core layer processes navigation requests.

#### Station Graph Engine

The station is represented as a graph consisting of:

* Nodes → platforms, entrances, facilities, junctions and floors
* Edges → walkable paths between nodes

This allows the system to calculate routes through the station.

#### Dynamic Route Calculator

The route calculator considers:

* Distance
* Current route availability
* Facility closures
* Crowd conditions
* Passenger preferences

It can recalculate a route whenever relevant station information changes.

#### Accessibility Route Filter

The system can remove unsuitable paths for passengers who select accessibility requirements.

For example:

**Wheelchair mode → avoid stairs → prioritize lifts and ramps → calculate accessible route**

#### Facility Status Manager

Stores and updates the operational status of facilities such as:

* Open
* Closed
* Under maintenance
* Temporarily unavailable

#### Notification Service

Provides important passenger notifications such as:

* Platform changes
* Route closures
* Facility closures
* Navigation warnings

### 4. Data & Integration Layer

The system maintains:

* Station layout data
* Facility and landmark information
* Navigation paths
* Live station updates
* Platform information
* Railway service information

An administrative interface can be used by authorized railway staff to update station information.

### Architecture Flow

```text
Passenger / Kiosk
       │
       ▼
Destination Search + Preferences
       │
       ▼
Navigation Application
       │
       ▼
Context & Route Processing
       │
 ┌─────┼───────────────┐
 ▼     ▼               ▼
Map   Facility      Accessibility
Data  Status        Requirements
 │     │               │
 └─────┼───────────────┘
       ▼
Dynamic Route Calculator
       │
       ▼
Recommended Route
       │
       ▼
Map + Step-by-Step + Voice Guidance
```

### Architecture Diagram

The complete architecture diagram is provided in the repository as:

`docs/architecture.png`

It represents the User Layer, Application Layer, Core Services Layer and Data & Integration Layer.

---

# 3. Use Cases

## Main Use Cases

### Use Case 1 – Find a Facility

A passenger searches for a facility such as a restroom, food court, ticket counter or waiting hall.

The system identifies the destination and provides directions from the passenger's current location.

### Use Case 2 – Navigate to a Platform

A passenger selects a platform as the destination.

The system calculates a route through the station and displays step-by-step instructions.

### Use Case 3 – Accessibility Navigation

A passenger selects an accessibility preference.

The system avoids unsuitable paths such as stairs and prioritizes accessible infrastructure such as:

* Lifts
* Ramps
* Accessible entrances
* Wheelchair-friendly pathways

### Use Case 4 – Voice Navigation

A visually impaired passenger enables voice guidance.

The system provides spoken instructions such as:

* Move forward
* Turn left
* Take the lift
* Continue towards Platform 3

### Use Case 5 – Real-Time Route Recalculation

If a route becomes unavailable because of maintenance, crowding or a temporary closure, the system identifies the affected path and generates an alternative route.

### Use Case 6 – Facility Status

Passengers can check whether a facility is currently available.

For example:

```text
Food Court
Status: Open

Restroom
Status: Temporarily Closed

Lift
Status: Available
```

### Use Case 7 – Digital Kiosk Navigation

Passengers without the mobile application can use a touch-screen kiosk.

They select their destination and receive:

* Station map
* Route
* Estimated walking distance
* Directional instructions
* Accessibility options

### Use Case 8 – Railway Staff Updates

Authorized railway staff can update:

* Facility status
* Station layout
* Temporary closures
* Platform information
* Navigation restrictions

These updates are reflected in the navigation system.

---

## Use Case Diagram

```text
                         ┌──────────────────────────────┐
                         │   RAILGUIDE NAVIGATION       │
                         │           SYSTEM             │
                         │                              │
Passenger ──────────────►│ Search Facility             │
   │                     │                              │
   ├────────────────────►│ Get Directions              │
   │                     │                              │
   ├────────────────────►│ Select Route Preference     │
   │                     │                              │
   ├────────────────────►│ Enable Voice Guidance       │
   │                     │                              │
   ├────────────────────►│ View Real-Time Updates      │
   │                     │                              │
   └────────────────────►│ View Accessibility Options  │
                         │                              │
                         └──────────────────────────────┘
                              ▲          ▲
                              │          │
                  ┌───────────┘          └────────────┐
                  │                                    │
          Railway Staff                         Railway Data
                  │                                    │
                  ▼                                    ▼
        Update Station Information             Platform Information
        Update Facility Status                Service Updates
        Manage Closures                       Station Data
```

The formal diagram is also provided as:

`docs/use-case-diagram.png`

---

# 4. Technology Stack

## Frontend

* React.js
* HTML5
* CSS3
* JavaScript
* Responsive UI

## Mobile / Multi-platform

* React Native

## Backend

* Node.js
* Express.js
* REST APIs

## Database

* PostgreSQL
* PostGIS for spatial/location-related data

## Maps & Navigation

* Mapbox / Three.js
* GeoJSON
* Graph-based indoor navigation model

## Real-Time Services

* WebSocket / Firebase
* Real-time facility and station-status updates

## Voice Accessibility

* Web Speech API / Text-to-Speech

## Cloud & Deployment

* Firebase / AWS
* Cloud-based API hosting

## Development & Version Control

* Git
* GitHub
* Visual Studio Code

---

# 5. Dependencies

The proposed implementation may use the following dependencies:

```text
react
react-dom
react-native
express
axios
pg
postgis
socket.io
firebase
mapbox-gl
three
@react-three/fiber
dotenv
cors
```

### Functional Dependencies

The system requires:

* Station layout and pathway data
* Facility location data
* Platform information
* Facility availability information
* Navigation graph
* Real-time station updates
* Railway service integration where APIs are available

### Hardware Dependencies

For a complete deployment:

* Passenger smartphone
* Touch-screen digital kiosk
* Station display/network infrastructure
* Server/cloud infrastructure

---

# 6. Key Advantages

### Context-Aware Navigation

The route is generated according to passenger requirements instead of providing only a fixed map.

### Accessibility First

Passengers can specifically request routes that avoid stairs and prioritize accessible infrastructure.

### Dynamic Routing

Routes can be recalculated when station conditions change.

### Multi-Platform Access

The same navigation service can be accessed through mobile devices and station kiosks.

### Facility Awareness

Passengers can identify the location and current status of important facilities.

### Reduced Passenger Confusion

Clear visual, textual and voice instructions help passengers reach their destination with fewer navigation difficulties.

### Scalable Station Model

The station can be represented as a graph, allowing the same navigation engine to be adapted to different railway stations by changing the station map and facility data.

---

# 7. Example User Flow

```text
Passenger enters station
        ↓
Opens RailGuide / Kiosk
        ↓
Selects "Platform 5"
        ↓
Selects "Accessible Route"
        ↓
System checks station graph
        ↓
Checks lifts, ramps and blocked paths
        ↓
Dynamic Route Calculator
        ↓
Accessible route generated
        ↓
Passenger receives:
• Map
• Distance
• Step-by-step directions
• Voice guidance
        ↓
Station update occurs
        ↓
System detects affected route
        ↓
Alternative route generated
        ↓
Passenger receives updated directions
```

---

# 8. Expected Outcome

RailGuide aims to provide passengers with a simple and accessible way to navigate complex railway stations.

The system combines **indoor mapping, graph-based route calculation, accessibility preferences, facility status and real-time updates** into one navigation platform.

This can help passengers locate facilities faster, reduce unnecessary movement inside crowded stations, improve accessibility and provide clearer navigation for passengers unfamiliar with the station environment.

---

# 9. Conclusion

RailGuide transforms railway-station navigation from a static map-based experience into a **dynamic, context-aware navigation service**.

By combining passenger preferences with station layout and changing station conditions, the system can generate more appropriate routes for different passenger requirements while supporting mobile users, kiosk users and accessibility-focused navigation.
