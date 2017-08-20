# 프로젝트 생성
`django-admin.py` 명령어로 저장소에서 템플릿을 다운로드해서 프로젝트를 생성한다.

```
django-admin.py startproject --template https://github.com/pincoin/django-quickstarter/archive/master.zip repo
```

# `conf/settings/secret.py` 파일 생성

```
cp docs/ko/05_secret.md conf/settings/secret.py
```

# 프로젝트 실행
서버 실행을 하려면 설정 모듈을 정확히 지정해야 한다.

* 명령행 옵션으로 지정: `--settings=conf.settings.local`
* 환경변수로 지정: `DJANGO_SETTINGS_MODULE=conf.settings.local`

아래와 같이 명령행 옵션으로 테스트 서버를 구동할 수 있다.

```
manage.py runserver --settings=conf.settings.local
```

위 예시의 `local`이 아닌 `production`, `staging` 등으로 변경하여 구체적인 설정 파일을 지정할 수 있다.

만약 아무런 옵션도 지정하지 않는다면 [manage.py](/manage.py#L6) 파일 및 [conf/wsgi.py](/conf/wsgi.py#L14) 파일에서 `conf.settings.production` 값으로 간주한다.  