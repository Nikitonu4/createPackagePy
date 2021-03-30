# Установка нужных версий интерпретатора, установка зависимостей и запуск Python-приложений.


## Подготовка к работе

```sh
sudo apt updatе 
sudo apt install build-essential git vim tree wget # необходимый инструментарий
sudo apt install  zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev libssl-dev 
libreadline-gplv2-dev libncursesw5-dev tk-dev libc6-dev libffi-dev # библиотеки
```

Клонирование инструмента контроля версий Python

```sh
git clone https://github.com/pyenv/pyenv.git $HOME/.pyenv
vim $HOME/.bashrc 
```
Меняем последнюю строчку в файле на 
```sh
## pyenv configs export PYENV_ROOT="$HOME/.pyenv" export PATH="$PYENV_ROOT/bin:$PATH" if command -v pyenv 1>/dev/null 2>&1; then eval "$(pyenv init -)" fi
```

Обновляем shell оболочку
```sh
exec "$SHELL"
```
## Установка нужной версии интерпретатора
 
```sh
pyenv install 3.9.2
```
Установка конкретной версии в проект
```sh
pyenv local 3.9.2
```

Обновляем pip

```sh
python -m pip install --upgrade pip
```

## Устанавливаем virtualenv
```sc
sudo pip install virtualenv
```
Создаем окружение в проекте
```sc
virtualenv venv
```
Активируем окружение
```sc
. venv/bin/activate
```

## Устанавливаем инструмент сборки setuptools
```sc
pip install setuptools
```
Собираем проект в папку dist
```sc
python setup.py sdist
```
Пример setup.py:
```py
import os
from setuptools import setup

with open(os.path.join(os.path.dirname(__file__), 'README.md')) as readme:
    README = readme.read()

# allow setup.py to be run from any path
os.chdir(os.path.normpath(os.path.join(os.path.abspath(__file__), os.pardir)))

setup(
    name='project',
    version='0.1',
    packages=['Django'],
    include_package_data=True,
    license='BSD License',  # example license
    description='A simple Django app to conduct Web-based polls.',
    long_description=README,
    url='http://www.example.com/',
    author='Your Name',
    author_email='yourname@example.com',
    classifiers=[
        'Environment :: Web Environment',
        'Framework :: Django',
        'Intended Audience :: Developers',
        'License :: OSI Approved :: BSD License', # example license
        'Operating System :: OS Independent',
        'Programming Language :: Python',
        # Replace these appropriately if you are stuck on Python 2.
        'Programming Language :: Python :: 3',
        'Programming Language :: Python :: 3.2',
        'Programming Language :: Python :: 3.3',
        'Topic :: Internet :: WWW/HTTP',
        'Topic :: Internet :: WWW/HTTP :: Dynamic Content',
    ],
)
```
## Установка собранного проекта
```sc
pip install path/to/packageName.tar.gz
```
