# CP3-Devops-Hub_Iot

# Query Utilizada:
WITH AggregationStep AS
(
SELECT 
    System.Timestamp AS time,
    AVG(humidity) AS avg_humidity,
    MAX(humidity) AS max_humidity,
    MIN(humidity) AS min_humidity
FROM 
    IoTHubInput TIMESTAMP BY EventProcessedUtcTime
GROUP BY 
    TumblingWindow(second, 60)
)
SELECT 
    time,
    avg_humidity,
    max_humidity,
    min_humidity
INTO 
    powerbioutput
FROM 
    AggregationStep
   
 # Resultados no Power Bi:
