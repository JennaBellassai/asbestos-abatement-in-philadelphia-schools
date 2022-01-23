# asbestos-abatement-in-philadelphia-schools
Repo for exploring data from the Philadelphia City Controller's school district asbestos dashboard.

This repo contains the Jupyter notebook and data sources used to develop the visualizations in this blog post.

## Background

On November 10, 2021, the Office of the City Controller released [a dashboard](https://controller.phila.gov/philadelphia-audits/interactive-asbestos-dashboard/#/) displaying asbestos abatement projects in school buildings in the School District of Philadelphia. For more information about the dashboard, see [this press release](https://controller.phila.gov/city-controllers-office-releases-dashboard-on-school-district-asbestos-projects/) from the Office of the Controller and the dashboard's [About page](https://controller.phila.gov/philadelphia-audits/interactive-asbestos-dashboard/#/about).

The dashboard shows the number of asbestos abatement projects at school buildings in the district since 2016. I was interested to get a more detailed view of the data to answer questions such as:

* What is the total linear (and square) footage of asbestos removed or planned to be removed per school for these projects?
* Do schools with less funding in the district tend to have more linear (and square) footage of asbestos described in these projects?
* Do schools with a greater percentage of economically disadvantaged students tend to have more linear (and square) footage of asbestos described in these projects?
* Is the number and severity of asbestos abatement projects planned in the district increasing or decreasing over time?
* Do schools that opened in earlier years have more projects or more severe projects?

## Data

* __school-district-asbestos-download-1-23.csv__ - Downloaded from "Download Data" on the Office of the City Controller's [dashboard](https://controller.phila.gov/philadelphia-audits/interactive-asbestos-dashboard/#/) on 01/23/22. For information about this data, see the dashboard's [companion repo](https://github.com/PhilaController/asbestos-dashboard-data).
* __geocoded_addresses.csv__ - [File](https://github.com/PhilaController/asbestos-dashboard-data/blob/main/data/interim/geocoded_addresses.xlsx) containing facility address, latitude, longitude, and stress address for school buildings from the dashboard's companion repo.
* __schools.csv__ - Information about schools compiled from files in dashboard's companion repo.
* __district_school_budgets.csv__ - Budget information for schools for the 2021-2022 school year. Obtained from [PDF](https://cdn.philasd.org/offices/budget/FY22_School_Budget_Book.pdf) published on School District of Philadelphia website.

## Usage

To create the CSV files underlying the visualizations in [this blog post](https://jennabellassai.github.io/asbestos-projects-in-the-philadelphia-school-district), run the cells in asbestos_abatement.ipynb.

## Output
* __asbestos_lf_per_school.csv__ - Output file containing the following:
    * `School Name` - name of the school
    * `Economically Disadvantaged Percentage` - percentage of students classified as economically disadvantaged, according to [2021 School Budget Book](https://cdn.philasd.org/offices/budget/FY22_School_Budget_Book.pdf)
    * `FY 22 Budget (Total Positions) Per Proj Enrolled Student` - school budget according to [2021 School Budget Book](https://cdn.philasd.org/offices/budget/FY22_School_Budget_Book.pdf) per student based on projected enrollment for the 2021-2022 school year
    * `Year Opened` - year the school opened
    * `lat` - latitude
    * `long` - longitude
    * `Total LF` - total linear footage of asbestos material mentioned in asbestos abatement project descriptions for the school since 2016
* __asbestos_sf_per_school.csv__ - Output file containing all of the above columns except `Total LF`, with the addition of:
    * `Total SF` - total square footage of asbestos material mentioned in asbestos abatement project descriptions for the school since 2016