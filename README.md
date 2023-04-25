# python_app

### セットアップ
```
sudo apt install python
python -V
> Python 3.10.6
pip --version
> pip 23.1 from /usr/local/lib/python3.10/dist-packages/pip (python 3.10)

pip install Flask
pip install pipenv

pipenv --version
> pipenv, version 2023.3.20
```

### パッケージ一覧
```
pipenv graph
Flask-Login==0.5.0
  - Flask [required: Any, installed: 1.1.2]
    - click [required: >=5.1, installed: 8.1.3]
    - itsdangerous [required: >=0.24, installed: 1.1.0]
    - Jinja2 [required: >=2.10.1, installed: 2.11.3]
      - MarkupSafe [required: >=0.23, installed: 1.1.1]
    - Werkzeug [required: >=0.15, installed: 0.16.1]
Flask-Script==2.0.6
  - Flask [required: Any, installed: 1.1.2]
    - click [required: >=5.1, installed: 8.1.3]
    - itsdangerous [required: >=0.24, installed: 1.1.0]
    - Jinja2 [required: >=2.10.1, installed: 2.11.3]
      - MarkupSafe [required: >=0.23, installed: 1.1.1]
    - Werkzeug [required: >=0.15, installed: 0.16.1]
Flask-SQLAlchemy==2.5.1
  - Flask [required: >=0.10, installed: 1.1.2]
    - click [required: >=5.1, installed: 8.1.3]
    - itsdangerous [required: >=0.24, installed: 1.1.0]
    - Jinja2 [required: >=2.10.1, installed: 2.11.3]
      - MarkupSafe [required: >=0.23, installed: 1.1.1]
    - Werkzeug [required: >=0.15, installed: 0.16.1]
  - SQLAlchemy [required: >=0.8.0, installed: 1.4.47]
    - greenlet [required: !=0.4.17, installed: 2.0.2]
typing-extensions==4.5.0
```

### DB初期化
```
pipenv run python manage.py init_db
```

### 起動
```
pipenv shell
FLASK_APP=flask_blog flask run
```
