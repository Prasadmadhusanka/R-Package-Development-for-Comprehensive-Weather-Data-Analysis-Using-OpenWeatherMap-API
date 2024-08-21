# R Package Development for Comprehensive Weather Data Analysis Using OpenWeatherMap API

## Repository Overview

This repository contains the complete development process and documentation for creating an R package designed for visualizing weather data sourced from the OpenWeatherMap API. The package, named **RAtmoGraphs**, includes all the necessary steps and files to build, document, and maintain the package effectively.

## Table of Content

- [Introduction](#introduction)
- [Motivation](#motivation)
- [Methodology](#methodology)
- [Analysis Results](Analysis-Results)
- [Conclusion](conclusion)
  - [Data Source](#data-source)


## Introduction

Weather conditions play a crucial role in various aspects of our daily lives, ranging from agriculture and transportation to disaster preparedness and urban planning. With the advent of easily accessible weather data through APIs, there's an increasing need for tools that simplify the visualization and analysis of this data. In response to this need, an R package **RAtmoGraphs** that utilize the OpenWeatherMap API to extract, process, and visualize temperature, humidity, and wind speed data.

## Motivation

The motivation behind creating this R package to help researchers, analysts, and enthusiasts to easily understand weather data and get useful information from it. It aims to make the process simple and customizable for everyone. Dealing with raw data from weather APIs can be challenging to interpret. This package bridges this gap by providing easy to use functions that simplify the data extraction and visualization process. This helps you to understand the information better and use it to make decisions.
* The key functions within the package, namely `get_weather_data`, `map_temperature_data`, `map_humidity_data`, and `map_windspeed_data`, address for  weather data visualization.
* The `get_weather_data` function efficiently compiles API responses into well structured data frames. The mapping functions, on the  other hand, enable users to visualize the 
  distribution of temperature, humidity, and wind speed across specific regions.
* The `map_temperature_data` function, which generates density heat maps of temperature data for the nearest 50 locations from the user's specified location. This function aids in 
  identifying temperature trends and anomalies, helping users make informed decisions based on local weather conditions.
* Similarly, the `map_humidity_data` and `map_windspeed_data` functions employ dot-density maps to depict humidity and wind speed distributions, respectively, offering insights into 
  these critical weather parameters.

## Methodology

### Data Source

The data used in the "RAtmoGraphs" package is sourced from the [OpenWeatherMap API](https://openweathermap.org/api), a widely recognized and comprehensive platform for accessing weather data across the globe. OpenWeatherMap provides real time and historical weather data, including temperature, humidity, wind speed, precipitation, and atmospheric pressure, among other parameters. The data is retrieved through the API's endpoints, which allow for the extraction of specific weather parameters for various geographical locations. For this package, the API is customized to extract data, including temperature, humidity, and wind speed, for 50 points surrounding the user’s specified location.

Key Features of the OpenWeatherMap API:

* Global Coverage: Offers weather data for any geographical location worldwide, including over 200,000 cities.
* Current and Historical Data: Provides both current weather data and historical weather data for analysis.
* Multiple Parameters: Allows access to a wide range of weather parameters such as temperature, humidity, wind speed, pressure, and more.
* Free and Paid Plans: OpenWeatherMap offers a free tier with limited access and paid plans that provide more extensive data and higher 
  request limits.

The dataset includes the following key variables:

1.	Station name
2.	Latitude
3.	Longitude
4.	Temperature / humidity / pressure
5.	description

### R Package Development

The development and implementation of the "RAtmoGraphs" package involve several key steps, from package developmet to visualization and package deployment. Below is a detailed outline of the entire process.

#### 1. create_package():

a. First, Call `create_package()` to initialize a new package in a directory on computer. `create_package()` will automatically create 
   that directory if it doesn’t exist yet.

**`create_package("~/path/to/RAtmoGraphs")`**

b. Then call `devtools` package in R whcih is widely used by developers for creating, testing, and managing R packages. It provides a 
   suite of functions that streamline the package development process. 

When create a new R package using create_package() from the devtools package, the function sets up a directory structure that includes several important files and subdirectories. These components are crucial for the organization, building, and distribution of R package.

* **.Rbuildignore** and **.gitignore** help manage what gets included in final package and what gets tracked by version control.
* **DESCRIPTION** is essential for defining package's identity, dependencies, and author information, which are necessary for package distribution and installation.
* **NAMESPACE** ensures that package’s interface is clean and that dependencies are correctly managed.
* The **R/ directory** is where the actual code lives, making it the heart of your package.
* The **.Rproj** file and **.Rproj.user** directory enhance the development experience in RStudio by managing your environment and session settings.

Following shows important files and sub categories created 

![create package](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/create%20pakage.PNG)

#### 2. use_git()

Then call `use_git()` function (which is often used alongside devtools in R package development) is used to initialize a Git repository in current project directory.

#### 3. Developing Core Functions

**Function for API Integration**

* `get_weather_data` Function: 
Develop the `get_weather_data` function to interact with the OpenWeatherMap API. This function should accept parameters like station name,latitude, longitude, type of weather data (e.g., temperature, humidity, wind speed) and description. The function will send HTTP GET requests to the API, retrieve the data, and structure it into a data frame. It gives the details for 50 nearest locations from the user.

**Functions for Visualization:**

* Temperature Visualization (`map_temperature_data`):
  Develop the `map_temperature_data` function to create density heat maps using the processed data. Utilize packages like `ggplot2`, 
  `sf`, or `leaflet` for creating visualizations.

* Humidity Visualization (`map_humidity_data`):
  Create a function to generate dot-density maps for humidity data. Each dot can represent a predefined quantity of humidity, with color 
  or size variations to indicate intensity.

* Wind Speed Visualization (`map_windspeed_data`):
  Similarly, develop a function for wind speed visualization using dot-density mapping techniques.

#### 4.	use_r()

Then call `use_r()` function to create new R script files within R package project. These script files are stored in the `R/` directory of package and are essential for defining the functions and code that make up the core functionality of the package. This directory is where  typically store the R functions and other R code files.

![use_r](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/usr_r.png)

#### 5.	Load_all()

The `load_all()` function from the devtools package  is a crucial tool for R package development. It helps streamline the process of loading and testing of package’s functions during development. Calling  `load_all()`  loads all the functions and objects from package’s R/ directory into R session. This allows testing and interacting with the package as if it were installed. Also Instead of installing the package (which involves building and installing it into the R library), and allows to quickly load the package code without going through the installation process. This is useful for rapid development and testing. Whenever make changes to package code, `load_all()` ensures that the latest version of the package is loaded into R session. This way, can immediately test the updates without needing to reinstall the package.

#### 6.	check()

Then call `check()` function from the devtools package is an essential tool for validating the integrity and quality of R package. Running `check()` helps ensure that package meets CRAN (Comprehensive R Archive Network) standards and adheres to best practices for R package development. `check()` performs a series of automated checks on the package, including verifying the package structure, documentation, and code quality. It runs the same checks as R CMD check, which is the standard for package validation in R. 

It checks that all functions and datasets in the package are properly documented. This includes verifying that roxygen2 comments are correctly converted into .Rd files and that documentation fields are complete. Also It ensures that the code follows standard R coding practices, including naming conventions and formatting. This helps maintain consistency and readability. Also it checks that all package dependencies are correctly specified and that the package can be built and installed without missing dependencies. The function provides a comprehensive report of any errors, warnings, or notes that arise during the checks, helping you identify and fix issues before distributing the package.

#### 7.	Edit DESCRIPTION

Then edit the description file. The `DESCRIPTION` file is a critical component of any R package. It contains metadata about the package, including its name, version, dependencies, and more.  This information is used to understand the package’s purpose and requirements. Editing the DESCRIPTION file correctly is essential for ensuring that the package is properly configured, adheres to standards, and functions as expected. Under dependencies, It lists other R packages that  package depends on, ensuring that all necessary dependencies are installed when the package is used. It specifies the license under which your package is distributed, informing users of their rights and obligations. Also It includes additional information such as the package’s URL, bug reports, and collaborators.

![description](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/DESCRIPTION.PNG)

#### 8.	use_mit_license()

The `use_mit_license()` function is used to add an MIT License to R package. The MIT License is a popular open-source license known for its simplicity and permissiveness. It allows others to freely use, modify, and distribute code, as long as they include the original copyright notice and license text. When calling `use_mit_license()`, it generates a LICENSE file in the root directory of R package, which contains the text of the MIT License. This file is crucial for ensuring that the package’s licensing terms are clearly communicated. The function adds placeholders for author name and the year in the license text, which should customize to reflect the actual author and the current year. Including a license file in package clarifies the terms under which others can use, modify, and distribute code. This protects your rights as an author and informs users of their obligations. The MIT License is permissive and well-understood, which can encourage other developers to use and contribute to package.

![mitlicnse](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/mit_license.png)

#### 9.	Document()

By call The `document()` function from the devtools package is used to generate documentation files for R package based on the comments and annotations in R script files. This process involves converting Roxygen2 comments (which are used to document functions and other objects in the package) into .Rd files, which are the standard documentation format for R packages. It creates .Rd (R documentation) files in the `man/` directory of package. These files are used to create the help pages for your functions, datasets, and other objects. It updates the documentation files based on the latest Roxygen2 comments in R scripts. This ensures that the documentation is in sync with code. It also updates the NAMESPACE file to include any new functions or datasets that have documented or to adjust exports according to annotations.

![doument](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/mit_license.png)

#### 10. check() again

After calling the `document()` function to generate or update the package documentation, it’s essential to run the `check()` function to validate that everything in the package is functioning correctly and adheres to best practices. Once this function call regexcite should pass R CMD check cleanly now and forever more: 0 errors, 0 warnings, 0 notes.

![check](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/check_again.PNG)

#### 11. install()

The `install()` function from the devtools package is used to install the R package locally on the machine. This is a crucial step in the development process, allowing to test and use the package as if it were an installed package from CRAN or any other repository. It builds the package from source and installs it into local R library. This includes compiling any C/C++ code if applicable and ensuring that all dependencies are correctly handled. 

After installation, the package is available for loading and testing in R environment. Then can use library(packageName) to load it. Also It allows to verify that the package installation process is successful and that the package is functioning as expected in the local environment. After making changes to package, use `install()` to apply these changes locally and test them before finalizing or distributing the package. Ensures that the package is correctly built and installed, and that all functions and features work as expected. It is an integral part of the development workflow, allowing to iteratively build, install, and test the package.

![instsll](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/install.PNG)

#### 12. use_testthat()

The `use_testthat()` function from the usethis package is used to set up the testthat framework for testing within R package. testthat is a popular package for unit testing in R, providing tools to write and run tests to ensure that package functions as expected. It creates a tests/testthat/ directory in package structure, including essential files for organizing and running tests.It adds testthat as a dependency in package’s DESCRIPTION file, ensuring that testthat is installed when the package is used. Also it generates a sample test file (tests/testthat/testthat.R) with basic content to help get started with writing tests and configures the basic setup needed for running tests with testthat.

![usetest](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/test.png)

#### 13. use_package()

The `use_package()` function from the usethis package is designed to simplify the process of adding package dependencies to R package. This function helps you declare that package depends on or imports another package, which ensures that the required package is installed and available when package is used. It modifies the DESCRIPTION file of package to include the specified package as a dependency. It adds the package to the Imports, Depends, or Suggests field, depending on the arguments you provide. It updates the NAMESPACE file to import the specified package's functions, making them available within ythe package's functions. This is particularly useful for ensuring that the necessary functions are available when the package is loaded. By declaring dependencies properly, it ensures that anyone using or developing the package will have the required packages installed, reducing the risk of missing dependencies and related issues.

#### 14. use_readme_rmd()

The `use_readme_rmd()` function from the usethis package is used to set up a README file for  R package using R Markdown. R Markdown is a versatile tool for creating dynamic documents, and it allows to write  README file in a format that can include both code and narrative text. This function helps create a standardized and comprehensive README that can include instructions, examples, and other relevant information about package. It includes a basic template in the README.Rmd file, with placeholders and structure to help you get started. The template typically includes sections like package description, installation instructions, usage examples, and more.

![readme](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/readme.PNG)

#### 15. The end, check() and install()

Once set up the  R package with all the necessary components such as writing functions, adding documentation, and setting up tests need to ensure that the package is correctly structured and functional. This is where the `check()` and `install()` functions come into play.

#### 16. Creating vignettes

Creating vignettes for an R package is an important step in providing comprehensive documentation and examples of how to use the package. Vignettes are long-form guides or tutorials that demonstrate the functionalities of R package in a more detailed and narrative manner compared to traditional documentation.

![vigneete](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/vignette.png)

Following describe step by step guide on how to create vignettes for R package:

**a. Set Up the `knitr` and `rmarkdown` Packages**

Vignettes are typically written in R Markdown (`.Rmd` files), so need the `knitr` and `rmarkdown` packages to create and render 
them.
     
**`install.packages(c("knitr", "rmarkdown"))`**

**b. Add the `vignette` Directory**

Then  need to create a `vignettes` directory in R package structure if it doesn’t already exist. This is where all  vignette files 
will be stored.
     
**`usethis::use_vignette(“vignette-name")`**
     
This command creates a new R Markdown file and adds the necessary entries to `DESCRIPTION` file.

**c. Edit the Vignette**

Open the newly created R Markdown file in the `vignettes` directory and edit it to include content. The file will have a `.Rmd` 
extension and should include:

- Title and Metadata: At the top of the file, provide a title and other metadata using YAML syntax.
-  Narrative Text: Write descriptive text explaining the features and use cases of your package.
-  Code Chunks: Include R code chunks that demonstrate how to use package. These chunks should be wrapped in ```{r} ``` for 
   execution.
  
**d. Build and Test**
  
Use `devtools::build_vignettes()` and `devtools::check()` to ensure the vignette is correctly included and functioning.
  
#### 17. Building and Installing the Package

Use `devtools::build()` to compile R package into a tarball (.tar.gz) file. This file can then be shared or uploaded to repositories like CRAN or GitHub.

## Analysis Results

### Data Exploration

Exploring the weather data is essential to explore characteristics and patterns within the dataset. It involves understanding the distribution, trends, and potential outliers present in the temperature, humidity, and wind speed variables.  Use geographical plots (maps) to visualize the distribution of temperature, humidity, and wind speed across different locations. This can highlight regional variations and trends. By performing thorough data exploration, users of the R package can gain a comprehensive understanding of the weather data's characteristics and insights. This serves as a foundation for making informed decisions, conducting further analysis, and utilizing the package's visualization functions effectively to communicate findings.

### Data Frame Visualization

For analysis, extracted weather data using the `get_weather_data` function from  R package. This function efficiently gathered information on temperature, humidity, and wind speed from the OpenWeatherMap API for a specific region and time period. This raw data was then structured into a data frame, a tabular format that organizes the data for easy manipulation and analysis. The data frame provided a clear overview of the collected weather data, with each row representing an observation and each column corresponding to a specific variable (location name, latitude, longitude, timestamp, temperature, humidity, wind speed, and description etc.). This organized structure allowed us to perform various analyses and visualizations to gain insights into the weather patterns

![Data Frame for Tempurature](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/dataframe.PNG)

### Geospatial Visualization:

A **density heat map**, visually represents the density or distribution of data points across a geographical area. It uses color gradients to highlight areas with higher or lower concentrations of data points. In the context of weather data visualization, a density heat map can show the spatial distribution of temperature across a region. Heat map symbology employs a dynamic raster visualization method that effectively represents the relative density of data points. It achieves this through a range of colors that reflecting the density values. This color scheme smoothly progresses from cooler shades, signifying areas with sparse point density, to warmer hues, indicating regions with a high concentration of points. This gradient of colors enables viewers to identify patterns and variations in data density across the displayed area and help to identify temperature trends, hotspots or cold spots. 

**Map for tempurature**

![Density heat map for Tempurature](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/heatmap2.PNG)

A **dot density map** is a type of thematic map that employs dots to represent the spatial distribution of a particular phenomenon or attribute. Each dot on the map represents a predefined quantity of the phenomenon being studied. The arrangement and concentration of these dots provide insights into the density and patterns of the phenomenon across a geographical area. In the context of weather data visualization, a dot density map could be used to represent the distribution of variables like humidity and wind speed. For example, a dot density map of humidity might show each dot representing a certain percentage of humidity. Also the color and the size of the Dot relative the value of the parameter. Dots could be clustered in areas with higher humidity levels and sparser in regions with lower humidity.

**Map for humidity**

![Dot density heat map for Humidity](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/humidity%20map.PNG)

**Map for Wind Speed**

![Dot density heat map for Wind Speed](https://github.com/UpekshaIndeewari/R-Package-Development-for-Comprehensive-Weather-Data-Analysis-Using-OpenWeatherMap-API/blob/main/images/windspeed%20map.PNG)

## Conclusion

This analysis provides a comprehensive view of the weather data, highlighting the variations in temperature, humidity, and wind speed over a specific time period. The results presented above offer data's characteristics, trends, and relationships. The R package's visualization functions, such as density heat maps and distribution plots, enable users to easily interpret and communicate the findings, ultimately enhancing decision-making processes and further research in weather-related domains.
