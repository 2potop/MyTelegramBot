# MyTelegramBot
Простой телеграмм бот на питоне

Боты это сторонние приложения которые работают внутри телеграмма.
Это специальный аккаунт которым управляет программа вместо человека.


Боты могут выполнять следующие функции:
    1) Присылать оповещения и новости.
    2) Присылать информацию в общие чаты 
    3) Принимать платежи
    4) Создавать HTML игры 
    5) Перевод текста и многое другое

Бот запускается на сервере разработчика. Чтобы отправить сообщение пользователю, бот делает HTTP-запрос к серверу телеграмма передавая JSON с сообщением и идентификатор пользователя. Как только Пользователь отправил сообщение боту, сообщение попадает на сервер телеграмм. Из сервера телеграмм сообщение боту может попасть 2 путями:

    Webhooks — суть проста, вы на своем сервере создаете API, при настройке бота указываете адрес этого API как адрес, куда        Telegram должен присылать сообщения пользователей. 
    Как только пользователь пишет боту, бэкенд Telegram'а пересылает JSON с сообщением на ваш API. То есть hook это и есть API по которому другие системы (в данном случает Telegram), уведомляют вашу систему (в данном случает вашего бота) о событиях (о том, что пользователь отправил боту сообщение).

    Long-polling — бот сам периодически отправляет HTTP запросы к серверам Telegram'а, чтобы узнать нет ли новых сообщений. Если есть, Telegram отдает боту JSON с массивом этих сообщений. Каждый раз делая запрос, бот передает Telegram'у номер (на англ. offset — смещение) последнего полученного сообщения, чтобы не получить одно и то же сообщение 2 раза. Например, при первом запросе бот получил 5 сообщений с номерами [1, 2, 3, 4, 5]. В следующий раз бот передает идентификатор 6, говоря, что первые 5 уже получил, теперь готов обрабатывать 6-е и далее.

    