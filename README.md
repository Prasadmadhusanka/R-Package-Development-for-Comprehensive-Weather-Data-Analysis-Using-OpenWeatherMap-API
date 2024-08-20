# R Package Development for Comprehensive Weather Data Analysis Using OpenWeatherMap API

## Repository Overview

This repository contains the complete development process and documentation for creating an R package designed for visualizing weather data sourced from the OpenWeatherMap API. The package, named **RAtmoGraphs**, includes all the necessary steps and files to build, document, and maintain the package effectively.

## Introduction:

Weather conditions play a crucial role in various aspects of our daily lives, ranging from agriculture and transportation to disaster preparedness and urban planning. With the advent of easily accessible weather data through APIs, there's an increasing need for tools that simplify the visualization and analysis of this data. In response to this need, an R package **RAtmoGraphs** that utilize the OpenWeatherMap API to extract, process, and visualize temperature, humidity, and wind speed data.

## Motivation

The motivation behind creating this R package to help researchers, analysts, and enthusiasts to easily understand weather data and get useful information from it. It aims to make the process simple and customizable for everyone. Dealing with raw data from weather APIs can be challenging to interpret. This package bridges this gap by providing easy-to-use functions that simplify the data extraction and visualization process. This helps you to understand the information better and use it to make decisions.
* The key functions within the package, namely `get_weather_data`, `map_temperature_data`, `map_humidity_data`, and `map_windspeed_data`, 
  address for  weather data visualization.
* The `get_weather_data` function efficiently compiles API responses into well-structured data frames. The mapping functions, on the 
  other hand, enable users to visualize the distribution of temperature, humidity, and wind speed across specific regions.
* The `map_temperature_data` function, which generates density heat maps of temperature data for the nearest 50 locations from the user's 
  specified location. This function aids in identifying temperature trends and anomalies, helping users make informed decisions based on 
  local weather conditions.
* Similarly, the `map_humidity_data` and `map_windspeed_data` functions employ dot-density maps to depict humidity and wind speed 
  distributions, respectively, offering insights into these critical weather parameters.

## Methodology

### Data Source

The data used in the "RAtmoGraphs" package is sourced from the [OpenWeatherMap API](https://openweathermap.org/api), a widely recognized and comprehensive platform for accessing weather data across the globe. OpenWeatherMap provides real-time and historical weather data, including temperature, humidity, wind speed, precipitation, and atmospheric pressure, among other parameters. The data is retrieved through the API's endpoints, which allow for the extraction of specific weather parameters for various geographical locations. For this package, the API is customized to extract data, including temperature, humidity, and wind speed, for 50 points surrounding the user’s specified location.

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
6.	

### R Package Development

The development and implementation of the "RAtmoGraphs" package involve several key steps, from package developmet to visualization and package deployment. Below is a detailed outline of the entire process.

**1. create_package():**

a. First, Call `create_package()` to initialize a new package in a directory on computer. create_package() will automatically create 
   that directory if it doesn’t exist yet.

**`create_package("~/path/to/RAtmoGraphs")`**

b. Then call `devtools` package in R whcih is widely used by developers for creating, testing, and managing R packages. It provides a 
   suite of functions that streamline the package development process. 

When create a new R package using create_package() from the devtools package, the function sets up a directory structure that includes several important files and subdirectories. These components are crucial for the organization, building, and distribution of R package

* **.Rbuildignore** and **.gitignore** help manage what gets included in final package and what gets tracked by version control.
* **DESCRIPTION** is essential for defining package's identity, dependencies, and author information, which are necessary for package 
   distribution and installation.
* **NAMESPACE** ensures that package’s interface is clean and that dependencies are correctly managed.
* The **R/ directory** is where the actual code lives, making it the heart of your package.
* The **.Rproj** file and **.Rproj.user** directory enhance the development experience in RStudio by managing your environment and 
  session settings

c. Then call `use_git()` function (which is often used alongside devtools in R package development) is used to initialize a Git 
   repository  in current project directory.




## Data Exploration:
Exploring the weather data is essential to explore characteristics and patterns within the dataset. It involves understanding the distribution, trends, and potential outliers present in the temperature, humidity, and wind speed variables. Here are some exploratory data analysis techniques that can be applied through this package to the weather dataset:
Geospatial Visualization: Use geographical plots (maps) to visualize the distribution of temperature, humidity, and wind speed across different locations. This can highlight regional variations and trends
By performing thorough data exploration, users of the R package can gain a comprehensive understanding of the weather data's characteristics and insights. This serves as a foundation for making informed decisions, conducting further analysis, and utilizing the package's visualization functions effectively to communicate findings.

## Analysis Results:

### Data Frame visualization
For analysis, extracted weather data using the get_weather_data function from our R package. This function efficiently gathered information on temperature, humidity, and wind speed from the OpenWeatherMap API for a specific region and time period. This raw data was then structured into a data frame, a tabular format that organizes the data for easy manipulation and analysis. The data frame provided a clear overview of the collected weather data, with each row representing an observation and each column corresponding to a specific variable (latitude, longitude, timestamp, temperature, humidity, wind speed, etc.). This organized structure allowed us to perform various analyses and visualizations to gain insights into the weather patterns

![Data Frame for Tempurature](https://github.com/UpekshaIndeewari/R_Package_RAtmoGraphs/blob/main/1.PNG)

### Geospatial Visualization:
A density heat map, visually represents the density or distribution of data points across a geographical area. It uses color gradients to highlight areas with higher or lower concentrations of data points. In the context of weather data visualization, a density heat map can show the spatial distribution of temperature across a region. Heat map symbology employs a dynamic raster visualization method that effectively represents the relative density of data points. It achieves this through a range of colors that reflecting the density values. This color scheme smoothly progresses from cooler shades, signifying areas with sparse point density, to warmer hues, indicating regions with a high concentration of points. This gradient of colors enables viewers to identify patterns and variations in data density across the displayed area and help to identify temperature trends, hotspots or cold spots. 

![Density heat map for Tempurature](https://github.com/UpekshaIndeewari/R_Package_RAtmoGraphs/blob/main/3.PNG)

A dot density map is a type of thematic map that employs dots to represent the spatial distribution of a particular phenomenon or attribute. Each dot on the map represents a predefined quantity of the phenomenon being studied. The arrangement and concentration of these dots provide insights into the density and patterns of the phenomenon across a geographical area. In the context of weather data visualization, a dot density map could be used to represent the distribution of variables like humidity and wind speed. For example, a dot density map of humidity might show each dot representing a certain percentage of humidity. Also the color and the size of the Dot relative the value of the parameter. Dots could be clustered in areas with higher humidity levels and sparser in regions with lower humidity.

Map for humidity

![Dot density heat map for Humidity](https://github.com/UpekshaIndeewari/R_Package_RAtmoGraphs/blob/main/5.PNG)

Map for Wind Speed

![Dot density heat map for Wind Speed](https://github.com/UpekshaIndeewari/R_Package_RAtmoGraphs/blob/main/7.PNG)


## Conclusion:
This analysis provides a comprehensive view of the weather data, highlighting the variations in temperature, humidity, and wind speed over a specific time period. The results presented above offer data's characteristics, trends, and relationships. The R package's visualization functions, such as density heat maps and distribution plots, enable users to easily interpret and communicate the findings, ultimately enhancing decision-making processes and further research in weather-related domains.
