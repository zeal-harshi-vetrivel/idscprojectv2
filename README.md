# CIFScientists

# Project Title: Analysis of Green House Gases Emitted by America’s 3rd Largest City

This repository is the culmination of a semester long project led by members of Illinois Data Science during the Spring semester of the academic year 2022-2023.

## About This Version

This copy (`idscprojectv2`) is a personal revision maintained by Harshi Vetrivel, meant to show how the analysis has evolved since the original 2023 submission. It replaces the original 2014-2020 data snapshot with a refreshed 2014-2023 export from the same source, fixes several data-cleaning bugs the original notebook had (see Methodology), and replaces the original grab-bag of exploratory/predictive analyses with a single, more rigorously tested question. The original team and description below are preserved as historical context; the Methodology and Dataset sections describe the current state of the notebook.

# Meet our Team:

Denise Bahena -  Co-Team Lead

Alekhya Nathella - Co-Team Lead 

Otniel Fernandez - Collaborator

Ryan Oh - Collaborator

Claire Quin - Collaborator

Claudia Robles - Collaborator

Harshi Vetrivel - Collaborator


# Official Description:

In an effort to stave off the environmental crisis that is predicted to occur later this century, many 
cities have begun to implement policies with the objective of reducing the ecological impact that urban places have on the environment due to their advanced industrialization. Thus, our goal is to analyze the energy program of one such city, Chicago, Illinois, to measure the success of their efforts as a whole, and locate any other trends regarding energy use in the city.

The technical tools used to complete this analysis are:
Python — Programming Language
Colab — Web IDE, for ease of collaboration

Packages used to complete analysis are:
Pandas — Data Analysis
Numpy — Number manipulation
Matplotlib.pyplot — Data Visualization

# Methodology
Chicago_Energy.ipynb is a Jupyter Notebook that:

1. Loads `Chicago_Energy_Benchmarking.csv` and cleans it: renames the portal export's human-readable column headers to the snake_case field names the API version uses, coerces the numeric columns the export formats with thousands separators (e.g. `"104,849"`) back to numeric, audits missing values and duplicate `(id, data_year)` records, and buckets each property's community area into a region.
2. Answers two questions the original single-snapshot version couldn't, now that the dataset spans 10 years (2014-2023):
   - **Has citywide GHG intensity actually declined, or does that just reflect a changing mix of reporting buildings?** Chicago's benchmarking ordinance phased in by building size, so the early reporting pool is a much smaller, different population than the later one. This is checked against a fixed panel of buildings with a multi-year reporting history, not just the raw yearly average.
   - **Among buildings tracked across multiple years, are individual buildings actually reducing their own emissions intensity?** Each repeat-reporting building gets its own year-over-year trend, rather than relying on a citywide average that a changing population or a few large movers could distort.

The original 2023 version instead asked whether GHG emissions were linearly associated with electricity use and square footage, and whether mean GHG intensity differed significantly across building types, using regression, a building-size classifier (Random Forest / KNN), and a Geopandas map. That analysis has been removed from this version in favor of the trend analysis above; it's still available in this repository's git history.

# Dataset: Chicago Energy Benchmarking, 2014-2023

Chicago Energy Benchmarking (CSV) sourced through: City of Chicago Data Portal. Refreshed September 2026 from the same source as the original project; replaces the original 2014-2020 snapshot (17,728 rows) with a 2014-2023 export (28,329 rows).

Chicago Outline shape files: used by the original version's Geopandas map, which this version no longer includes. Left in the repository in case a spatial visualization is added back later.

# Data Dictionary

Data Year: Calendar Year of every record

ID: A six digit unique identifier assigned to each property by the Chicago Energy Benchmarking Ordinance

Property Name: Official name of the property

Reporting Status: If the property submitted a report for that calendar year

Address: Street Address of the property

Zip Code: Zip Code of the property

Chicago Energy Rating: Zero to four star energy rating assigned to each property

Exempt from Chicago Energy Rating: Shows if the property is subject to the Chicago Energy Benchmarking Ordinance

Community Area: The Chicago community Area where the property is located

Primary Property Type: the primary function of a property

Gross Floor Area: The total indoor area of the property in square feet

Year Built: The year the property was built

Number of buildings: Number of buildings in the property

Water Use: Water use per year in thousands of gallons

Energy Star Score: Rating of property’s overall energy score out of 100

Electricity Use: Annual Electricity use in thousands of British Thermal Unit

Natural Gas Use: Annual Natural Gas use in thousands of British Thermal Unit

District Steam Use: Annual District Steam use in thousands of British Thermal Unit

District Chilled Water Use: Annual District Chilled Water use in thousands of British Thermal Unit

All Other Fuel Use: Annual Other Fuel use in thousands of British Thermal Unit

Site EUI: Site Energy Use Intensity is the energy use divided by the gross floor area 

Source EUI: Source Energy Use, Annual energy use to operate divided by the area in square feet

Weather Normalized Site EUI: Site Energy Use Intensity during 30-year average weather conditions

Weather Normalized Source EUI: Source Energy Use Intensity during 30-year average weather conditions

Total GHG Emissions: Total greenhouse gas emissions of carbon dioxide, methane and nitrous oxide in metric tons

GHG Intensity: Total GHG Emissions divided per square foot

Latitude: Latitude of the property

Longitude: Longitude of the property

Location: Latitude and longitude of the property

