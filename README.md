# SQLalchemy-challenge

After making the decision to take some time off, it was decided to take a long holiday vacation in Honolulu, Hawaii! In preparation of the trip, planning was necessary to do some climate analysis on the area. The following steps were important to accomplish this task.

## Initial Step

# Climate Analysis and Exploration

To complete this part, Python and SQLAlchemy was used to perform basic climate analysis and data exploration of the climate database. Develop dnalysis through using SQLAlchemy ORM queries, Pandas, and Matplotlib.

* From provided [starter notebook](climate_starter.ipynb) and [hawaii.sqlite](Resources/hawaii.sqlite) files begin climate analysis and data exploration.

* Use SQLAlchemy’s `create_engine` to connect to SQLite database.

* Use SQLAlchemy’s `automap_base()` to reflect tables into classes and save a reference to those classes called `Station` and `Measurement`.

* Link Python to the database by creating a SQLAlchemy session.

* **Important:** Close out session at the end of the notebook.

# Precipitation Analysis

To perform an analysis of precipitation in the area, do the following:

* Find the most recent date in the dataset.

* Use this date to retrieve the previous 12 months of precipitation data by querying the 12 previous months of data. 
*   **Note:** Do not pass in the date as a variable into query.

* Select only the `date` and `prcp` values.

* Load the query results into a Pandas DataFrame, and set the index to the date column.

* Sort the DataFrame values by `date`.

* Plot the results by using the DataFrame `plot` method, as shown in the following image:

  ![precipitation](Images/precipitation.png)

* Use Pandas to print the summary statistics for the precipitation data.

# Station Analysis

To perform an analysis of stations in the area, do the following:

* Design a query to calculate the total number of stations in the dataset.

* Design a query to find the most active stations (the stations with the most rows).

    * List the stations and observation counts in descending order.

    * Which station id has the highest number of observations?

    * Using the most active station id, calculate the lowest, highest, and average temperatures.

    * Use functions such as `func.min`, `func.max`, `func.avg`, and `func.count` in the queries.

* Design a query to retrieve the previous 12 months of temperature observation data (TOBS).

    * Filter by the station with the highest number of observations.

    * Query the previous 12 months of temperature observation data for this station.

    * Plot the results as a histogram with `bins=12`, as shown in the following image:

    ![station-histogram](Images/station-histogram.png)

* Close out the session.

- - -

### Part 2: Design Climate App

After completion of initial analysis, design a Flask API based on the queries that were developed.

Use Flask to create the routes, as follows:

* `/`

    * Homepage.

    * List all available routes.

* `/api/v1.0/precipitation`

    * Convert the query results to a dictionary using `date` as the key and `prcp` as the value.

    * Return the JSON representation of the dictionary.

* `/api/v1.0/stations`

    * Return a JSON list of stations from the dataset.

* `/api/v1.0/tobs`

    * Query the dates and temperature observations of the most active station for the previous year of data.

    * Return a JSON list of temperature observations (TOBS) for the previous year.

* `/api/v1.0/<start>` and `/api/v1.0/<start>/<end>`

    * Return a JSON list of the minimum temperature, the average temperature, and the maximum temperature for a given start or start-end range.

    * When given the start only, calculate `TMIN`, `TAVG`, and `TMAX` for all dates greater than or equal to the start date.

    * When given the start and the end date, calculate the `TMIN`, `TAVG`, and `TMAX` for dates from the start date through the end date (inclusive).

## Key steps

* Join the station and measurement tables for some of the queries.

* Use Flask `jsonify` to convert the API data into a valid JSON response object.
