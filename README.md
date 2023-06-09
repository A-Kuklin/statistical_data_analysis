# Исследование тарифов
  * [Описание исследования](#Описание-исследования)
  * [Описание тарифов](#Описание-тарифов)
  * [Описание данных](#Описание-данных)
  * [Общий вывод](#Общий-вывод)
## Описание исследования
Заказчик — федеральный оператор сотовой связи «Мегалайн».<br>
Предмет исследования два тарифных плана: «Смарт» и «Ультра».<br>
Предстоит сделать предварительный анализ тарифов на небольшой выборке клиентов.<br>
Проанализируем поведение клиентов и сделаем вывод — какой тариф лучше.

## Описание тарифов
* **Тариф «Смарт»**<br>
   Ежемесячная плата: 550 рублей<br>
   Включено 500 минут разговора, 50 сообщений и 15 Гб интернет-трафика<br>
   Стоимость услуг сверх тарифного пакета:<br>
   - минута разговора: 3 рубля
   - сообщение: 3 рубля
   - 1 Гб интернет-трафика: 200 рублей<br><br>
* **Тариф «Ультра»**<br>
   Ежемесячная плата: 1950 рублей<br>
   Включено 3000 минут разговора, 1000 сообщений и 30 Гб интернет-трафика<br>
   Стоимость услуг сверх тарифного пакета:<br>
   - минута разговора: 1 рубль
   - сообщение: 1 рубль
   - 1 Гб интернет-трафика: 150 рублей

Справочно: «Мегалайн» всегда округляет секунды до минут, а мегабайты — до гигабайт.

## Описание данных
* calls
  - `id` — 'уникальный номер звонка',
  - `call_date` — 'дата звонка',
  - `duration` — 'длительность звонка в минутах',
  - `user_id` — 'идентификатор пользователя, сделавшего звонок',
* internet 
  - `id` — уникальный номер сессии,
  - `mb_used` — объём потраченного за сессию интернет-трафика (в мегабайтах),
  - `session_date` — дата интернет-сессии,
  - `user_id` — идентификатор пользователя,
* messages
  - `id` — уникальный номер сообщения,
  - `message_date` — дата сообщения,
  - `user_id` — идентификатор пользователя, отправившего сообщение,
* tariffs
  - `tariff_name` — название тарифа,
  - `rub_monthly_fee` — ежемесячная абонентская плата в рублях,
  - `minutes_included` — количество минут разговора в месяц, включённых в абонентскую плату,
  - `messages_included` — количество сообщений в месяц, включённых в абонентскую плату,
  - `mb_per_month_included` — объём интернет-трафика, включённого в абонентскую плату (в мегабайтах),
  - `rub_per_minute` — стоимость минуты разговора сверх тарифного пакета,
  - `rub_per_message` — стоимость отправки сообщения сверх тарифного пакета,
  - `rub_per_gb` — стоимость дополнительного гигабайта интернет-трафика сверх тарифного пакета,
* users
  - `user_id` — уникальный идентификатор пользователя,
  - `first_name` — имя пользователя,
  - `last_name` — фамилия пользователя,
  - `age` — возраст пользователя (годы),
  - `reg_date` — дата подключения тарифа (день, месяц, год),
  - `churn_date` — дата прекращения пользования тарифом (если значение пропущено, то тариф ещё действовал на момент выгрузки данных),
  - `city` — город проживания пользователя,
  - `tariff` — название тарифного плана

## Общий вывод
* Медианная выручка тарифа «Ультра» больше, чем выручка тарифа «Смарт» (2061 руб. > 1337 руб.)
* Клиенты тарифа «Ультра» не «выбирают» полностью пакеты услуг по звонкам и по сообщениям,
   и основная масса не перерасходует лимит по трафику.
* Большинство клиентов тарифа «Смарт» превышают лимиты пакетов услуг.
* Клиентов тарифа «Смарт» практически в два раза больше клиентов «Ультра».
* Cредняя выручка пользователей из Москвы не отличается от выручки пользователей из других регионов.
* Тариф «Ультра» более выгоден, исходя из того, что клиенты «Ультра» не перерасходуют лимиты по пакетам услуг и при этом выручка больше, чем по тарифу «Смарт».
* Возраст, дата подключения тарифа и дата отключения таблицы `users` не понадобились для анализа.
***
_Работа над проектом велась в PyCharm 2021.3.2 (Professional Edition)_<br>
_формат ячеек Markdown различается в веб-версии и в PyCharm_