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
테스트 버전

* PostgreSQL: 14.x(Ubuntu 22.04), 12.x(Ubuntu 20.04)

```
pip install psycopg2
```

시스템에 postgresql이 설치되어 있어야 위 패키지 설치 가능하다.

```
brew install postgresql
```

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
테스트 버전

* MySQL: 5.7, 8.0
* MariaDB: 10.x

```
pip install mysqlclient
```

시스템에 mysql이 설치되어 있어야 위 패키지 설치 가능하다.

```
brew install mysql
```

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
테스트 버전: SQL Server 2014, 2016, 2017, 2019

```
pip install mssql-django
```

`2.3.11` 버전은 다를 수 있으므로 실제 설치 경로에 맞춰준다.

```bash
export CPPFLAGS="-I/opt/homebrew/Cellar/unixodbc/2.3.11/include"
export LDFLAGS="-L/opt/homebrew/Cellar/unixodbc/2.3.11/lib"
pip install pyodbc
```

ODBC 17 설치
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
HOMEBREW_NO_ENV_FILTERING=1 ACCEPT_EULA=Y brew install msodbcsql17 mssql-tools

# 18 설치 (22년 5월 현재 동작 안 함)
# HOMEBREW_NO_ENV_FILTERING=1 ACCEPT_EULA=Y brew install msodbcsql18 mssql-tools18
```

```json
{
  "DATABASES": {
    "default": {
      "ENGINE": "mssql",
      "NAME": "스키마_이름",
      "USER": "아이디",
      "PASSWORD": "비밀번호",
      "HOST": "호스트.주소",
      "PORT": "1433",
      "OPTIONS": {
        "driver": "ODBC Driver 17 for SQL Server"
      }
    }
  }
}
```

ODBC 드라이버
* `{ODBC Driver 17 for SQL Server}` - SQL Server 2008 ~ 2019
* `{ODBC Driver 18 for SQL Server}` - SQL Server 2012 ~ 2019 (22년 5월 현재 M1 맥북에서 동작 안 함)

#### mssql-django ~22년 4월 현재
* Django 3.2 / 4.0
* SQL Server 2016, 2017, 2019

#### django-mssql-backend ~20년 4월
* Django 2.2 / 3.0
* SQL Server 2008/2008R2, 2012, 2014, 2016, 2017, 2019

#### django-pyodbc-azure ~18년 8월
* Django 2.1
* SQL Server 2008/2008R2, 2012, 2014, 2016, 2017

### Oracle
테스트 버전: 12.x, 19.x

```
pip install cx-Oracle
```

https://www.oracle.com/kr/database/technologies/instant-client/macos-intel-x86-downloads.html
접속 후 Basic Package (DMG) 파일 다운로드 한다. 그리고 디렉토리 안에 `./install_ic.sh` 스크립트 실행하여 설치
M1에서는 Rosetta2 실행 필요

SID: DB 이름(aws 기본값: `ORCL`)
