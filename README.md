# COMPARATIVE ENERGY ANALYSIS PIPELINE ☀️💨⚡

### OVERVIEW 🔎:
This program basically analyze historical energy production (from solar and wind sources) and weather data and expects scenarios labeled as BEST and WORST 
## 🔧 My Contribution

**⚠️ IMPORTANT:** I (Aleynaonrr) developed the **Energy Database Module** for this project. This includes:
- `energy_data.db` - SQLite database design and implementation
- `test_energy_database.py` - Complete database testing and validation
- Database schema, tables, and query optimization
- Data validation and integrity checks

**Other project components were developed by my team members.**

## 🤝 Team Members

This is a **collaborative project** developed by:
- **Aleynaonrr** - Energy Database Development ⭐
- **zeyneptuana22** - Project Contributor
- **zehraa2005** - Project Contributor
- **enessaduman** - Project Contributor
- **busracode** - Project Contributor

---


### What did we deal with and how we handled it?
First we parsed the hourly enegry production data from the EPIAS Transparency Platform for 3 months period. Then , thanks to dear visiual crossing weather data company workers, they dedicated a subscribtion to one of our account and we downloaded the weather data as "solar radiation" and "wind speed".
#### Cleaning and Analysing
1) First we equalize the date format from EPIAS and visualcrossing data. Since one of them was turkish and other one is english resources, the date order was different.
2) We indicated the columns that are carrying numbers in a string form as the type of float64.
3) We converted units such as fahreneit to celcius and mph to m/s. 
4) We structed power equations such as solar_power(parameters as tempurture, solar_Radiation) and wind_power(wind_speed^3)(you can also the facinating spikey effect of cubic wind_speed existance in the equation)
5) We calculated best and worst scalers so that we can estimate the whole country's production based on the couple of cities. (real_production/(Σ(power_equation_best_week*city's_weight_on_total)))
6) We also designed a graph_shaper functions so that we can handle both unlikely discrete values and Watt to MegaWatt conversions.

## Requirements 🔧⚙️

### 1️⃣ Node.js 📊:
Node.js provides us the JavaScript runtime environment that we need for ReactJS. Here is the [download link](https://nodejs.org/en/download "Node.js download page"). You can choose the proper operating system for your own pc and download the installer.
Make sure the installation is completed, we will run it from the terminal.

### 2️⃣ Libraries 📚: 
We need a bunch of libraries to run the program. You can use your IDE's terminal:
````commandline
cd Backend
py -m pip install -r requirements.txt
````

### 3️⃣ Installing the Node Modules
1) Open a new local terminal on your IDE
2) Run this command lines:
````commandline
    cd frontend
    npm install
````
⚠️⚠️ Installation of node modules might take even 1-2 minutes ⚠️⚠️

### 4️⃣ Preparing the Backend
1) Get into the directory. Open a terminal and run this:
````commandline
cd Backend
````
2) First you have to scrap the web for energy data:
````commandline
py energy_production_scrap.py
````
PS: Playwright headless has been set as true so you will not see any visual action.
3) Now for the cleaning and analysing part we use this command:
````commandline
py data_cleaning_analysing.py
````
4) To avoid from redundant calculations, we fill a database using analyzed data.
````commandline
py energy_database.py
````

### 5️⃣ Starting the Server
Here the command line to start the server:
````commandline
py server.py
````

### RUN THE PROGRAM
Here we run the reactjs and open the browser. Open a new terminal an write this:
````commandline
cd frontend
npm start
````

### File Structure 📁:
````
Proje3WEATHER_ENERGY/
├── Backend/
│   ├── .env                           # Environment variables (Credentials)
│   ├── complete_solar_records.json    # Output: Processed solar data
│   ├── complete_wind_records.json     # Output: Processed wind data
│   ├── data_cleaning_analysing.py     # Main energy analysis module
│   ├── energy_data.json               # Raw scraped energy data
│   ├── energy_data_v2 [2].db          # SQLite database for storage
│   ├── energy_database.py             # Database management scripts
│   ├── energy_production_scrap.py     # Playwright/Scrapy automation
│   ├── README.md                      # Backend documentation
│   ├── requirements.txt               # Python dependencies
│   └── server.py                      # Backend API server
├── frontend/
│   ├── node_modules/                  # Project dependencies (Library root)
│   ├── public/                        # Static assets
│   ├── src/                           # Frontend source code (React/Vue/etc.)
│   ├── .gitignore                     # Git ignore rules
│   ├── package.json                   # Frontend metadata and scripts
│   ├── package-lock.json              # Dependency lock file
│   └── README.md                      # Frontend documentation
└── WEATHER_DATA/                      # Directory containing raw weather JSONs

````
