# GPS Tracking and Emergency Alert System

## Overview
This system is designed to ensure child safety by leveraging GPS tracking, geofencing, and emergency alert mechanisms. The features include real-time location monitoring, battery level alerts, and an emergency switch for immediate action. Additionally, it integrates a home automation feature for enhanced child safety.

## Features
1. **Geofencing**:
   - Define multiple geofenced locations (e.g., home, school, park, relative's house).
   - Alerts when a child exits a geofenced area.

2. **Battery Level Monitoring**:
   - Tracks the battery level of the child's device.
   - Sends alerts if the battery level falls below a predefined threshold (default: 20%).

3. **Emergency Switch**:
   - Activates an immediate emergency alert when triggered.

4. **Home Automation Integration**:
   - Allows control of smart home devices (e.g., locks, cameras) to enhance child safety.

## How It Works
1. **Real-Time Alerts**:
   - The system checks if the child is within any geofence and monitors battery levels.
   - Alerts are generated based on location and battery conditions.

2. **Emergency Button**:
   - A dedicated button to simulate an emergency situation, overriding normal checks.

3. **User Input**:
   - Latitude, longitude, and battery level inputs are taken via interactive widgets.

4. **Output**:
   - Informational messages or alerts are displayed with timestamps for clarity.

## Test Cases
### Test Case 1: Inside a geofence (home)
**Inputs**:
- Latitude: 37.7749
- Longitude: -122.4194
- Battery Level: 85%

**Expected Output**:
`[timestamp] Info: Child is safely within 'home'. Battery level: 85%.`

### Test Case 2: Outside all geofences
**Inputs**:
- Latitude: 37.8000
- Longitude: -122.5000
- Battery Level: 50%

**Expected Output**:
`[timestamp] ALERT: Child is outside all designated geofences (Unknown Location).`

### Test Case 3: Inside a geofence (park) with low battery
**Inputs**:
- Latitude: 37.7683
- Longitude: -122.4825
- Battery Level: 18%

**Expected Output**:
`[timestamp] ALERT: Battery level is low (18%). Currently at park.`

### Test Case 4: Inside a geofence (school) with normal battery
**Inputs**:
- Latitude: 37.7809
- Longitude: -122.4278
- Battery Level: 70%

**Expected Output**:
`[timestamp] Info: Child is safely within 'school'. Battery level: 70%.`

## Implementation
### Geofencing and Alerts
```python
import pandas as pd
from geopy.distance import geodesic
import datetime
import ipywidgets as widgets
from IPython.display import display

# Define coordinates for multiple geofenced locations
geofences = {
    "home": (37.7749, -122.4194),
    "school": (37.7809, -122.4278),
    "park": (37.7683, -122.4825),
    "relative_house": (37.8044, -122.2711)
}

# Define battery threshold for alerts
battery_threshold = 20  # Battery level (%) below which alert should be triggered

# Emergency switch status
emergency_switch_active = False

# Function to check if a location falls within any geofence
def check_geofence_alert(lat, lon, geofences, radius=0.002):
    """
    Check if a given point (lat, lon) is within any defined geofences.
    Returns (alert_status, location_name) where alert_status is True if outside all geofences,
    and location_name is the geofence name or 'outside_geofences'.
    """
    for location_name, coords in geofences.items():
        distance = geodesic((lat, lon), coords).meters
        if distance <= radius * 1000:
            return False, location_name  # No alert needed, within geofence
    return True, "outside_geofences"  # Alert, outside all geofences

# Function to simulate emergency switch using a button in Google Colab
def on_emergency_button_click(b):
    global emergency_switch_active
    emergency_switch_active = True
    print("[Emergency Alert] Emergency switch activated! Triggering immediate action.")

# Function to generate alerts based on inputs
def generate_alert(latitude, longitude, battery_level):
    global emergency_switch_active  # Declare as global to modify the global variable
    timestamp = datetime.datetime.now()

    # Check geofence status
    alert_status, location_name = check_geofence_alert(latitude, longitude, geofences)

    # If emergency switch is activated, send emergency alert
    if emergency_switch_active:
        alert_message = f"[{timestamp}] EMERGENCY ALERT: Emergency switch activated! Immediate action required!"
        emergency_switch_active = False  # Reset emergency switch after activation
    else:
        # Determine if an alert should be raised
        if alert_status:
            alert_message = f"[{timestamp}] ALERT: Child is outside all designated geofences (Unknown Location)."
        elif battery_level < battery_threshold:
            alert_message = f"[{timestamp}] ALERT: Battery level is low ({battery_level}%). Currently at {location_name}."
        else:
            alert_message = f"[{timestamp}] Info: Child is safely within '{location_name}'. Battery level: {battery_level}%."

    # Display alert message
    print(alert_message)

# Widgets for input
latitude_input = widgets.FloatText(value=37.7749, description='Latitude:')
longitude_input = widgets.FloatText(value=-122.4194, description='Longitude:')
battery_level_input = widgets.FloatSlider(value=50, min=0, max=100, step=1, description='Battery Level:')
submit_button = widgets.Button(description="Check Alert")

# Emergency switch button
emergency_button = widgets.Button(description="Activate Emergency Switch")

# Register button click events
emergency_button.on_click(on_emergency_button_click)

# Function to handle the submit button click
def on_submit_button_click(b):
    latitude = latitude_input.value
    longitude = longitude_input.value
    battery_level = battery_level_input.value
    generate_alert(latitude, longitude, battery_level)

# Register submit button click event
submit_button.on_click(on_submit_button_click)

# Display the widgets
display(latitude_input, longitude_input, battery_level_input, submit_button, emergency_button)
```

## Future Enhancements
1. **Advanced AI Integration**:
   - Use machine learning to predict and prevent unsafe conditions.
2. **Mobile App Integration**:
   - Provide notifications via a mobile application for convenience.
3. **Enhanced Home Automation**:
   - Automate security responses like locking doors or activating cameras during emergencies.

## License
This project is licensed under the MIT License.

