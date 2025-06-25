# Austrian Renewable Energy and District Heating Model

This repository contains the OSeMOSYS-based national-local energy system model for Austria. The model optimizes the full energy system under 100% renewable energy constraints and includes case studies of district heating systems in Neusiedl am See and Oberwart.

---

## 📘 Table of Contents

- [Overview](#overview)  
- [Case Studies](#case-studies)  
- [Data Sources](#data-sources)  
- [Installation](#installation)  
- [Usage](#usage)  
- [Project Structure](#project-structure)  
- [Contributing](#contributing)  
- [License](#license)  
- [Contact](#contact)

---

## 📌 Overview

This OSeMOSYS model minimizes the cost of supplying all Austrian energy demands—electricity, district heat, industrial heat, and transport—using only renewable sources like wind, solar, hydropower, and biomass. It includes:

- Hourly-resolution modeling (8760 time slices)  
- Energy storage (thermal, batteries, hydro, hydrogen)  
- Cost-optimal technology selection  
- Local district heating integrated within a national context

The model can simulate and compare scenarios with different energy mixes, infrastructure configurations, and local vs. national optimization trade-offs.

---

## 🏙️ Case Studies

Two representative Austrian district heating systems are modeled:

### Neusiedl am See
- 2.6 MW wood boiler  
- 2 MW heat pumps  
- Wind-powered + grid access  

### Oberwart
- 5.8 MW wood boiler  
- 0.35 MW electric resistance heater  
- Small-scale urban system  

Each system is tested under:
1. Current prices and fixed equipment  
2. Fully renewable Austrian supply (fixed equipment)  
3. Fully renewable system with optimized local technology mix

---

## 📊 Data Sources

- Hourly demand & renewables: ENTSO-E, Energie Burgenland, GeoSphere Austria  
- Biomass potential: Austria Biomass Association (2024)  
- Technology costs: IRENA (2023), Danish Energy Agency (2020), Fraunhofer ISE (2024)  
- Useful energy demand: Statistics Austria (2024)  
- Case study operational data: Energie Burgenland

Full dataset references are provided in the accompanying paper and `data/` directory.

---

## ⚙️ Installation

**Clone the repository:**
```bash
git clone https://github.com/ShravanKumar23/OSeMOSYS-Austrian-Energy-Model.git
cd OSeMOSYS-Austrian-Energy-Model
```

**Create a conda environment:**
```bash
conda env create -f OSeMOSYS.yml
conda activate osemosys
```

This environment file ensures compatibility with dependencies used across OSeMOSYS models. The process to run the model is exactly the same.

---


## 📥 Input Data

The input data is stored in an Excel file:

```
./model/Input_Data/AT_2019_8jun.xlsx
```

This file contains all the necessary parameters to run the optimization model. The parameter structure follows the conventions of the original OSeMOSYS-GNU 2 framework.

---

## 🧠 Model File

The core model script is an enhanced version of OSeMOSYS-PuLP with improved performance for matrix generation and post-processing. This version aligns with the short version of OSeMOSYS-GNU and reflects ongoing improvements in model speed and efficiency.

- Model script:  
  ```
  ./model/OSeMOSYS.py/
  ```

- Utilities and helper functions:  
  ```
  ./model/utils/
  ```

---

## ▶️ Run the Model

It is recommended to create a fresh Python environment and install required libraries such as `pulp`.

**Create and activate environment:**
```bash
conda create --name pulp python=3.8
conda activate pulp
```

**Run the model:**
```bash
python OSeMOSYS.py -i AT_2019_8jun.xlsx -s cplex -o csv
```

Replace `cplex` with `gurobi` or `cbc` depending on your installed solver.

The results will be saved as:
```
./Output_Data/AT_2019_8jun_results.csv
```

---

## 🧱 Project Structure

```
├── data/                       # Input datasets (demand, cost, weather)
├── configs/                    # Model configuration YAMLs
├── src/                        # Model and plotting scripts
├── results/                    # Output CSVs from model runs
├── figures/                    # Plots and result visualizations
├── OSeMOSYS.yml                # Conda environment file
├── OSeMOSYS.py                # Main execution script
├── README.md
└── LICENSE
```

---

## 🤝 Contributing

Contributions are welcome! To propose changes or additions:

1. Fork the repository  
2. Create a branch: `git checkout -b feature/your-feature`  
3. Commit your changes  
4. Push to your fork  
5. Submit a Pull Request

---

## 📝 License

This project is licensed under the [MIT License](LICENSE).

---

## 📬 Contact


Shravan Kumar Pinayur Kannan  
GitHub: [@ShravanKumar23](https://github.com/ShravanKumar23)  
Email: shravankannan.p@gmail.com

---

> 📄 For details on the model methodology, assumptions, and results, see:  
> *“Optimizing District Heating in a Fully Renewable Energy System: An Austrian Case Study” (2025)*

---


