## bauen und testen des Samples von
https://developer.confluent.io/quickstart/kafka-docker/

## starten cluster
docker-compose up -d

## topic anlegen
docker exec broker \
kafka-topics --bootstrap-server broker:9092 \
             --create \
             --topic quickstart

## message schreiben
docker exec --interactive --tty broker \
kafka-console-producer --bootstrap-server broker:9092 \
                       --topic quickstart

## CTRL-D um das Senden von Messages zu beenden

## alles Messages lesen
## am Besten in einem neuen Terminal auführen, um das Erstellen und Lesen von Messages zu sehen
docker exec --interactive --tty broker \
kafka-console-consumer --bootstrap-server broker:9092 \
                       --topic quickstart \
                       --from-beginning

## kafka wieder beenden
docker-compose down



## next sample
https://developer.confluent.io/tutorials/kafka-console-consumer-producer-basics/kafka.html

## bash in den broker
docker exec broker bash

## topic orders erstellen
docker-compose exec broker kafka-topics --create --topic orders --bootstrap-server broker:9092

## consumer mit key:value pair
kafka-console-consumer \
  --topic orders \
  --bootstrap-server broker:9092 \
  --from-beginning \
  --property print.key=true \
  --property key.separator=":"

## producer mit key:value pair
kafka-console-producer \
  --topic orders \
  --bootstrap-server broker:9092 \
  --property parse.key=true \
  --property key.separator=":"

## Schema registry for checking schemas
## prüft Daten auf Schemakonsistenz beim Schreiben (und Lesen?)
https://medium.com/slalom-technology/introduction-to-schema-registry-in-kafka-915ccf06b902
https://developer.confluent.io/tutorials/kafka-console-consumer-producer-avro/kafka.html





