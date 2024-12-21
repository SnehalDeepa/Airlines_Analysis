# Airlines_Analysis

## Business statement
  
This Airline Market Analysis project aims to provide airlines with data-driven insights to optimize operations, reduce delays, and enhance customer satisfaction. By analyzing key metrics such as flight performance, passenger demographics, and regional trends, the project offers actionable recommendations to improve efficiency, streamline processes, and support strategic business decisions in the competitive airline industry.

## Objective: 
The objective of the Airline Market Analysis project is to explore and analyze airline data to identify key patterns, trends, and performance metrics. This includes examining passenger demographics, flight status, operational efficiency, and delay patterns, to provide actionable insights that can help optimize airline operations and improve customer experiences.

## Overview:
In this project, I utilized SQL for data querying, Python for data manipulation and analysis, and Power BI for creating interactive visualizations. The analysis covers various aspects of the airline industry, including flight delays, passenger distribution, and performance by airport and region. The project aims to deliver valuable insights into operational improvements and strategic decision-making, helping airlines enhance efficiency and customer satisfaction.

## Tools Used

- sql
- python
- power bi

## Data Used
<a href="https://github.com/SnehalDeepa/Airlines_Analysis/blob/main/Airline%20Dataset%20Updated%20-%20v2%20update.csv"<Dataset</a>

# SQL Schema

```sql
 select * from airline_data;
```

### 1)GENDER DISTRIBUTION OF PASSENGER

```sql
SELECT Gender, COUNT(*) AS Count
FROM airline_data
GROUP BY Gender;
```

### 2)TOP 5 NATIONALITIES AMONG PASSENGERS

```sql
SELECT TOP 5 
    Nationality, 
    COUNT(*) AS Passenger_Count
FROM airline_data
GROUP BY Nationality
ORDER BY Passenger_Count DESC;
```

### 3)AVERAGE AGE OF PASSENGER BY NATIONALITY

```sql
SELECT TOP 10 Nationality, AVG(Age) AS Average_Age
FROM airline_data
GROUP BY Nationality
ORDER BY Average_Age DESC;
```

### 4)MOST FREQUENTED AIRPORTS BY PASSENGERS

```sql
SELECT Airport_Name, COUNT(*) AS Count
FROM airline_data
GROUP BY Airport_Name
ORDER BY Count DESC;
```

## 5)COUNTRIES WITH THE HIGHEST NUMBER OF DEPARTING FLIGHTS

```sql
SELECT Country_Name, COUNT(*) AS Count
FROM airline_data
GROUP BY Country_Name
ORDER BY Count DESC;
```

### 6)MOST COMMON CONTINENTS INVOLVED IN FLIGHT ROUTES

```sql
SELECT Continents, COUNT(*) AS Count
FROM airline_data
GROUP BY Continents
ORDER BY Count DESC;
```

### 7)OVERALL DISTRIBUTION OF FLIGHT STATUS

```sql
SELECT Flight_Status, COUNT(*) AS Count
FROM airline_data
GROUP BY Flight_Status;
```

### 8)AIRPORT OR COUNTRY WITH THE MOST DELAYED OR CANCELED FLIGHTS

```sql
SELECT Airport_Name, Country_Name, COUNT(*) AS Delayed_Canceled_Count
FROM airline_data
WHERE Flight_Status IN ('Delayed', 'Canceled')
GROUP BY Airport_Name, Country_Name
ORDER BY Delayed_Canceled_Count DESC;
```

### 9)BUSINESS DEPARTURE MONTHS AND DAYS

```sql
SELECT 
    MONTH(Departure_Date) AS Month, 
    COUNT(*) AS Count
FROM airline_data
GROUP BY MONTH(Departure_Date)
ORDER BY Count DESC;
```

```sql
SELECT 
    DAY(Departure_Date) AS Day, 
    COUNT(*) AS Count
FROM airline_data
GROUP BY DAY(Departure_Date)
ORDER BY Count DESC;
```

### 10)SEASONAL TRENDS IN FLIGHT DELAYS OR CANCELLATION

```sql
SELECT 
    MONTH(Departure_Date) AS Month, 
    COUNT(*) AS Delayed_Canceled_Count
FROM airline_data
WHERE Flight_Status IN ('Delayed', 'Canceled')
GROUP BY MONTH(Departure_Date)
ORDER BY Delayed_Canceled_Count DESC;
```

### 11)FLIGHT STATUS VARIATION BY TIME OF YEAR

```sql
SELECT 
    MONTH(Departure_Date) AS Month, 
    Flight_Status, 
    COUNT(*) AS Count
FROM airline_data
GROUP BY MONTH(Departure_Date), Flight_Status
ORDER BY Month, Count DESC;
```

### 12)AVERAGE AGE OF PASSENGERS USING DIFFERENT AIRPORTS

```sql
SELECT Airport_Name, AVG(Age) AS Average_Age
FROM airline_data
GROUP BY Airport_Name
ORDER BY Average_Age DESC;
```

### 13)POPULAR FLIGHT ROUTES BY PASSENGER AGE GROUPS

```sql
SELECT 
    CASE 
        WHEN Age < 18 THEN 'Under 18'
        WHEN Age BETWEEN 18 AND 35 THEN '18-35'
        WHEN Age BETWEEN 36 AND 50 THEN '36-50'
        ELSE '51+' 
    END AS Age_Group, 
    COUNT(*) AS Count
FROM airline_data
GROUP BY 
    CASE 
        WHEN Age < 18 THEN 'Under 18'
        WHEN Age BETWEEN 18 AND 35 THEN '18-35'
        WHEN Age BETWEEN 36 AND 50 THEN '36-50'
        ELSE '51+' 
    END
ORDER BY Count DESC;
```

### 14)TOP INSIGHTS OR TRENDS FROM THE DATA

### Summarize key metrics

```sql
SELECT 
    COUNT(DISTINCT Passenger_ID) AS Total_Passengers,
    COUNT(DISTINCT Pilot_Name) AS Total_Pilots,
    COUNT(DISTINCT CONCAT(Airport_Name, '-', Arrival_Airport)) AS Total_Routes,
    COUNT(*) AS Total_Flights,
    SUM(CASE WHEN Flight_Status = 'On-Time' THEN 1 ELSE 0 END) AS On_Time_Flights,
    SUM(CASE WHEN Flight_Status = 'Delayed' THEN 1 ELSE 0 END) AS Delayed_Flights,
    SUM(CASE WHEN Flight_Status = 'Canceled' THEN 1 ELSE 0 END) AS Canceled_Flights
FROM airline_data;
```

### 15)TOP NATIONALITIES AMONG PASSENGERS

```sql
SELECT TOP 5 
    Nationality, 
    COUNT(*) AS Passenger_Count
FROM airline_data
GROUP BY Nationality
ORDER BY Passenger_Count DESC;
```

### 16)TOP 5 AIRPORTS BY PASSENGER VOLUME

```sql
SELECT TOP 5
    Airport_Name, 
    COUNT(*) AS Passenger_Count
FROM airline_data
GROUP BY Airport_Name
ORDER BY Passenger_Count DESC;
```
