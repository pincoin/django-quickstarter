# 비밀값

`conf/settings/secret.json` 파일 이름으로 저장하고 해당 코드는 절대로 공개 저장소에 커밋되어서는 안 된다.

## 보안 설정 값
* `SECRET_KEY`: 비밀 키
* `DEBUG`: 디버깅 여부
* `ALLOWED_HOSTS`: 접속 허용 호스트

위 값은 개발환경과 운영서버의 값이 반드시 다르면서 소스코드 저장소에 공개되면 안 되는 내용이다.

```json
{
  "DEBUG": true,
  "SECRET_KEY": "대소문자_숫자_특수문자_포함_50자리",
  "ALLOWED_HOSTS": [
    "localhost",
    "127.0.0.1",
    "[::1]"
  ]
}
```

## 데이터베이스 설정
### SQLite
```json
{
  "DATABASES": {
    "default": {
      "ENGINE": "django.db.backends.sqlite3",
      "NAME": "/home/myproject/django-quickstarter/db.sqlite3"
    }
  }
}
```

`os.path.join` 같은 파이썬 코드를 쓸 수 없는 json 파일이므로 SQLite 파일의 절대경로를 명시한다.

### PostgreSQL
```
pip install psycopg2
```

시스템에 postgresql이 설치되어 있어야 위 패키지 설치 가능하다.

테스트 버전

* PostgreSQL: 14.x(Ubuntu 22.04), 12.x(Ubuntu 20.04)

```json
{
  "DATABASES": {
    "default": {
      "ENGINE": "django.db.backends.postgresql",
      "NAME": "스키마_이름",
      "USER": "아이디",
      "PASSWORD": "비밀번호",
      "HOST": "호스트.주소",
      "PORT": "5432"
    }
  }
}
```

### MySQL (MariaDB)

```
pip install mysqlclient
```

시스템에 mysql이 설치되어 있어야 위 패키지 설치 가능하다.

테스트 버전

* MySQL: 5.7, 8.0
* MariaDB: 10.x

```json
{
  "DATABASES": {
    "default": {
      "ENGINE": "django.db.backends.mysql",
      "NAME": "스키마_이름",
      "USER": "아이디",
      "PASSWORD": "비밀번호",
      "HOST": "호스트.주소",
      "PORT": "3306",
      "OPTIONS": {
        "init_command": "SET sql_mode='STRICT_TRANS_TABLES'"
      }
    }
  }
}
```

### SQL Server

### Oracle
