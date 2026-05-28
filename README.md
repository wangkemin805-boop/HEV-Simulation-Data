# HEV-Simulation-Data

Heavy Duty Vehicle (HDV) Simulation Data Repository - Focused on Fuel Cell Powered Trucks

## Overview

This repository contains comprehensive data models, parameters, and simulation code for heavy duty vehicles powered by fuel cell technology. It provides:

- **Fuel Cell System Parameters**: Complete specifications for PEM fuel cell stacks
- **Truck Models Database**: Detailed specifications for fuel cell powered trucks (Class 6 and Class 8)
- **Simulation Framework**: Python-based vehicle dynamics and powertrain simulation

## Repository Structure

```
HEV-Simulation-Data/
├── fuel_cell/
│   └── fuel_cell_model_parameters.json    # PEM fuel cell stack specifications
├── truck_database/
│   └── truck_models.json                   # Truck models and specifications
├── simulation/
│   └── vehicle_simulation_model.py         # Vehicle dynamics simulation
└── README.md                               # This file
```

## Fuel Cell System Parameters

Located in `fuel_cell/fuel_cell_model_parameters.json`

### Key Specifications
- **Stack Type**: Proton Exchange Membrane (PEM)
- **Rated Power**: 150 kW
- **Peak Power**: 170 kW
- **Efficiency**: 55-60%
- **Operating Temperature**: 50-90°C
- **Operating Pressure**: 100-350 kPa

### Hydrogen Storage
- **Capacity**: 40 kg
- **Pressure**: 700 bar
- **Estimated Range**: 500 km
- **Tank Material**: Carbon fiber reinforced composite

## Truck Models

Located in `truck_database/truck_models.json`

### Available Models

#### 1. Class 8 Heavy Duty Truck (HDV-FC-001)
- **GVWR**: 36,288 kg (80,000 lbs)
- **Fuel Cell Power**: 150 kW
- **Battery**: 70 kWh Li-ion
- **Motor Power**: 170 kW
- **Max Speed**: 120 km/h
- **Gradeability**: 25%
- **Range**: 500 km

#### 2. Class 6 Medium Duty Truck (HDV-FC-002)
- **GVWR**: 15,000 kg (33,000 lbs)
- **Fuel Cell Power**: 100 kW
- **Battery**: 50 kWh Li-ion
- **Motor Power**: 120 kW
- **Max Speed**: 110 km/h
- **Gradeability**: 20%
- **Range**: 450 km

## Simulation Model

Located in `simulation/vehicle_simulation_model.py`

### Features
- **Fuel Cell Dynamics**: Models efficiency curves, temperature management
- **Battery Management**: SOC tracking, charge/discharge control
- **Vehicle Dynamics**: Driving resistance, acceleration, grade handling
- **Hydrogen Consumption**: Real-time H2 flow calculation

### Key Classes
- `FuelCellVehicleSimulator`: Main simulation engine
- `VehicleState`: Tracks complete vehicle status
- `FuelCellState`: Manages fuel cell operation
- `BatteryState`: Manages battery status

### Simulation Capabilities
- Driving resistance calculation (rolling resistance, aerodynamic drag, grade resistance)
- Power demand estimation
- Fuel cell efficiency modeling based on load
- Battery charge/discharge management
- Hydrogen consumption tracking
- Thermal management simulation

## Usage Example

```python
from vehicle_simulation_model import FuelCellVehicleSimulator, VehicleState, FuelCellState, BatteryState

# Initialize simulator
simulator = FuelCellVehicleSimulator(
    'truck_models.json',
    'fuel_cell_model_parameters.json'
)

# Create initial vehicle state
initial_state = VehicleState(
    speed=0.0,
    acceleration=0.5,  # m/s^2
    position=0.0,
    grade=0.0,
    wind_speed=0.0,
    fuel_cell=FuelCellState(0, 0, 0, 25, 0, 0),
    battery=BatteryState(80, 0, 25, 400),
    hydrogen_remaining=40
)

# Run simulation step
next_state = simulator.step(initial_state)
```

## Performance Metrics

### Efficiency Characteristics
- **Well-to-Wheel**: 45-48%
- **Powertrain**: 85-87%
- **Thermal**: 60%

### Emissions
- **Direct Tailpipe**: Zero (water vapor only)
- **CO2 Equivalent**: Depends on hydrogen production method
  - Green hydrogen: ~0 g CO2/km
  - Gray hydrogen: ~10-15 g CO2/km

## Data Files Format

All data files are in JSON format for easy parsing and integration with various simulation tools.

### Fuel Cell Parameters JSON Structure
```json
{
  "fuel_cell_stack": {...},
  "performance_parameters": {...},
  "operating_conditions": {...},
  "electrical_characteristics": {...},
  "hydrogen_storage": {...},
  "thermal_management": {...},
  "durability_and_life": {...}
}
```

### Truck Models JSON Structure
```json
{
  "truck_fleet": [
    {
      "model_id": "HDV-FC-001",
      "name": "...",
      "specifications": {...},
      "powertrain": {...},
      "performance": {...}
    }
  ]
}
```

## Contributing

To contribute improvements or additional truck models:

1. Maintain consistency with the existing JSON structure
2. Include complete specifications for new models
3. Update simulation code to support new parameters
4. Document any new features in the README

## References

- SAE J2030: Fuel Cell Vehicle Terminology
- ISO 14687: Hydrogen Fuel Quality
- Heavy Duty Vehicle Fuel Cell Technology Development Standards

## License

This simulation data repository is created for educational and research purposes.

---

**Last Updated**: 2026-05-28
**Repository Owner**: wangkemin805-boop
