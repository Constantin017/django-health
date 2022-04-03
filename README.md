# Django Health

## Result ?

- /health
- /health/db
- /health/cache
- /health/storage
- /health/migrate

## How to add django health check feature ?

1. On the project need to be installed package:

```bash
pip install django-health-check
```

2. On installed apps add:

```python
INSTALLED_APPS = [
    # ...
    # required
    'health_check',
    # stock Django health checkers
    'health_check.db',
    'health_check.cache',
    'health_check.storage',
    'health_check.contrib.migrations',
    # requires celery
    'health_check.contrib.celery',
    'health_check.contrib.celery_ping',
    # disk and memory utilization; requires psutil
    'health_check.contrib.psutil',
    # requires boto3 and S3BotoStorage backend
    'health_check.contrib.s3boto3_storage',
    # requires RabbitMQ broker
    'health_check.contrib.rabbitmq',
    # requires Redis broker
    'health_check.contrib.redis',
]
```

3. On the urls.py need to add access routes:

```python
urlpatterns = [
    # ...
    path('health/', include('health_check.urls')),
]
```

4. If we using DB check need to do migration.

```bash
python manage.py migrate
```

## More about this python django package

Detail information by link: https://pypi.org/project/django-health-check/
