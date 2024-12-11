# DevSecOps_Homework_8


## Проверьте свои кластеры с помощью Kubernetes Bench
Установлен kube-bench согласно инструкциям, приведённым на GitHub:
https://github.com/aquasecurity/kube-bench


Скачен конфигурационный файл job.yaml для kube-bench
https://github.com/aquasecurity/kube-bench/blob/main/job.yaml

Конфиг применён при помощи команды:

```
kubectl apply -f job.yaml
job.batch/kube-bench created
```
Статус исполнения команд проверен:

```
administrator@ubuntu:~$ kubectl get pods
NAME                     READY   STATUS      RESTARTS   AGE
kube-bench-hxtsm         0/1     Completed   0          17m
nginx-54b9c68f67-cthp6   1/1     Running     0          50m
nginx-pod                1/1     Running     0          46m
```

Результат сохранён в логе пода и просмотрен при помощи команды:

```
kubectl logs kube-bench-hxtsm
```


Логи пода были экспортированы:

```
kubectl logs kube-bench-hxtsm >> kube-bench.log
```

И логи доступны по ссылке: [kube-bench.log](/logs/kube-bench.log)

# Настрена сетевая политика для ограниченного доступа между подами
Создан файл с сетевой политикой: [network-policy.yaml](/files/network-policy.yaml)
И применён при помощи команды:

```
kubectl apply -f network-policy.yaml
```

# Установлен Falco для мониторинга
Установка выполнена командой:
```
sudo apt-get install -y falco
```
Ниже приведён лог установки:

```
administrator@ubuntu:~$ sudo apt-get install -y falco
Чтение списков пакетов… Готово
Построение дерева зависимостей… Готово
Чтение информации о состоянии… Готово         
Уже установлен пакет falco самой новой версии (0.39.2).
Обновлено 0 пакетов, установлено 0 новых пакетов, для удаления отмечено 0 пакетов, и 28 пакетов не обновлено.
administrator@ubuntu:~$ 
```