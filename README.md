# Kafka_ClickHouse

# Descripción del proyecto

Este proyecto está diseñado para cargar datos a través de la API de una compañía cervecera estadounidense en la base de datos 
ClickHouse a través de Kafka en tiempo real.

## Realización

1. Verificamos el API (https://api.openbrewerydb.org/breweries)
   con una solicitud GET para entender la estructura del archivo. 
   Sabemos que los datos se devuelven en formato JSON. 
   Para esto, escribiré un [código en Python](https://github.com/elena210910/Kafka_ClickHouse/blob/main/Code_test_python) y revisaré los datos.

Los datos obtenidos:

![](https://github.com/elena210910/Kafka_ClickHouse/blob/main/screen1.PNG)

2. En los datos obtenidos podemos ver los nombres de las columnas,
   seleccionar las columnas necesarias y escribir el [código para enviarlos a Kafka.](https://github.com/elena210910/Kafka_ClickHouse/blob/main/Code_to_kafka)
   
    ***Bibliotecas utilizadas***
  
     **json:** Serialización y deserialización de datos JSON.
  
     **requests:** Realización de solicitudes HTTP al API.
  
     **kafka (KafkaProducer):**  Envío de datos a Kafka.

   

   
  

4. Ejecutemos nuestro archivo y luego revisemos la interfaz de Kafka. Veremos nuestro tópico allí.
   Actualmente, Kafka almacenará temporalmente nuestro archivo - 'breweriess', asegurando que los datos no 
   se pierdan si el consumer no está disponible.
    No especificamos el consumer en el código, así que el resto lo haré a través de ClickHouse.

   ![](https://github.com/elena210910/Kafka_ClickHouse/blob/main/screen2.PNG)




 5. Clickhouse.
    Ahora vamos a hablar de ClickHouse, una base de datos columnar, muy rápida y optimizada para OLAP.
    Su rendimiento se debe a sus motores de almacenamiento. Para obtener datos de Kafka, utilizaremos un motor especial.
    Os presento a ENGINE = Kafka 🚀🎆

    Primero, [crearemos una tabla](https://github.com/elena210910/Kafka_ClickHouse/blob/main/tabla_raw_breweries) (raw_breweries) que extraiga datos de Kafka,
    utilizando el puerto configurado, el nombre del tópico y asegurándonos de que las columnas coincidan.

    Segundo. Las tablas que utilizan el motor Kafka, como en nuestro caso raw_breweries, no se pueden manejar ni consultar como una tabla normal.
    [Crearemos una segunda tabla](https://github.com/elena210910/Kafka_ClickHouse/blob/main/tabla_breweries_data) (breweries_data) con la que podamos trabajar posteriormente.
    En esta tabla, si es necesario, se pueden cambiar los tipos de datos de las columnas. 
    Lo importante es que estén correctamente especificados, de lo contrario, los datos de la tabla raw_breweries no se transferirán.  
  








   
