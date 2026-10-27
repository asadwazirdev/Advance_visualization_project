# NYC Taxi Data Analysis - Final Report

## 1. Objective
Clean and prepare the NYC taxi trip data, create new features, scale and encode it, and use interactive charts to find insights about when, where and how people travel by taxi.

## 2. Dataset
- Source: Kaggle - NYC Taxi Trip Duration (yasserh)
- Raw size: 1,458,644 trips
- Period covered: 01 Jan 2016 to 30 Jun 2016
- Clean size: 1,438,277 trips (98.6% of the raw data kept)

## 3. Data cleaning
| Step | Rows removed | Rows left |
|---|---|---|
| Missing critical values | 0 | 1,458,644 |
| Duplicates | 0 | 1,458,644 |
| Unreadable dates | 0 | 1,458,644 |
| Invalid duration (<1 min, zero/negative or >3 h) | 10,707 | 1,447,937 |
| Invalid passenger count (not 1-6) | 19 | 1,447,918 |
| Coordinates outside NYC area | 855 | 1,447,063 |
| Zero distance (<0.1 km) | 7,445 | 1,439,618 |
| Impossible speed (<1 or >100 km/h) | 1,341 | 1,438,277 |

Why: zero-length trips, impossible speeds, GPS points outside New York and unrealistic passenger counts are data errors. Keeping them would distort every average and chart.

## 4. Feature engineering
- Time features: hour, day, month, weekday, weekend flag, rush-hour flag, time of day
- Distance (Haversine formula), trip duration in minutes, average speed (km/h)
- Categories: distance category (Short/Medium/Long/Very Long) and passenger group (Solo/Couple/Small/Large)

## 5. Scaling and encoding
- Min-Max scaling puts values between 0 and 1; Standardization centres them at 0 with a standard deviation of 1. The shape of the data stays the same in both cases.
- Min-Max is sensitive to outliers (a few long trips squeeze everyone else near 0); Standardization handles them better.
- Label encoding was used for passenger group, time of day and the store-and-forward flag. One-hot encoding was used for passenger group and time of day.

## 6. Key insights
1. **Typical trip:** about 3.5 km, 14.0 minutes, at 14.5 km/h on average. Most trips (47%) are in the 'Short (<2 km)' category.
2. **Demand peaks at 18:00** and is lowest at 5:00.
3. **Busiest weekday is Friday**, quietest is Monday. Weekends make up 29% of trips.
4. **Busiest month is March.**
5. **Speed and traffic:** rush-hour speed is 12.6 km/h against 15.2 km/h at other times (17% slower). The fastest hour is 5:00 (24.6 km/h) and the slowest is 15:00 (12.1 km/h).
6. **Who rides:** 'Solo' is the largest passenger group (71% of trips). 'Morning' is the most common time of day (25% of trips).
7. **Distance vs duration:** correlation is 0.78, so longer trips take more time, but traffic makes duration less predictable than distance alone.
8. **Weekday vs weekend:** average trip lasts 14.4 min on weekdays and 12.9 min on weekends.
9. **Map view:** 63% of all pickups are within 3 km of Times Square, while 5% are within 2 km of JFK or LaGuardia airport (see the geo map and density map).

## 7. Business recommendations
- Put more taxis on the road around 18:00 and on Fridays, and fewer around 5:00 to reduce idle time.
- Plan fares and driver schedules around rush hours, because trips are 17% slower then.
- Keep cars near the busiest pickup zones shown on the density map (63% of pickups are within 3 km of Times Square) and check airport coverage (5% of pickups are within 2 km of JFK or LaGuardia).
- Use the passenger group and time-of-day patterns for targeted offers (for example larger vehicles for group trips).

## 8. Limitations
- Cleaning thresholds (1 minute to 3 hours, 1 to 100 km/h, 0.1 km minimum distance) are reasonable choices, not official rules; other thresholds would change the numbers slightly.
- Haversine gives the straight-line distance, not the real road distance, so real trips are somewhat longer.
- The map charts use a random sample of 20,000 trips for speed.

## 9. Files produced
- `nyc_taxi_processed.csv` and `nyc_taxi_processed_sample.csv`
- `outputs/` folder: geo map, density map, animations, sunburst, scaling comparison and `trips_over_time.gif`