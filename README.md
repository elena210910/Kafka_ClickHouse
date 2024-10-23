# Kafka_ClickHouse

# Descripción del proyecto

Este proyecto está diseñado para cargar datos a través de la API de una compañía cervecera estadounidense en la base de datos 
ClickHouse a través de Kafka en tiempo real.

## Realización

Primero, verificamos el API (https://api.openbrewerydb.org/breweries)
con una solicitud GET para entender la estructura del archivo. 
Sabemos que los datos se devuelven en formato JSON. 
Para esto, escribiré un código en Python y revisaré los datos.
