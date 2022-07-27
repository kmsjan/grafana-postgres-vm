# grafana-postgres-vm

`docker compose up`


## VictoriaMetrics

VictoriaMetrics будет доступна на следующих портах:

* `--graphiteListenAddr=:2003`
* `--opentsdbListenAddr=:4242`
* `--httpListenAddr=:8428`

## vmagent

vmagent используется для очистки и отправки временных рядов в
экземпляр VictoriaMetrics. Он принимает совместимые с Prometheus
конфигурация `prometheus.yml` с перечисленными целями для очистки.

[Web interface link](http://localhost:8429/).

## vmalert

vmalert оценивает правила оповещения (`alerts.yml`) для отслеживания VictoriaMetrics
состояние здоровья. Он связан с AlertManager для срабатывания оповещений,
и с VictoriaMetrics для выполнения запросов и сохранения состояния предупреждений.

[Web interface link](http://localhost:8880/).

## alertmanager

AlertManager принимает уведомления от vmalert и запускает оповещения.
Все уведомления блокируются в соответствии с конфигурацией `alertmanager.yml`.

[Web interface link](http://localhost:9093/).

## Grafana

* /grafana-postgres/environment/.gfenv

To access service open following [link](http://localhost:3000).

Default credential:

* login - `admin`
* password - `admin`

Grafana по умолчанию снабжена следующими сущностями:

* VictoriaMetrics datasource
* Prometheus datasource
* VictoriaMetrics overview dashboard

## Postgres

* /grafana-postgres/environment/.pgenv
