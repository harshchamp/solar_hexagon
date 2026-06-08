# Solar Hexagon - Solar Panel Current Prediction

A comprehensive data analysis and machine learning project for predicting solar panel current output using weather data and sensor telemetry. This project analyzes multi-year solar tracker data to understand panel performance and predict current generation based on environmental conditions.

## Overview

Solar Hexagon is an advanced analytics project that processes and analyzes large-scale solar panel sensor data combined with weather information. The project focuses on predicting panel current output (PanelCurrent_mA) using various sensor metrics, environmental conditions, and temporal features. With over 42+ million sensor records from 2023-2024, this project demonstrates real-world data processing at scale.

## Project Structure

- **Solaranalysis.ipynb** - Main Jupyter notebook containing comprehensive solar data analysis, feature engineering, and prediction modeling

## Dataset Overview

The project combines two years of sensor data from solar tracking systems with weather information:

### Data Sources

- **2024 Solar Tracker Data:** ansasol_tracker_2024.csv (6.76M records)
- **2023 Solar Tracker Data:** ansasol_tracker_2023.csv (36.17M records)
- **Combined Dataset:** 42.93M total records (after deduplication)

### Data Characteristics

- **Time Period:** June 2023 - Current 2024
- **Unique Timestamps:** 42.7M distinct measurements
- **Geographic Coverage:** Solar tracking systems across multiple locations (Latitude/Longitude coordinates)
- **Temporal Resolution:** Hourly measurements with precise timestamps

## Dataset Columns

| Column | Type | Description |
|--------|------|-------------|
| inserted_datetime | String | UTC timestamp of measurement |
| UniqueKey | String | Unique identifier for tracking system |
| DATA | Integer | Data package identifier |
| Longitude | Float | Geographic longitude coordinate |
| Latitude | Float | Geographic latitude coordinate |
| DAS | Integer | Device availability status |
| TAS | Integer | System availability status |
| MbAddress_PUB | Integer | Modbus address identifier |
| PanelVoltage_mV | Integer | Solar panel voltage (millivolts) |
| PanelCurrent_mA | Integer | Solar panel current (milliamps) - **TARGET VARIABLE** |
| Position_a1_rad | Float | Axis 1 position (radians) |
| MotorCurrent_a1_mA | Integer | Motor current for axis 1 (milliamps) |
| TargetAngle_a1_rad | Float | Target angle for axis 1 (radians) |
| StateOfCharge | Integer | Battery state of charge (%) |
| RemainingCapatity_mAh | Integer | Battery remaining capacity (mAh) |
| FullCapatity_mAh | Integer | Battery full capacity (mAh) |
| Voltage_mV | Integer | Battery voltage (millivolts) |
| AvgCurrent_mA | Integer | Average current (milliamps) |
| Current_mA | Integer | Current measurement (milliamps) |
| TempPcb_Kx10 | Integer | PCB temperature (Kelvin × 10) |
| TempBat_Kx10 | Integer | Battery temperature (Kelvin × 10) |
| StateOfHealth | Integer | Battery state of health (%) |
| Alarms1, Alarms2 | Integer | System alarm flags |
| HardwareId, SoftwareId | Integer | System identification |
| MainState, CommissionState | Integer | System state indicators |

## Key Features

### Data Processing
- **Multi-year Integration:** Combines 2023 and 2024 data into unified analysis framework
- **Large-scale Data Handling:** Processes 42M+ records using Pandas and Dask
- **Memory Optimization:** Chunk-based reading for efficient memory management
- **Data Deduplication:** Removes duplicate entries based on timestamps
- **Feature Engineering:** Creates temporal features (Date, Time, UniqueKey_weather)

### Analysis Capabilities
- **Panel Performance Analysis:** Tracks solar panel current output patterns
- **Environmental Impact:** Correlates weather with power generation
- **Temporal Analysis:** Hourly and daily patterns in solar generation
- **System Diagnostics:** Battery health, voltage stability, temperature monitoring
- **Predictive Modeling:** Machine learning for panel current prediction

### Advanced Techniques
- **Dask Integration:** Distributed data processing for large datasets
- **Google Drive Integration:** Cloud storage access for data files
- **Temporal Feature Extraction:** Date, hour, and timestamp-based features
- **Multi-system Aggregation:** Handles data from multiple tracking systems

## Technologies Used

- **Python 3** - Programming language
- **Pandas** - Data manipulation and analysis
- **NumPy** - Numerical computing
- **Dask** - Distributed data processing
- **Google Colab** - Cloud-based development environment
- **Jupyter Notebook** - Interactive analysis environment

## Getting Started

### Prerequisites

- Python 3.x
- Jupyter Notebook or Google Colab
- Required packages: pandas, numpy, dask[dataframe]
- Google Drive access (for data files)

### Installation

1. Clone this repository
2. Install required dependencies:
   ```bash
   pip install pandas numpy dask[dataframe] jupyter
   ```

3. Set up Google Drive connection:
   - Place `ansasol_tracker_2023.csv` and `ansasol_tracker_2024.csv` in Google Drive
   - Path: `/MyDrive/Colab Notebooks/`

### Usage

1. Open in Google Colab or Jupyter Notebook:
   ```bash
   jupyter notebook Solaranalysis.ipynb
   ```

2. Follow the notebook sections:
   - Mount Google Drive for data access
   - Load and process 2024 data
   - Load and process 2023 data
   - Combine datasets
   - Perform feature engineering
   - Execute analysis and predictions

## Analysis Workflow

### 1. Data Loading and Initial Processing
- Loads 2024 solar tracker data from Google Drive
- Uses chunk-based reading (1.05M records per chunk)
- Concatenates chunks into unified DataFrame
- Performs initial data inspection

### 2. Data Quality Checks
- Verifies data types across columns
- Identifies missing values
- Checks for duplicate entries
- Validates geographic coordinates

### 3. Feature Engineering
- Converts datetime strings to pandas datetime objects
- Extracts date and hour features
- Creates unique weather keys (Date-Hour combinations)
- Prepares data for merge with weather information

### 4. Data Integration
- Combines 2023 and 2024 datasets
- Deduplicates based on timestamp
- Removes irrelevant columns (alarm flags, manual controls)
- Standardizes data format across years

### 5. Advanced Processing
- Handles battery metrics and health indicators
- Processes motor and panel positioning data
- Manages multi-system data aggregation
- Optimizes for predictive modeling

## Dataset Statistics

- **2024 Records:** 6,763,707
- **2023 Records:** 36,167,641
- **Combined Records:** 42,931,348
- **After Deduplication:** 42,725,478
- **Unique Timestamps:** 42,725,478
- **Columns (After Processing):** 36

## Key Metrics

### Solar Panel Metrics
- Panel Voltage: Measured in millivolts
- Panel Current: Primary prediction target
- Panel Position: Tracked in radians

### Battery Metrics
- State of Charge: 0-100%
- State of Health: 0-100%
- Temperature: Kelvin × 10
- Voltage and Current: Continuous monitoring

### Environmental Factors
- Geographic coordinates (Latitude/Longitude)
- System availability indicators
- Temperature sensors (PCB and Battery)

## Use Cases

1. **Power Generation Forecasting:** Predict panel output based on weather
2. **System Performance Analysis:** Track efficiency across multiple installations
3. **Battery Management:** Optimize charge cycles and longevity
4. **Maintenance Planning:** Identify underperforming systems
5. **Energy Trading:** Forecast generation for market optimization

## Data Processing Considerations

### Memory Management
- Chunk-based reading for large CSV files
- Dask library for distributed computing
- Selective column loading
- Deduplication for reduced dataset size

### Data Quality
- Handles UTC timestamps
- Validates coordinate ranges
- Monitors sensor accuracy
- Tracks system health indicators

### Scalability
- Designed for multi-terabyte datasets
- Efficient aggregation across time periods
- Parallel processing capabilities
- Cloud-based infrastructure ready

## Notes

- Data is stored in UTC timestamps
- Temperature values are in Kelvin × 10 format (divide by 10 for actual Celsius + 273.15)
- Current measurements in milliamps (mA)
- Voltage measurements in millivolts (mV)
- Position/angle measurements in radians
- Notebook is optimized for Google Colab execution
- Large dataset requires significant RAM (20GB+ recommended)

## Advanced Features

### Dask Integration
- Distributed processing of large CSV files
- Memory-efficient operations
- Parallel computations
- Scalable to larger datasets

### Data Pipeline
1. **Ingestion:** Load from Google Drive
2. **Processing:** Clean and deduplicate
3. **Feature Engineering:** Extract temporal features
4. **Aggregation:** Combine multiple data sources
5. **Preparation:** Format for ML models

## Files in Repository

- `Solaranalysis.ipynb` - Main analysis notebook (263 KB)
- `README.md` - This documentation

## Contributing

Contributions are welcome! Areas for improvement:
- Add weather data integration
- Implement machine learning models
- Add visualization dashboards
- Optimize processing pipeline
- Extend to real-time predictions

## License

This project is open source and available under the MIT License.

## References

- Pandas Documentation: https://pandas.pydata.org/
- Dask Documentation: https://dask.org/
- Solar Panel Technology: Solar tracking and efficiency optimization
- Data Science Best Practices: Large-scale data processing

## Contact

For questions or suggestions, please reach out through GitHub Issues.
