![chicago_aerial_view](./images/chicago_aerial_view.jpg)

# Chicago-Vehicle-Crash-Analysis

**Authors**: [Morgan Goode](https://www.linkedin.com/in/morgangoode/), [Jimmy McLaughlin](https://www.linkedin.com/in/james-mclaughlin-wm/), [Sean Harris](https://www.linkedin.com/in/sean-harris-data-sci-and-finance/)

## Busines Problem

### Stakeholders:
* [Mayor Bandon Johnson](https://www.chicago.gov/city/en/depts/mayor.html)
* [Vision Zero](https://www.chicago.gov/city/en/depts/cdot/supp_info/vision-zero-chicago.html)
![VisionZeroLogo](./images/VisionZeroLogo.png)

### Background:
Vision Zero is Chicago’s commitment to eliminating fatalities and serious injuries from traffic crashes. They believe that every crash is but a predictable and preventable occurrence and that no traffic-related death is acceptable.

### Our Goal:
In this hypothetical scenario, our team has been tasked with analyzing Chicago crash data provided by the city in order to predict loss of life or severe injury (alternately referred to as an incapacitating injury) in the event of a car crash involving an impaired driver.

## Data

The Chicago Data Portal provides the public with datasets on traffic crashes from 2013 through the present. We used two tables to conduct our analysis:
1.   [Crashes](https://data.cityofchicago.org/Transportation/Traffic-Crashes-Crashes/85ca-t3if) contains data on each traffic crash on that takes place in the city and falls under the jurisdiction of the Chicago Police Department.
2.   [People](https://data.cityofchicago.org/Transportation/Traffic-Crashes-People/u6pd-qa9d) contains data on people involved in a crash and if any injuries were sustained.

### Data Limitations

Incomplete records containting null values as well as values that appeared to be obvious human clerical errors (such as -177-year-old or a 3-year-old drunk driver) necessitated cleaning and imputation.

## EDA, Merging and Filtering

Our initial 2018 - 2023 dataset contained ~1.3 million records of people involved in ~700K car crashes.

We merged `people` with `crashes` and filtered by date beginning with 2018 (the first year complete data is available) through 2023.

Filtering for crashes involving **impaired** people resulted in ~13.3K people involved in ~7.7K crashes.

### Features of Interest

#### Defining **impaired**:
 * People 21+ with a blood alchohol content (BAC) >= 0.08, people < 21 with a BAC < 0.0
 * People whose physical condition was determined to have contributed to the accident and was described as having involved substances (e.g.: alcohol, drugs, medication, etc.).
 * Crashes where the primary and/or secondary cause was due to drugs or alcohol.

#### Primary features of interest:
* From people data:
  * Physical condition
  * Blood alcohol content and test status (e.g.: taken, not offered, refused etc.)
  * Person type (e.g.: driver, passenger, pedestrian, cyclist, etc.)
  * Age
  * Sex
* From crash data:
  * Primary crash cause
  * Secondary crash cause
  * Crash type (injury/tow or no injury/drive away)
  * Hit and run (Y/N)
  * Total severe injuries and fatalities
  * Crash hour
  * Lighting condition
  * Posted speed limit
  * Location (latitude and longitude)
* New custom/aggregate features:
  * Is driver (Y/N)
  * Total drivers in crash
  * Under influence (Y/N)
  * Total serious injuries (inclusive of fatal and incapacitating)
  * Has serious injury (Y/N) <-- `OUT TARGET COLUMN`
    * The 'target' created a highly imbalanced data set   
    
## Models



### Findings from models:

* An impaired driver has 13% higher odds of fatality or severe injury
* Drivers have 50% less odds of death or severe injury
* Men have 9% higher odds of death or severe injury from a crash than women

# Conclusion

To reduce serious and ftal accident involving intoxication Vision Zero Chicago should:

* Consider change to hit and run policy
* Follow up with survivors
* PSA targeted at passengers and cyclists

## Next Steps

* Analyze high-volumne crash areas
* Examine if the treating hospital has impact on survival rate
* Analyze the people data for insights on repeat offenders

# For More Information

See the full analysis in the [Jupyer Notebook](Phase3_Project_Master_Dataset_Build_people_crashes.ipynb) or review [this presentation](Chicago_Crash_Data_Presentation.pdf).

Technical Lead: [Morgan Goode](https://www.linkedin.com/in/morgangoode/)
Presentation Lead: [Jimmy McLaughlin](https://www.linkedin.com/in/james-mclaughlin-wm/)
Github Lead: [Sean Harris](https://www.linkedin.com/in/sean-harris-data-sci-and-finance/)

## Repository Structure
```
├── data
├── images
├── .gitattributes
├── .gitignore
├── Chicago_Crash_Data_Presentation.pdf
├── Phase3_Project_MAster_Dataset_Build_people_crashes.ipynb
└── README.md
```
