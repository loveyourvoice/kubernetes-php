1) Клонируем репо
2) Создаем PVC ```kubectl apply -f code-pvc.yaml```
3) Разворачиваем
```
kubectl apply -f php-fpm-deployment.yaml
kubectl apply -f nginx-deployment.yaml
kubectl apply -f nginx-configmap.yaml
kubectl apply -f services.yaml
```
4) Если используется **Docker Desktop** или **microk8s** , то сервис будет доступен по ссылке http://localhost/
5) Для того чтобы вытянуть изменения из гит репа и перезапустить php контейнер ```kubectl rollout restart deployment/php-fpm```

_В microk8s недоступны порты выкинутые LoadBalancer, нужно включить дополнение ```microk8s enable metallb```_