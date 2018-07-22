# Djangoアプリ作成メモ
基本的にはここに従ってやってみる。
<https://docs.djangoproject.com/ja/2.0/intro/>

## インストールする
ターミナルからこのコマンドを実行する。
`pip install Django`

インストールできたことを確認する。
```
MacBook:workspace tani$ python
Python 3.6.5 |Anaconda, Inc.| (default, Apr 26 2018, 08:42:37)
[GCC 4.2.1 Compatible Clang 4.0.1 (tags/RELEASE_401/final)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import django
>>> print(django.get_version())
2.0.7
```
pythonから抜けるには、control+D。

## プロジェクトを作成する
このコマンドでmysiteプロジェクトを作成できる。
作る場所にcdしてから実行する。
```
$ cd documents/workspace/
$ django-admin startproject mysite
$ ls -al mysite
total 8
drwxr-xr-x  4 tani  staff  128  7 21 17:02 .
drwxr-xr-x  6 tani  staff  192  7 21 17:02 ..
-rwxr-xr-x  1 tani  staff  538  7 21 17:02 manage.py
drwxr-xr-x  6 tani  staff  192  7 21 17:02 mysite
$ ls -al mysite/mysite/
total 24
drwxr-xr-x  6 tani  staff   192  7 21 17:02 .
drwxr-xr-x  4 tani  staff   128  7 21 17:02 ..
-rw-r--r--  1 tani  staff     0  7 21 17:02 __init__.py
-rw-r--r--  1 tani  staff  3088  7 21 17:02 settings.py
-rw-r--r--  1 tani  staff   748  7 21 17:02 urls.py
-rw-r--r--  1 tani  staff   389  7 21 17:02 wsgi.py
```

## 開発用サーバーの起動
このコマンドで開発サーバが立ち上がる。
```
$ cd mysite/
$ python manage.py runserver
Performing system checks...

System check identified no issues (0 silenced).

You have 14 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.

July 21, 2018 - 08:07:02
Django version 2.0.7, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

<http://127.0.0.1:8000/>にアクセスすると、ロケットが飛んでる画面が出た。

## アプリケーション作成
これでpollsアプリケーションを作成できる。
```
$ python manage.py startapp polls
```

##　DBのマイグレート
これでDBをマイグレートできる。
modelクラスを作ってから実行する。
```
$ python manage.py makemigrations polls
$ python manage.py migrate
```

## settings.pyの変更
作成したアプリケーションを追加する。
```
INSTALLED_APPS = [
    # 作成したアプリケーションの名前に応じて変わる。
    'polls.apps.PollsConfig',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

言語とタイムゾーンの設定を変更する。
```
# LANGUAGE_CODE = 'en-us'
LANGUAGE_CODE = 'ja'

# TIME_ZONE = 'UTC'
TIME_ZONE = 'Asia/Tokyo'

# USE_TZ = True
USE_TZ = False

```

## 管理ユーザの作成
管理サイトにログインする管理ユーザを作成する。
ユーザ名、メールアドレス、パスワード（２回）を入力する。
```
$ python manage.py createsuperuser
```

##　CSSフレームワークの選定
どれにしようか。。。
    - <http://chinpui.net/?p=676>
