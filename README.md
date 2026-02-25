# Ansible Role: Lighthouse

Роль для установки и настройки Lighthouse - инструмента для мониторинга производительности веб-приложений от VK.

## Описание

Роль выполняет следующие действия:
- Устанавливает nginx и unzip
- Скачивает и распаковывает Lighthouse
- Настраивает nginx для обслуживания Lighthouse
- Запускает и включает nginx в автозагрузку

## Требования

- Ansible >= 2.9
- Ubuntu (любая версия)

## Параметры роли

| Параметр | Значение по умолчанию | Описание |
|----------|----------------------|----------|
| `lighthouse_repo_url` | `https://github.com/VKCOM/lighthouse/archive/refs/heads/master.zip` | URL архива Lighthouse |
| `lighthouse_install_dir` | `/usr/share/nginx/html` | Директория для распаковки архива |
| `lighthouse_web_root` | `/usr/share/nginx/html/lighthouse-master` | Корневая директория веб-приложения |
| `lighthouse_nginx_conf` | `/etc/nginx/conf.d/lighthouse.conf` | Путь к конфигурационному файлу nginx |

## Пример использования

```yaml
- hosts: lighthouse_servers
  become: yes
  roles:
    - lighthouse-role
```

С переопределением параметров:

```yaml
- hosts: lighthouse_servers
  become: yes
  roles:
    - role: lighthouse-role
      vars:
        lighthouse_install_dir: /var/www
        lighthouse_web_root: /var/www/lighthouse-master
```

## Лицензия

MIT

## Автор

Dogafas
