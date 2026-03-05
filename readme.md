alembic==1.17.2
bcrypt==5.0.0
blinker==1.9.0
certifi==2026.1.4
charset-normalizer==3.4.4
click==8.3.1
colorama==0.4.6
coloredlogs==15.0.1
contourpy==1.3.0
cycler==0.12.1
dnspython==2.8.0
email-validator==2.3.0
filelock==3.20.3
Flask==3.1.2
Flask-Bcrypt==1.0.1
Flask-Login==0.6.3
Flask-Migrate==4.1.0
Flask-SQLAlchemy==3.1.1
Flask-WTF==1.2.2
flatbuffers==25.2.10
fonttools==4.56.0
fsspec==2025.3.0
greenlet==3.1.1
humanfriendly==10.0
idna==3.11
itsdangerous==2.2.0
Jinja2==3.1.6
kiwisolver==1.4.7
Mako==1.3.10
MarkupSafe==3.0.2
matplotlib==3.9.4
mpmath==1.3.0
networkx==3.4.2
numpy==1.26.4
onnxruntime==1.23.0
opencv-python==4.10.0.84
packaging==25.0
pillow==11.2.1
polars==1.37.0
protobuf==6.31.0
psutil==7.0.0
pyparsing==3.2.3
pyreadline3==3.5.4
python-dateutil==2.9.0.post0
python-dotenv==1.1.0
PyYAML==6.0.2
requests==2.32.3
scipy==1.13.1
six==1.17.0
SQLAlchemy==2.0.40
sympy==1.14.0
typing_extensions==4.12.2
ultralytics-thop==2.0.18
urllib3==2.3.0
Werkzeug==3.1.3
WTForms==3.2.1



# 1. Préparer le système
sudo apt update && sudo apt upgrade -y
sudo apt install python3-pip python3-venv libopenblas-dev libjpeg-dev libtiff-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libxvidcore-dev libx264-dev

# 2. Créer et activer l’environnement virtuel
python3 -m venv venv
source venv/bin/activate

# 3. Configurer pip pour piwheels
pip install --upgrade pip
pip config set global.extra-index-url https://www.piwheels.org/simple

# 4. Installer les dépendances (sauf torch)
pip install -r requirements.txt

# 5. Installer PyTorch et Torchvision (exemple pour Python 3.11 sur ARM64)
pip install https://github.com/KumaTea/pytorch-arm64/releases/download/v2.1.2/torch-2.1.2-cp311-cp311-linux_aarch64.whl
pip install https://github.com/KumaTea/pytorch-arm64/releases/download/v2.1.2/torchvision-0.16.2-cp311-cp311-linux_aarch64.whl

# 6. Vérifier l’installation
python -c "import torch; print(torch.__version__)"-