# openresty-art

Helm-чарт для запуска openresty (nginx) со своим конфигом и HTML-страницами.

## Установка

    helm repo add openresty-art https://raw.githubusercontent.com/<ТВОЙ_ЛОГИН>/helm-charts/main/charts
    helm repo update
    helm install app openresty-art/openresty-art -n app --create-namespace

## Основные параметры

| Параметр | По умолчанию | Описание |
|---|---|---|
| application.replicaCount | 1 | Количество подов |
| application.reloader | false | Аннотации stakater reloader |
| application.image.tag | centos-rpm | Тег образа |
| application.resources | {} | Ресурсы контейнера |
| service.type | ClusterIP | ClusterIP или NodePort |
| service.nodePort | "" | Порт ноды для NodePort |
| ingress.enabled | false | Создавать Ingress |
| ingress.className | "" | Ingress-класс |
| conf.defaultConf | см. values.yaml | Конфиг nginx |
| html.* | index, 50x | HTML-файлы |

## Пример подмены файлов

    helm install app openresty-art/openresty-art \
      --set-file conf.defaultConf=my-default.conf \
      --set-file html.index=html/index.html
