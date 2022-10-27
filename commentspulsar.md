## pulsar mit websockets ausprobieren
docker run -it -p 6650:6650  -p 6651:8080 -v "$(pwd)"/pulsar/pulsardata:/pulsar/data -v "$(pwd)"/pulsar/pulsarconf:/pulsar/conf apachepulsar/pulsar:2.10.2 bin/pulsar standalone

docker run -it --mount source=$(pwd)/tmp,target=/tmp --rm busybox
docker run -it -v "$(pwd)"/tmp:/tmp --rm busybox



docker run -it -p 6650:6650  -p 6651:8080 --mount source=pulsardata,target=/pulsar/data --mount source=pulsarconf,target=/pulsar/conf apachepulsar/pulsar:2.10.2 bin/pulsar standalone


