

# Module 1 Homework – Docker & SQL

## Q1
pip version: 25.3

## Q2
Answer: db:5432

## Q3
SELECT COUNT(*) AS short_trips
FROM green_taxi_data_2025
WHERE trip_distance <= 1
  AND lpep_pickup_datetime >= '2025-11-01'
  AND lpep_pickup_datetime < '2025-12-01';

## Q4
SQL:
SELECT DATE(lpep_pickup_datetime) AS pickup_day, MAX(trip_distance) AS max_distance
FROM green_taxi_data_2025
WHERE trip_distance < 100
  AND lpep_pickup_datetime >= '2025-11-01'
  AND lpep_pickup_datetime < '2025-12-01'
GROUP BY pickup_day
ORDER BY max_distance DESC
LIMIT 1;

## Q5
SQL:
SELECT z.Zone, SUM(g.total_amount) AS total_amount
FROM green_taxi_data_2025 g
JOIN zones z ON g.pulocationid = z.LocationID
WHERE DATE(g.lpep_pickup_datetime) = '2025-11-18'
GROUP BY z.Zone
ORDER BY total_amount DESC
LIMIT 1;

## Q6
SQL:
SELECT z2.Zone AS dropoff_zone, g.tip_amount AS max_tip
FROM green_taxi_data_2025 g
JOIN zones z1 ON g.pulocationid = z1.LocationID
JOIN zones z2 ON g.dolocationid = z2.LocationID
WHERE z1.Zone = 'East Harlem North'
  AND lpep_pickup_datetime >= '2025-11-01'
  AND lpep_pickup_datetime < '2025-12-01'
ORDER BY g.tip_amount DESC
LIMIT 1;



