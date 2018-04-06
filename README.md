# Homework34 - Redis + HA

Для запуска ДЗ необходимо:
- задать на vboxnet0 адрес из подсети 10.0.0.0/24
- с использованием `vagrant up` создать рабочее окружение
- запустить установку `ansible-playbook hw33-redis.yaml`

Проверка:
- подключиться к srv1: `vagrant ssh srv1`
- на srv1 выполнить `watch redis-cli info replication`
- на экране srv1 отображается:
```
[root@srv1 ~]# redis-cli info replication
# Replication
role:slave
master_host:10.0.0.20
master_port:6379
master_link_status:up
...

```
- выключить srv2
- на экране srv1 отображается:
```
[root@srv1 ~]# redis-cli info replication
# Replication
role:slave
master_host:10.0.0.20
master_port:6379
master_link_status:up
...

```
- включить srv2
- redis на srv1 вернулся в состояние slave