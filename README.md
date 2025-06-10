Multi Energy Hub Model

project/
│
├── objects/
│   ├── __init__.py
│   ├── grid_user.py           # Contains the GridUser class
│   ├── electrical_grid.py     # Contains the ElectricalGrid class
│   ├── storage.py             # Contains the SharedEnergyStorage class
│   ├── conversion.py          # Contains the ConversionUnit class
│   └── sink_source.py         # Contains the SinkSource class
│
└── main.py                    # Entry point: loads data, runs the solver, and triggers visualization



------------------------------------------------------------

Overview:
-----------
This project implements an energy hub model designed to simulate and manage energy flows across an electrical grid. It integrates multiple components including grid users, electrical grids, shared energy storage, conversion units, and sink/source management to balance supply and demand in real time.

Key Components:
------------------
1. Grid Users:
   - Represent individual energy consumers or generators with unique demand and curtailment characteristics.
2. Electrical Grid:
   - Contains grid constraints, peak capacity, and pricing data that drive the energy balancing operations.
3. Shared Energy Storage:
   - Manages energy storage operations including charging, discharging, and state-of-charge (SOC) balancing.
4. Conversion Units:
   - Convert surplus electricity into other energy forms (or vice versa) to meet grid flexibility requirements.
5. Sink/Source:
   - Handles energy surplus or deficits that cannot be absorbed or supplied directly by storage or conversion units.

Project Structure:
---------------------
- Main Solver (runmodelsolver.py):
  - Loads input data (CSV files) for grid users, grid profiles, shared storage, and conversion units.
  - Executes the solver over a defined number of time steps.
  - Implements flexibility handling (storage management, conversion, and curtailment).
  - Outputs simulation results to a CSV file and provides visualization functions.

- Objects Module (Objects.py):
  - Defines classes for grid users, electrical grids, shared energy storage, conversion units, and sink/source objects.

- Visualization Module (vizualizeoutput.py):
  - Contains functions to visualize grid load profiles and storage behavior based on the output CSV.

- Data Files:
  - CSV files serve as the data sources:
    * Grid user data and load profiles.
    * Electrical grid constraints and electricity price profiles.
    * Shared energy storage parameters.
    * Conversion unit parameters.
    * Output CSV for simulation results.

Inputs:
--------
The model reads several CSV files that define:
- Grid Users: Demand profiles and curtailment settings.
- Electrical Grid: Constraints (supply, demand) and pricing over time.
- Shared Energy Storage: Capacity, charging/discharging limits, and SOC boundaries.
- Conversion Units: Input/output energy conversion parameters and capacity limits.
- Sink/Source: Parameters to manage excess or deficit energy flows.

Outputs:
---------
The simulation produces a CSV file containing:
- Time step identifier.
- Total and adjusted load.
- Supply and demand constraints.
- Available capacity on both supply and demand sides.
- Details of storage and conversion mutations.
- Curtailment amounts and associated costs.
- Electricity price and activity status of storage units.

How to Run:
-------------
1. Install Dependencies:
   - Ensure Python 3 is installed.
   - Install required packages (e.g., pandas, matplotlib) using pip:
       pip install pandas matplotlib

2. Prepare Data Files:
   - Place the CSV data files in the corresponding directories as referenced in the code:
       * Objectdata/GridUserdata/objectinfo/GridUser.csv
       * Objectdata/GridUserdata/Loadprofiles
       * Objectdata/GridUserdata/objectinfo/ElectricalGrid.csv
       * Objectdata/GridUserdata/objectinfo/SharedEnergyStorage.csv
       * Objectdata/GridUserdata/objectinfo/ConversionUnit.csv

3. Run the Solver:
   - Execute the main solver script. For example:
       python solver.py
   - This script loads the data, runs the simulation for a specified number of time steps, saves the results to a CSV file, and calls visualization functions.

4. View Results:
   - Open the output CSV file (e.g., Objectdata/GridUserdata/Output files/baselinerundatanocurtailwithstorage.csv) to inspect simulation results.
   - The visualization functions generate plots that provide insights into grid load profiles and storage behavior.

Formulas and Operations:
---------------------------
The model utilizes a range of formulas to perform operations such as:
- Retrieving electricity prices and calculating grid load.
- Checking grid constraints and available capacity.
- Managing storage (charging/discharging) based on load conditions.
- Curtailing loads based on predefined cost and cap settings.
- Converting energy between mediums to address surplus or deficits.

For further details on the formulas and calculations, refer to the project documentation.

License:
---------
MIT License

Acknowledgments:
-----------------
Credit any collaborators, libraries, or resources that contributed to the development of this project.
