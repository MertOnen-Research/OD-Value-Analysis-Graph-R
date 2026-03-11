OD Value Analysis & Automated Graphing in R
This repository provides an automated workflow for researchers to import, process, and visualize Absorbance (OD) data from Excel plate reader exports.

It is specifically designed to handle large volumes of files by automatically extracting experimental metadata (like Plate Number and Incubation Time) directly from the filenames.

Key Features
Batch Import: Processes an unlimited number of .xlsx files at once.

Filename Metadata Extraction: No more manual entry. The script "reads" the plate and hour from the file title.

Targeted Extraction: Uses specific cell ranges (e.g., D26:F29) to ignore software-generated headers.

Tidy Data Conversion: Automatically transforms "Wide" plate layouts into "Long" formats ready for ggplot2.

Statistical Visualization: Generates scatter plots with Mean ± SD error bars and trend lines.

1. File Naming Convention
To use the automation features, your Excel files must follow a consistent naming pattern. The script uses Regular Expressions to find digits following specific keywords.

Recommended Format: ExperimentName_plate 1_2h.xlsx

The script looks for the word "plate " to find the Plate ID.

The script looks for a number followed by "h" to find the Hour.

⚙️ 2. Installation & Setup
Ensure you have the following R libraries installed:


install.packages("tidyverse")
install.packages("readxl")
Clone this repository to your local machine.

Place all your absorbance Excel files in your Working Directory.

Open the R project and run the scripts in order.

🛠 3. Data Extraction Range
Plate readers often export a lot of "junk" text at the top of the Excel sheet. This script targets the raw data block directly.

Default Target: D26:F29

If your data sits in a different location (e.g., your plate layout is larger), simply adjust the range argument in the import_lab_data function.

4. Workflow Overview
Step 1: Automated Import
The script loops through your folder, opens every Excel file, grabs the data box, and tags it with the Plate/Hour info found in the filename.

Step 2: Stats Calculation
It groups the data by "Cells" (Concentration) and calculates the Mean and Standard Deviation for every group across all replicates.

Step 3: Graphing
A polished ggplot2 visualization is generated, showing raw data points (colored by Plate) overlaid with black mean points and error bars.

Contributing
If you use a different plate reader software (like Gen5, SoftMax Pro, etc.) and the coordinates change, feel free to fork this repo and submit a Pull Request with updated ranges!
