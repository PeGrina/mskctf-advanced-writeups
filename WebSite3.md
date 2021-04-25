# WebSite3

Заходя на сайт, видим 2 картинки на чёрном фоне, одна из них означает космос другая ветвь. Это намекает на дерево git. Проверим папку `.git`, действительно она там есть. Тогда сдампим её через git-dumper.
```bash
git-dumper http://web.ctf.msk.ru/ctn2021/advancedquals/WebSite3/.git/ WebSite3
```
Зайдя в директорию с сдампленным проектом, видим login.php, смотря код видим следующее:
```php
<?php
  require_once "config.php";
?>
```
Следовательно, где-то затерялся ещё один файл с конфигом, хорошо, посмотрим остальной код. Видим обычную авторизацию после верновведёных полей которой получим флаг. Но вот username и password находятся в потерянном `config.php`. Тогда время применять git:
```bash
git log
```
Видим все коммиты:
`
commit 3adab4d59f5951e0471435643a45d138795efedc (HEAD -> master)
Make body black

commit 0582e6c14506689b7d7dc94df34376270701c7d7
Add login form

commit b8dfe2717dc0a632ecd9db2cea2eaa5d01fa5b06
Remove config

commit 2dd7285b2877ef9a3a5a18eb7bd7970c15c9dd90
Add config

commit 341d580b5959b9f8a30b3ee31dbf61d6eb4dc940
Add Static
`
Нам интересен коммит добавления конфига, поэтому прописываем команду: `git show 2dd7285b2877ef9a3a5a18eb7bd7970c15c9dd90`
И получаем код конфига:
```php
<?php
  $username = "testuser";
  $testpassword = "e9e633097ab9ceb3e48ec3f70ee2beba41d05d5420efee5da85f97d97005727587fda33ef4ff2322088f4c79e8133cc9cd9f3512f4d3a303cbdb5bc585415a00";
?>
```
Пароль можно посмотреть через декриптор  (из `login.php` узнаём, что это `sha512`), получаем пароль `testpassword`
Логинимся с username и password `testuser` и `testpassword` соответственно и получаем флаг:

Flag: `CYBERTHON{83_4W433_0F_9i7}`
