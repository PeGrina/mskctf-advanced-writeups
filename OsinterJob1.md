# OsinterJob1

Сразу же, видя ник, пробиваем его в namechk.com. Получаем гитхаб github.com/Shimmer088 и репозиторий с проектом. В репозитории находим файл setup.py со следующим содержим:
```python
import setuptools

with open("README.md", "r", encoding="utf-8") as fh:
    long_description = fh.read()

setuptools.setup(
    name="simple-backend-app",
    version="0.0.1",
    author="Shimmer088",
    author_email="sfbaui@uzanet.ru",
    description="A small example backend app",
    long_description=long_description,
    long_description_content_type="text/markdown",
    package_dir={"": "src"},
    packages=setuptools.find_packages(where="src"),
    python_requires=">=3.6",
)
```
Откуда видем почту `sfbaui@uzanet.ru`. Из хинтов узнаём, что Shimmer любит 'общаться' и делает это в популярном сервисе microsoft, намёк был на skype, ищем юзера с данной почтой и видим в имени флаг (ну либо просто ищем юзера с ником CYBERTHON)
![alt skype](https://i.ibb.co/ftM4NXN/Zkm-DLZ-0m-Z0.jpg)

Flag: `CYBERTHON{se3cH_eve3yWhe3e}`
