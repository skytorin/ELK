# ELK Stack
# Elasticsearch, Logstash, Kibana, Beats

## Установка Elasticsearch
Копируем себе публичный ключ репозитория
```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```

Если нет пакета apt-transport-https, то надо установить
```bash
apt install apt-transport-https
```

Добавляем репозиторий Elasticsearch в систему
```bash
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list
```

Устанавливаем Elasticsearch на Debian или Ubuntu
```bash
apt update && apt install elasticsearch
```

После установки добавляем elasticsearch в автозагрузку и запускаем
```bash
systemctl daemon-reload 
systemctl enable elasticsearch.service 
systemctl start elasticsearch.service
```

Проверим, что процесс запущен
```bash
systemctl status elasticsearch.service
```

Проверим теперь, что elasticsearch действительно нормально работает. Выполним к нему простой запрос о его статусе. 
```bash
curl 127.0.0.1:9200
curl 192.168.8.243:9200
```

Перезапуск процесса
```bash
systemctl restart elasticsearch.service
```

Настройки Elasticsearch
```bash
vi /etc/elasticsearch/elasticsearch.yml
```
## Установка Kibana
Добавляем публичный ключ
```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -
```

Добавляем рпозиторий Kibana
```bash
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | tee -a /etc/apt/sources.list.d/elastic-7.x.list
```

Запускаем установку Kibana
```bash
apt update && apt install kibana
```

Добавляем Кибана в автозагрузку и запускаем
```bash
systemctl daemon-reload
systemctl enable kibana.service
systemctl start kibana.service
```

Проверяем состояние запущенного сервиса:
```bash
systemctl status kibana.service
```

Перезапустим службу
```bash
systemctl restart kibana.service
```

Настройки Kibana
```bash
vi /etc/kibana/kibana.yml
```

## Установка Logstash:
Добавляем публичный ключ
```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -
```

Добавляем рeпозиторий Logstash
```bash
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | tee -a /etc/apt/sources.list.d/elastic-7.x.list
```

Запускаем установку Logstash
```bash
apt update && apt install logstash
```

Добавляем logstash в автозагрузку и запускаем
```bash
systemctl enable logstash.service
systemctl start logstash.service
```

Просмотр установленных плагинов
```bash
cd /usr/share/logstash/bin
./logstash-plugin list
./logstash-plugin list | grep codec-csv
```

Устновка плагинов
```bash
./logstash-plugin install logstash-codec-csv
```
## Beats
### Filebeat
```bash
https://www.elastic.co/downloads/beats/filebeat
```
```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
или
echo "deb https://artifacts.elastic.co/packages/oss-7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
sudo apt-get update && sudo apt-get install filebeat
sudo systemctl enable filebeat
sudo update-rc.d filebeat defaults 95 10
```

### Packetbeat
```bash
https://www.elastic.co/downloads/beats/packetbeat
```

### Winlogbeat
```bash
https://www.elastic.co/downloads/beats/winlogbeat
```

### Metricbeat
```bash
https://www.elastic.co/downloads/beats/metricbeat
```
### Heartbeat
```bash
https://www.elastic.co/downloads/beats/heartbeat
```

### Auditbeat
```bash
https://www.elastic.co/downloads/beats/auditbeat
```

### Functionbeat
```bash
https://www.elastic.co/downloads/beats/functionbeat
```

##  Порты служб, пароли по умолчанию
Elasticsearch
```bash
IP:9200
elastic / changeme
```

Веб морда Kibana
```bash
http://IP:5601
```

Logstash
```bash
IP:5044
```

