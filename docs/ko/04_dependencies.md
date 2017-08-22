# 의존성 설치 패키지
* Django
    * pytz
* django-crispy-forms    
* django-allauth
    * certifi
    * chardet
    * defusedxml
    * idna
    * oauthlib
    * python3-openid
    * requests
    * requests-oauthlib
    * urllib3
    
# 추천 패키지
## 자료구조
* django-model-utils
* django-mptt

## CMS 및 커뮤니티
* wagtail

## 기타 유틸리티
* django-ipware
* Pillow

# `INSTALLED_APPS`

## 기본 목록

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

## 추가 목록

```python
INSTALLED_APPS = [
    'django.contrib.sites',
]
```