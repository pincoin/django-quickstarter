# django-allauth
## 개요
이메일 인증 로그인을 지원하는 방법은 크게 두 가지이다:

* 커스텀 사용자 모델 정의 + `django-registration` 패키지
* `django-allauth` 패키지

소셜 로그인을 제공하는 대표적인 패키지는 다음과 같다:

* `django-social-auth` (개발 중단)
* `python-social-auth` (개발 중단)
* `social-app-django` (단, 패키지명은 `social-auth-app-django`)
* `django-allauth`

즉, 이메일 인증 로그인을 구현하고 소셜 로그인을 구현하는 방법은 아래와 같이 나눌 수 있다:

* 커스텀 사용자 모델 정의 + `django-registration` + `social-app-django`
* `django-allauth`

[django-quickstarter](https://github.com/pincoin/django-quickstarter) 프로젝트는 `django-allauth` 사용을 권장한다.

django-allauth의 장점은 거의 대부분의 소셜 로그인을 지원하고 회원가입시킬 수 있다.
SNS 공급자(provider)가 제공하는 부정확한 정보(예: 인증 받지 않은 이메일 주소 등)를 로그인 연동 과정에서 정확한 입력 요구할 수 있다.
특히, Django 시스템 기존 사용자의 경우에도 /accounts/social/connections/ 경로에서 소셜 로그인 계정 연동할 수 있고 remember me 기능도 지원한다.

## 사이트 프레임워크
Django 공식 패키지에서 `django.contrib.sites` 프레임워크를 제공한다. 이를 이용하여 사이트 기본 정보를 설정하고 복수 사이트를 구현할 수 있다.

django-allauth 앱을 이용하려면 사이트 프레임워크를 등록하고 올바로 설정해야 한다.

### 사이트 프레임워크 등록
`conf/settings/local.py` 파일 수정(운영서버는 `conf/settings/production.py`)

```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'django.contrib.sites', # <- 추가
]


SITE_IDE = 1 # <- 추가
```

SITE_ID 정수값은 django_site 데이터베이스 테이블에 있는 현재 사이트의 값이다. django_site 테이블에 여러 개의 사이트를 등록하고 그 중 하나를 지정하는 역할을 한다.

### `django_site` 테이블 생성 ###

`django_site` 테이블을 만들기 위해 `makemigrations` 필요 없이 바로 `migrate` 명령한다.

```
python manage.py migrate
```

### 사이트 도메인과 이름 변경

사이트 도메인과 이름 기본값이 `example.com`이다. 이를 파이썬 콘솔에서 아래와 같이 변경할 수 있다.

```
from django.contrib.sites.models import Site
mysite = Site.objects.get_current()
mysite.domain = 'my-site.com'
mysite.name = 'My site powered by Django'
mysite.save()
```

개발 환경에서는 `my-site.com` 같은 도메인 주소가 아닌 `127.0.0.1:8000` 같이 아이피주소:포트번호로 지정할 수 있다.
또한 콘솔이 아닌 admin site에서도 편리하게 수정할 수 있다.