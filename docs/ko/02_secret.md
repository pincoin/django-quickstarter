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
  "DATABASE": {
    "default": {
      "ENGINE": "django.db.backends.sqlite3",
      "NAME": "/home/myproject/django-quickstarter/db.sqlite3"
    }
  }
}
```

`os.path.join` 같은 파이썬 코드를 쓸 수 없는 json 파일이므로 SQLite 파일의 절대경로를 명시한다.

### PostgreSQL

### MySQL

### SQL Server

### Oracle
