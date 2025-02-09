# Stalkee
*Хабар принёс?*

> Бот [Telegram](https://telegram.org), сохраняющий голосовые сообщения, заданные администратором, и отправляющий их по инлайн запросам с сортировкой по числу использований.

![](https://img.shields.io/tokei/lines/github/arebaka/stalkee)
![](https://img.shields.io/github/repo-size/arebaka/stalkee)
![](https://img.shields.io/npm/v/stalkee)
![](https://img.shields.io/codefactor/grade/github/arebaka/stalkee)

![](https://img.shields.io/badge/Russian-100%25-brightgreen)

![тут должен быть скриншот инлайн запроса, но куда то делся](https://user-images.githubusercontent.com/36796676/127343858-474b275f-ab45-4a23-9c96-b118f4d389d1.png)

## TLDR
1. Создай и настрой бота через [@BotFather](https://t.me/BotFather)
2. Установи [Docker](https://www.docker.com), если не стоит
3. Скачай репозиторий
4. Установи переменные окружения в .env
5. `docker-compose up -d`
6. Кидай своему боту голосовые и отвечай на них одиночными сообщениями в таком формате:
   > `/add` <РЕПЛИКА>
7.  Для удаления добавленной реплики ответь на голосовое с ней командой `/remove`

## Подготовка без Docker
1. Создай бота через [@BotFather](https://t.me/BotFather), все инструкции он выдаёт сам, получи токен
2. Бот использует СУБД PostgreSQL. [Установи](https://www.postgresql.org/download/), если у тебя её нет
3. Создай базу данных в PSQL для своего бота
4. Бот работает на [node.js](https://npmjs.com/package/node), используя менеджер пакетов [npm](https://www.npmjs.com). Установи их
5. Узнай свой Telegram ID с помощью любого специального бота, например, [этого](https://t.me/myidbot)

## Установка без Docker
```bash
npm i stalkee
```

## Запуск без Docker
Для запуска бота нужны переменные окружения, их можно задать через оболочку или прописать в файле .env  
Вот их список:

- `BOT_TOKEN` – токен бота от @BotFather
- `BOT_ADMIN` – Telegram ID-ы админов бота через пробел, они будут иметь доступ к редактированию базы реплик; может состоять всего из одного ID
- `DATABASE_URI` – URI-строка для подключения к PSQL в формате `postgres://<USER>:<PASSWORD>@<HOST>/<DATABASE>:<PORT>`

Вместо задания параметров через переменные окружения можно прописать их в файле `config.toml`.
Но тогда следи за сохранностью своих секретов.

После задания окружения выполни
```bash
npx stalkee
```

Если всё прошло успешно, ты увидишь в консоли что то вроде этого:
```
> stalkee@1.2.0 start
> node index.js

Bot @stalkeeBot started.
> _
```
 
https://heroku.com/deploy?template=https://github.com/Islam766/stalkee


## Управление
После запуска в консоли доступны команды  
`stop` и `reload` для безопасных остановки и перезагрузки соответственно, а также  
`mode edit` для включения команд `/add` и `/remove` в список подсказок для удобного редактирования реплик, и  
`mode regular` для выключения.

Редактирование осуществляется через общение с ботом в Telegram. Админам (тем, чьи ID прописаны в окружении) доступны следующие команды:

**Добавление голосового сообщения в результаты инлайна**
> `/add <РЕПЛИКА>`

**Удаление голосового сообщения из результатов**
> `/remove`

Командами необходимо ответить на голосовое сообщение, которое и будет добавлено/удалено.

## Поддержка
Если у тебя что то не получается, или ты просто хочешь поговорить с создателем бота или его мамой, пиши [@arelive](https://t.me/arelive). Сюда же принимаются пинки от добровольных проект-менеджеров.
