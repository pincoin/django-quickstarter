# 주요 설정
* `conf/settings/base.py`
* `conf/settings/local.py`, `conf/settings/production.py`
* `conf/settings/secret.py`

자세한 정보는 [설정 공식 문서](https://docs.djangoproject.com/en/1.11/topics/settings/)와 [전체 설정 옵션 문서](https://docs.djangoproject.com/en/1.11/ref/settings/)를 확인한다.

## 보안 설정 값
* SECRET_KEY: 비밀 키
* DEBUG: 디버깅 여부
* ALLOWED_HOSTS: 접속 허용 호스트

위 값은 개발환경과 운영서버의 값이 반드시 다르면서 소스코드 저장소에 공개되면 안 되는 내용이다.

## 템플릿 설정
일반적으로 저장소(repo) 디렉토리 안에 templates/ 디렉토리가 위치하지만 시스템 리소스는 conf/ 프로젝트 디렉토리 한 곳에서 관리하도록 한다.

## 국제화/지역화 설정

## 정적 파일
* STATIC_URL: 웹 페이지에서 정적 파일을 참조하는 상위 루트 URL 경로 (개발/운영)
* STATIC_ROOT: manage.py collectstatic 명령어로 정적 파일을 한 곳에 모아놓는 경로 (운영)
* STATICFILES_DIRS: 여러 곳(여러 앱)에 산재한 정적 파일 디렉토리 (개발)
* STATICFILES_FINDERS: 동일한 정적 파일이 존재할 경우 찾는 우선순위 지정 (개발, 운영)

일반적으로 저장소(repo) 디렉토리 안에 static/ 디렉토리가 위치하지만 시스템 리소스는 conf/ 프로젝트 디렉토리 한 곳에서 관리하도록 한다.

## 미디어 파일(업로드 경로)
* MEDIA_URL: 웹 페이지에서 미디어 파일을 참조하는 상위 루트 URL 경로 (개발/운영)
* MEDIA_ROOT: 실제 미디어 파일이 업로드 되는 경로 (개발/운영)

## 로깅
