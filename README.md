# hoofdchart met subcharts

Dit is een voorbeeld van hoe een chart met subcharts gebouwd kan worden in Helm 3.
We hebben een hoofdchart met subcharts. Een lokale subchart genaamd: subchart1 (nginx webserver). De tweede subchart is grafana van bitnami, opgehaald van internet. In de values.yaml van de hoofdchart zijn ook andere applicaties te vinden. Deze kunnen geinstalleerd worden door "enabled=false" naar "enabled=true" te zetten.

## Om te installeren:

1. Maak een namespace aan met de naam: thales (Deze wordt gebruikt door subchart1)

    ```kubectl create ns thales```

2. Zet de namespace naar: thales

    ```kubectl config set-context --current --namespace thales```

3. Kopiër het mapje hoofdchart en subchart1 van github naar de Desktop.
4. Open de terminal en navigeer naar het mapje hoofdchart.
5. Met de terminal in hoofdchart, update alle subcharts.

    ```helm dependency update```
    
6. Installeer de hoofdchart, die vervolgens de subcharts gaat uitrollen.

    ```helm install -f values.yaml test123 .```
    
7. Controleer of de subcharts correct geinstalleerd zijn. Als het goed is draaien er nu drie pods. 2x subchart1 en 1x grafana.

    ```kubectl get pods```
