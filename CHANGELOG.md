# Change Log
Все заметные изменения в проекте будут описаны в этом файле

## Планируется
- Сделать обработку двухфакторной авторизации standalone и приложений официальных (возможно)

## [3.1.1] - 07.04.2017
### Добавлено
- Добавлено упущенное описание в README.md
- Добавлен режим вызова API через `execute`
- Добавлены методы для события Long Poll `message` (`sendSticker`, `sendPhoto`, `setActivity`, `reply`)
- В тесты добавлена проверка парсинга ошибок
- Добавлены примеры

### Удалено
- Удалена зависимость `entities`
- Удалён метод `messages.sendSticker`

## [3.1.0] - 07.04.2017
### Добавлено
- Перечитайте файл README.md

### Исправлено
- Модуль полностью переписан с нуля
- Метод setCaptchaHandler поменял порядок аргументов
- Работа с коллекциями изменена

### Удалено
- Удалена проверка на массив attachment в методе messages.send

## [3.0.0] - 10.02.2017
### Добавлено
- Добавлены тесты, `npm test` для расширенного текста необходимо вставить полный токен в `test.js`, [подробнее](https://github.com/negezor/vk-io#Тесты)

### Испралвено
- Исправлен код в `.chain()` и `.executes()` который приводил к ошибке
- Лёгкий рефакторинг и оптимизация

## [2.2.9] - 09.02.2017
### Добавлено
- Добавлены серверные методы `secure.*` для их использования нужен ключ в настройках `key`
- Добавлена авторизация для серверных приложений `appAuth`
- Добавлены методы для `message` в longpoll, `hasAttachments()`, `hasAttachment()`, `hasFwd()`, `getFwd()`, `isDialog()`, `isChat()`, `isGroup()`
- Добавлены настройки `restartError`, `restartCount` для рестарта методов с ошибкой

### Исправлено
- Полный рефакторинг с расчётом на производительности обработки longpoll

### Удалено
- Удалено свойство `fwd` в параметрых метода `send` longpoll
- Удалено событие `message.gift` используйте `message.hasAttachment('gift')`
- Удалено событие `message.money` используйте `message.hasAttachment('money')`
- Удалено событие `message.sticker` используйте `message.hasAttachment('sticker')`
- Удалено свойство `isChat` в `message` longpoll, используйте `message.from === 'chat'` или `message.isChat()`

## [2.2.8] - 11-01-2017
### Добавлено
- Добавлен метод `messages.getHistoryAttachments`

### Исправлено
- Обновлена версия API до `5.62`
- Исправлены ошибки в `standalone` авторизации
- Событие `unread.count` теперь снова возвращает объект
- Событие `typing.user` теперь снова возвращает объект
- В longpoll не будут обрабатываться события на которые не установлены обработчики
- В `message` изменено свойство `attach` на `attachments`

### Удалено
- Удалено свойство из настроек `ignoreMe`
- Проверка сообщения написанные собой

## [2.2.7] - 01-01.2017
### Исправлено
- Переименовано название платформы `web` на `standalone` в `user.online`
- Переименовано событие `message.flags.reset` в `message.flags.remove`
- Переименовано событие `group.flags.reset` в `group.flags.remove`
- Событие `unread.count` теперь возвращает число вместо объекта
- Событие `typing.user` теперь возвращает ID пользователя
- Рефакторинг longpoll под производительность
- Необрабатываемые обработчики капчи

## Удалено
- Удалены события `user.call`, `message.flags.replace`, `group.flags.replace`

## [2.2.6] - 18-12-2016
### Исправлено
- Обновлён обход ввода номера телефона в standalone авторизации
- Переписана очередь методов под производительность
- Увеличена скорость работы `stream`
- Лёгкий рефакторинг кода

### Удалено
- Статистика модуля

## [2.2.5] - 17-12-2016
### Исправлено
- Исправлена авторизация standalone
- Исправлен `getAttachment` с передачей массива
- Исправлен вызов `.catch` при отсутствии обработчика капчи

## [2.2.4] - 05-12-2016
### Исправлено
- Объект вызова `execute` в `stream.js`

## [2.2.3] - 03-12-2016
### Добавлено
- Добавлены методы для получение ссылки на фотографию `getLargePhoto`,`getMediumPhoto`,`getSmallPhoto`
- Добавлен метод для получения прикрипления `getAttachment`
- В обработчик `setCaptchaHandler` теперь передаётся последним параметром sid
- Добавлен класс/метод `chain` для удобной работы с execute

### Исправлено
- Метод авторизации `standloneAuth` переименован в `standaloneAuth`
- Исправлена утечка памяти связанная с `arguments`
- Отрефакторен код в некоторых местах
- Обновлено README.md

### Удалено
- Удалён метод `getQueueMessages`
- Удалено свойство `messages` в `vk.status`

## [2.2.2] - 12-11-2016
### Добавлено
- Новый метод `executes` для мультивызова методов
- Метод `gifts.send`
- Прокси

### Исправлено
- Отрефакторен код в некоторых местах
- Обновлены зависимости
- Обновлена версия API
- Параметр attach у message переименован в attachment

## [2.2.0] - 18-10-2016
### Добавлено
- Начался ввестись Change Log
- Добавлена обработка longpoll (подарков, переводов, стикеров)
- Новые методы «Подписка на сообщения сообщества»
- Добавлены методы для работы с рекламным кабинетом

### Исправлено
- Теперь отправляются большие запросы
- Теперь longpoll не будет падать от (ETIMEDOUT, ENOENT)
- Небольшие оптимизации в модуле
- Обновлена версия API
