# 비밀값
`conf/settings/secret.py` 파일 이름으로 저장하고 해당 코드는 절대로 공개 저장소에 커밋되어서는 안 된다.

아래 코드는 `conf/settings/secret.py` 파일 설정 예시이다.

```python
class Secret:
    # 보안 경고: 운영서버에서는 디버그 옵션을 끈다.
    DEBUG = True

    # 보안 경고: 운영서버에서는 접속 허용 서버를 명시적으로 지정해야 한다.
    ALLOWED_HOSTS = ['localhost', '127.0.0.1', '[::1]', ]

    # 보안 경고: 비밀키는 절대 노출되면 안 된다.
    # 아래 사이트에서 난수를 생성하여 사용할 수 있다.
    # http://www.miniwebtool.com/django-secret-key-generator/
    SECRET_KEY = 'g^fs)i_j9)2vntprrti&!9bmrfpmgcx4$agviz)=2qz'

    # 데이터베이스 접속 정보 (기본값: SQLite3)
    # https://docs.djangoproject.com/en/1.11/ref/settings/#databases
    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': 'db.sqlite3',
            'USER': None,
            'PASSWORD': None,
            'HOST': None,
            'PORT': None,
        }
    }
```