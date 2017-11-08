Weather Service
===========================================

Description
------------

This application is a simulation of a weather service which allows users to check the worldwide weather. 

Currently it supports two functions:

1. GetCitiesByCountry
      Get all major cities by country name.  Country name is optional. It would return all worldwide major cities if the country name is not provided.

2. GetWeather
      Get weather report by country name and city name.  Country name and city name are optional. If no weather report is found,  message "Data Not Found" would be returned.

    
Examples:
------------------------------------------
1. Retrieve all major cities in Australia:

Administrator@AUMMN MINGW64 /c/dev/Mule_workspace/weather_service

$ curl -G http://localhost:8081/globalweather/city?countryName="Australia"
  
  {
  "cities": [
    {
      "City": "Archerfield Aerodrome",
      "Country": "Australia"
    },
    {
      "City": "Amberley Aerodrome",
      "Country": "Australia"
    },
    {
      "City": "Alice Springs Aerodrome",
      "Country": "Australia"
    },
    {
      "City": "Brisbane Airport M. O",
      "Country": "Australia"
    }
  ]
}

2. Retrieve all major cities in worldwide (country name not provided):

$ curl -G http://localhost:8081/globalweather/city
{
  "cities": [
    {
      "City": "Williamtown Aerodrome",
      "Country": "Australia"
    },
    {
      "City": "Beijing",
      "Country": "China"
    },
    {
      "City": "Liverpool Bay",
      "Country": "Canada"
    },
    {
      "City": "Laboulaye",
      "Country": "Argentina"
    },    
    {
      "City": "Gillam, Man.",
      "Country": "Canada"
    }
  ]
 }   
    

3. Get the local weather report in Melbourne
       
http://localhost:8081/globalweather/weather?countryName=Australia&cityName=Melbourne

{
  "weather": {
    "Location": "Melbourne",
    "Time": "11 AM",
    "Wind": "15 km per hour",
    "Visibility": "10 km",
    "SkyConditions": "sunny",
    "Temperature": "18",
    "DewPoint": "2 C",
    "RelativeHumidity": "35",
    "Status": "Normal"
  }
}
      
4. Check the local weather report for Gladstone which is not supported

 http://localhost:8081/globalweather/weather?countryName=Australia&cityName=Gladstone
 
 
 HTTP/1.1 200 
 Content-Length: 16
 Content-Type: application/json
 Date: Wed, 08 Nov 2017 00:45:27 GMT

 "Data Not Found"


     
Structure:
----------
The project structure is built on top of Mule flow and follow the conventions. It has a set of unit tests and function tests to ensure the code quality. 


System Environment
------------------
* Java version: 1.8.0_45, vendor: Oracle Corporation
* Git version 2.5.1.windows.1
* Mule Anypoint Studio - Version: 6.3.0
* Mule Runtime 3.8.5 EE
* OS name: "windows 7", version: "6.1", arch: "amd64", family: "windows"


Building and Running
--------------------

Import the project into the Mule Anypoint Studio 6.3.0 via menus "File" -> "Import...",  then right click the project name and run it on the embedded Mule Runtime in AnyPoint Studio.


Version Control
---------------
Git is used for version control system. There are two git branches: dev is for the development and master is for the code release.  
The changes on dev are merged into master. Enter the project directory, enter the following command to get the git commit and merge history.

    git log


Future Improvements
-------------------
Several improvements could be done:

1. add fine exception strategy to handle failure cases
2. add Hypermedia support for API linking
3. Provide Asyn support through Hystrix
4. Secure API with OAUTH2


Major design decisions:
-----------------------
1. employ TDD and BDD
2. modular flows
3. Contract first API design - RAML
4. Use SoapUI for function tests


Challenging:
1. Used to use Spring Boot, Camel, Fuse,  new to Mule tech stack including RAML, DataWeaver.
2. Need to understand Mule development in short period of time
3. Different ways to solve the similar problems.



