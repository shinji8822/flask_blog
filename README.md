# python_app

### セットアップ
```
sudo apt install python
python -V
> Python 3.10.6

pip --version
> pip 23.1 from /usr/local/lib/python3.10/dist-packages/pip (python 3.10)

pip install Flask
python -c "import flask; print( flask.__version__ )"
> 2.2.3

pip install pipenv
pipenv --version
> pipenv, version 2023.3.20

```

### 依存関係
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
export FLASK_APP=flask_blog 
/home/shinji/.local/bin/pipenv run flask run --host 0.0.0.0 --port 8000
```

### systemdサービス登録
```
cat <<'EOF | sudo tee /etc/systemd/system/flask-flask_blog.service
[Unit]
Description=Flask Web instance
After=network.target

[Service]
User=shinji
WorkingDirectory=/home/shinji/py/application
#Environment="PATH="
#Environment="FLASK_SECRET_KEY="
#Environment="FLASK_MYSQL_HOST="
#Environment="FLASK_MYSQL_USER="
#Environment="FLASK_MYSQL_PASSWORD="
#Environment="FLASK_MYSQL_DB="
#Environment="FLASK_DEBUG=1"
#Environment="TEMPLATES_AUTO_RELOAD=1"
Environment="FLASK_APP=flask_blog"
ExecStart=/home/shinji/.local/bin/pipenv run flask run --host 0.0.0.0 --port 8000

[Install]
WantedBy=multi-user.
EOF

sudo systemctl daemon-reload
sudo systemctl start flask-flask_blog
sudo systemctl status flask-flask_blog
● flask-flask_blog.service - Flask Web instance
     Loaded: loaded (/etc/systemd/system/flask-flask_blog.service; disabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-12-25 17:26:47 JST; 2s ago
   Main PID: 24490 (flask)
      Tasks: 1 (limit: 9245)
     Memory: 32.3M
        CPU: 995ms
     CGroup: /system.slice/flask-flask_blog.service
             └─24490 /home/shinji/.local/share/virtualenvs/application-flT5KWh4/bin/python /home/shinji/.local/share/vi>

```
