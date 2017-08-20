# 프로젝트 구조

# 주요 설정
## 정적 파일
* STATIC_URL: 웹 페이지에서 정적 파일을 참조하는 상위 루트 URL 경로 (개발/운영)
* STATIC_ROOT: manage.py collectstatic 명령어로 정적 파일을 한 곳에 모아놓는 경로 (운영)
* STATICFILES_DIRS: 여러 곳(여러 앱)에 산재한 정적 파일 디렉토리 (개발)
* STATICFILES_FINDERS: 동일한 정적 파일이 존재할 경우 찾는 우선순위 지정 (개발, 운영)

## 미디어 파일(업로드 경로)
* MEDIA_URL: 웹 페이지에서 미디어 파일을 참조하는 상위 루트 URL 경로 (개발/운영)
* MEDIA_ROOT: 실제 미디어 파일이 업로드 되는 경로 (개발/운영)

## 로깅
