# PyBer_Analysis


This repository contains a data analysis of a Start Up that offers transfer services, connecting drivers with users.

An analysis was performed using python and jupyter notebook to extract the following information:

- The total number of rides for each city type is retrieved.
- The total number of drivers for each city type is retrieved.
- The sum of the fares for each city type is retrieved.
- The average fare per ride for each city type is calculated. 
- The average fare per driver for each city type is calculated.)


# Result

Fig. 1 shows the analysis of the number of trips per city as a function of the average fare, for each type of city (Urban, Suburban & Rural). Note that the size of each point is 10 times the rider´s per city.

[Number of trips per city](https://github.com/dani1925/PyBer_Analysis/blob/main/resources/Fig1.jpg)

Another main objective in this analysis is to determine the following data:

- Total Rides per city type. 
- Total Drivers per city type.
- Total Fares per city type.
- Average Fare per Ride per city type.
- Average Fare per Driver per city type.

## Merge Data Frames

As a first step, you need to merge the two dataframes into a single dataset. 

    # Combine the data into a single dataset
    pyber_data_df = pd.merge(ride_data_df, city_data_df, how="left", on=["city", "city"])

## Total Rides per city type. 

To get the Total rides per city types it´s necesary to use the method "groupyby" in "type" column. To then aply the count() method to the "ride_id" column.

    1. Get the total rides for each city type
    city_type_ride_id = pyber_data_df.groupby(["type"]).count()["ride_id"]

## Total Drivers per city type.

To get the Total drivers per city types it´s necesary to use the method "groupyby" in "type" column. To then aply the sum() method to the "driver_count" column.

    # 2. Get the total drivers for each city type
    city_type_driver_count = city_data_df.groupby(["type"]).sum()["driver_count"]
    city_type_driver_count

## Total Fares per city type.

Similar ti the total drivers per city apply the sum() method to "fare" column.

    #  3. Get the total amount of fares for each city type
    city_type_fare = pyber_data_df.groupby(["type"]).sum()["fare"]

# Summary

The following figure is a graphic representation of the analyzed data.As expected, the highest average rate occurs in urban cities, with a fare average of $2250usd

[Totale FAre by City Type](https://github.com/dani1925/PyBer_Analysis/blob/main/PyBer_fare_summary.jpg)