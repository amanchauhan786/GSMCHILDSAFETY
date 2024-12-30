# GPS Tracking and Emergency Alert System

## Overview
This project involves the analysis of synthetic GPS tracking data simulating a child's movement, along with an emergency alert system integrated into a GitHub repository. The dataset includes location coordinates, timestamps, battery levels, and location types, which can be utilized for movement pattern analysis, anomaly detection, and prediction of the next location.

### Features:
1. **Movement Pattern Analysis**: Identify hourly statistics and location clusters.
2. **Anomaly Detection**: Detect unusual movements using Isolation Forest.
3. **Movement Prediction**: Predict the next location using simple extrapolation.
4. **Emergency Alert System**: A button for triggering emergency alerts.

---

## Requirements
### Python Libraries
- pandas
- numpy
- matplotlib
- seaborn
- sklearn

### Dataset
- Latitude, longitude, timestamp, battery level, and location type data.

---

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repository.git
   ```

2. Navigate to the project directory:
   ```bash
   cd your-repository
   ```

3. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```

---

## Usage
### 1. Generate Synthetic Data
Run the script to generate synthetic GPS tracking data:
```bash
python generate_data.py
```

### 2. Analyze Movement Patterns
Analyze the movement patterns and visualize clusters:
```bash
python analyze_patterns.py
```

### 3. Detect Anomalies
Detect anomalous movements in the dataset:
```bash
python detect_anomalies.py
```

### 4. Predict Next Location
Predict the next location based on historical data:
```bash
python predict_location.py
```

### 5. Emergency Alert System
Click the **Emergency Alert Button** integrated into the web interface to trigger an emergency response. This button is linked to an alert system to notify pre-configured contacts.

---

## Project Structure
```
project-directory/
|
|-- data/                # Contains the synthetic dataset
|-- notebooks/           # Jupyter notebooks for detailed analysis
|-- scripts/             # Python scripts for analysis
|-- emergency_alert/     # Emergency alert system scripts
|-- README.md            # Project documentation
```

---

## Visualizations
### 1. **Movement Clusters**
Clusters are identified using the KMeans algorithm to group locations into meaningful patterns.

### 2. **Speed Distribution**
Distribution of speed data to identify abnormal behaviors.

### 3. **Anomalous Movements**
Scatterplot highlighting unusual GPS points.

---

## Contributions
Feel free to contribute by creating a pull request. Ensure your changes are well-documented.

---

## License
This project is licensed under the MIT License.

---

## Contact
For any issues or questions, please reach out via the repository's Issues section.

