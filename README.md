# Child Safety and Geofencing System

This project is designed to ensure child safety by integrating geofencing alerts, battery monitoring, emergency triggers, and a home automation feature. It also includes functionalities inspired by GitHub for code and repository management, providing a versatile platform for development and child safety.

---

## Features

### 1. **Geofencing Alerts**
- **Dynamic Geofencing**: Predefined geofences for locations such as `home`, `school`, `park`, and `relative_house`.
- **Location Monitoring**: Alerts generated when the child is outside all geofenced areas.
- **Battery Monitoring**: Notifications for low battery levels when inside or outside a geofenced area.
- **Custom Radius**: Adjustable radius for geofencing to suit specific needs.

### 2. **Emergency Switch**
- **Manual Trigger**: An emergency button to send immediate alerts.
- **Priority Alerting**: Overrides all other checks to prioritize emergency actions.

### 3. **Interactive Input System**
- **Widget-Based Input**: Users can input latitude, longitude, and battery level using interactive widgets.
- **Real-Time Feedback**: Instant alerts displayed based on the inputs provided.

### 4. **Test Cases**
#### Test Case 1: Inside a Geofence (`home`)
- **Input**: Latitude: `37.7749`, Longitude: `-122.4194`, Battery Level: `85%`
- **Expected Output**: `[timestamp] Info: Child is safely within 'home'. Battery level: 85%`

#### Test Case 2: Outside All Geofences
- **Input**: Latitude: `37.8000`, Longitude: `-122.5000`, Battery Level: `50%`
- **Expected Output**: `[timestamp] ALERT: Child is outside all designated geofences (Unknown Location).`

#### Test Case 3: Inside a Geofence (`park`) with Low Battery
- **Input**: Latitude: `37.7683`, Longitude: `-122.4825`, Battery Level: `18%`
- **Expected Output**: `[timestamp] ALERT: Battery level is low (18%). Currently at park.`

#### Test Case 4: Inside a Geofence (`school`) with Normal Battery
- **Input**: Latitude: `37.7809`, Longitude: `-122.4278`, Battery Level: `70%`
- **Expected Output**: `[timestamp] Info: Child is safely within 'school'. Battery level: 70%`

### 5. **Home Automation for Child Safety**
- **Smart Home Integration**: Automatically unlock doors or activate cameras when alerts are triggered.
- **Energy Saving**: Adjust lighting or temperature when the child is detected within a geofence.

### 6. **GitHub Clone Features**
- **Repository Management**: Create, read, update, and delete repositories directly from the interface.
- **Version Control**: Commit and track changes with detailed logs.
- **Collaboration**: Share repositories and manage access permissions.
- **Interactive Code Viewer**: Preview and edit code files within the platform.

### 7. **Low-Latency Performance**
- **Optimized Algorithms**: Geofence checks and alerts are processed efficiently to reduce delay.
- **Multi-Device Support**: Compatible with desktop, mobile, and IoT devices.

---

## How to Use

### Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/username/child-safety-geofence.git
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the application:
   ```bash
   python app.py
   ```

### Usage
- Enter latitude, longitude, and battery level via widgets.
- Click "Check Alert" to verify geofence and battery status.
- Use "Activate Emergency Switch" for immediate emergency alerts.

---

## Technologies Used
- **Python**: Core programming language for backend logic.
- **Geopy**: Used for geofence distance calculations.
- **IPyWidgets**: Interactive input and emergency button.
- **Pandas**: Data analysis and processing.
- **GitHub API**: Integrated for repository management features.
- **IoT**: Home automation triggered by alerts.

---

## Contributing
1. Fork the repository.
2. Create a feature branch:
   ```bash
   git checkout -b feature-name
   ```
3. Commit changes:
   ```bash
   git commit -m "Added new feature"
   ```
4. Push to the branch:
   ```bash
   git push origin feature-name
   ```
5. Open a Pull Request.

---

## License
This project is licensed under the MIT License. See `LICENSE` for more details.

---


