# Description
This Excel macro is designed to help archivists and researchers automatically add Latitude and Longitude coordinates to datasets based on State and County values. It uses a reference worksheet containing geolocation mappings and appends the resulting coordinates to the main data sheet without overwriting any existing data.

## How to Enable Macros in Excel
Before using the macro, ensure macros are enabled:

Open Excel and go to File > Options > Trust Center > Trust Center Settings.

Click Macro Settings and select “Enable all macros”.

Save and re-open the file if needed.

When opening the .xlsm file, click "Enable Content" if prompted.

## Required Inputs
 ### Main Data Sheet (Named: Sheet1)
A dataset with at least two labeled columns:

State

County

### Reference Data Sheet (Named: ReferenceData)
Must contain the following four columns:

State

County

Latitude

Longitude

## How to Run the Macro
Open the Excel file.

Go to the Developer tab.

Click the “Run lat/long calculator”.


## Outputs
Adds two new columns: Latitude and Longitude

Populated using matches from the ReferenceData sheet




