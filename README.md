# DLE-UniForm
![version](https://img.shields.io/badge/version-0.3-red.svg?style=flat-square "Version")
![DLE](https://img.shields.io/badge/DLE-10.X-green.svg?style=flat-square "DLE Version")
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](https://github.com/pafnuty/DLE-UniForm/blob/master/LICENSE)

## Описание
DLE-UniForm — простой модуль универсальных форм.

Пока модуль можно использовать как простую форму обратной связи т.к. не до конца ясна востребованность сего творения.

## Преимущества
- Не использует БД.
- Лёгкость настройки.
- Скорость работы.
- AJAX вызов и отправка форм (а знчаит бот не сможет спамить).
- Шаблоны email-сообщений в .tpl файлах.

## Установка
- Распаковать содержимое папки **upload** в корень сайта.
- Открыть **{THEME}/main.tpl** и в нужном месте, перед закрывающим тегом `</head>` вставить подключение стилей и скриптов модуля:
```html
<!-- DLE UniForm -->
<link rel="stylesheet" href="/engine/classes/min/index.php?charset=utf-8&amp;f={THEME}/uniform/css/uniform.css&amp;01" />
<script type="text/javascript" src="/engine/classes/min/index.php?charset=utf-8&amp;f={THEME}/uniform/js/jquery.magnificpopup.min.js,{THEME}/uniform/js/jquery.ladda.min.js,{THEME}/uniform/js/jquery.form.min.js,{THEME}/uniform/js/uniform.js&amp;01"></script>
<!-- /DLE UniForm -->
```
- Далее в нужном шаблоне, в нужном месте вставить кнопку вызова ajax-окна формы:
```html
<span class="uf-btn" data-uf-open="/engine/ajax/uniform/uniform.php" data-uf-settings='{"formConfig": "feedback"}'>Обратная связь</span>
```
где **feedback** — Папка с шаблонами формы формы, указывается подпапка, в папке uniform текущего шаблона сайта сайта (feedback), в которой должны лежать файлы config.tpl, form.tpl и email.tpl

Если всё прошло удачно — при нажатии на кнопку вы увидите такую форму:
![UniForm](https://dl.dropboxusercontent.com/u/8142395/uniform.png "UniForm")

## Настройка
- Описание и примеры параметров формы можно найти в файле **{THEME}/uniform/test/form.tpl**.
- Описание и примеры параметров email-сообщения можно найти в файле **{THEME}/uniform/callback/email.tpl**.

В форму можно передавать дополнительные данные со страницы через атрибут `data-uf-settings`. Например так:
```html
<span data-uf-open="/engine/ajax/uniform/uniform.php" data-uf-settings='{"formConfig": "feedback", "fields":{"newsid": "56", "user": "ПафНутиЙ"}}'>Обратная связь</span>
```
При этом в файле конфига формы нужно указать ключи, которые будут добавлены к форме в виде скрытых полей `hidden = newsid,user` (и в последствии отправятся на email, если требуется).

Если в качестве обязательного поля указан ключ `email` — такое поле будет проверено на соответствие email-адресу (наличие знака @ и точки).


