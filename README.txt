Информация с официального сайта

sensorsOnDevice - запрос списка датчиков и их показаний по ID устр-ва мониторинга.

- id ID устр-ва из ссылки вида http://narodmon.ru/ID в балуне на карте;
- trends = 1, необязательный параметр включающий расчет тендеции показаний;
- lang язык интерфейса приложения ISO 639-1 ("ru","en","uk").
ОТВЕТ сервера:
- id ID устройства в проекте;
- mac серийный номер устройства (только для владельца);
- name название устройства или его ID (если нет названия);
- my = 1, если это устр-во авторизованного пользователя, иначе = 0;
- owner ID владельца устройства в проекте;
- location местонахождение устройства, населенный пункт или область;
- distance расстояние в км от текущего местонахождения пользователя;
- liked количество положительных отзывов пользователей;
- sensors массив датчиков подключенных к указанному устр-ву;
- sensors[id] целочисленный код датчика в проекте;
- sensors[pub] = 1, если датчик публичный и = 0, если датчик приватный;
- sensors[type] код типа датчика (см. appInit);
- sensors[name] название датчика или его ID (если нет названия);
- sensors[value] последнее показание датчика;
- sensors[unit] единица измерения;
- sensors[time] время последнего показания датчика в UnixTime;
- sensors[changed] время последнего изменения показаний датчика в UnixTime;
- sensors[trend] коэффициент линейного роста показаний датчика за последний час, рассчитанный по МНК.
Пример запроса REST(GET):
http://narodmon.ru/api/sensorsOnDevice?id=5699&uuid=UUID&api_key=API_KEY&lang=ru
Пример запроса JSON(POST):
{"cmd":"sensorsOnDevice","id":5699,"uuid":"UUID","api_key":"API_KEY","lang":"ru"}
Ответ сервера:
{"id":5699,"mac":"","name":"Small Meteo v2","my":0,"owner":"rzhev69ru","location":"\u0443\u043b.\u041d\u0438\u043a\u0438\u0442\u044b \u0413\u043e\u043b\u043e\u0432\u043d\u0438, 5\/47, \u0420\u0436\u0435\u0432","distance":212.63,"liked":746,"sensors":
[{"id":15685,"pub":1,"type":3,"name":"\u0414\u0430\u0432\u043b\u0435\u043d\u0438\u0435","value":744.65,"unit":"mmHg","time":1453378180,"changed":1453378180,"trend":0},{"id":15684,"pub":1,"type":1,"name":"\u0423\u043b\u0438\u0446\u0430","value":-8.1,"unit":"\u00b0","time":1453378180,"changed":1453378180,"trend":0},
{"id":15689,"pub":1,"type":2,"name":"\u0423\u043b\u0438\u0446\u0430","value":79,"unit":"%","time":1453378180,"changed":1453378180,"trend":0}]}

userLogon - авторизация пользователя в проекте и его регистрация.

- login логин пользователя для авторизации, если он не указан, то возвращается текущий логин для uuid;
- hash хэш для авторизации, вычисляется как MD5(uuid + MD5(введенный пароль)), если он не указан, то считается запросом на регистрацию в проекте по email / sms;
- lang язык интерфейса приложения ISO 639-1 ("ru","en","uk").
ОТВЕТ сервера:
- login имя авторизованного пользователя для текущего uuid или пустая строка;
- vip = 1 признак партнера, донатора, разработчика, администрации, для остальных = 0.
Пример запроса REST(GET):
http://narodmon.ru/api/userLogon?login=MYNAME&hash=MD5HASH&uuid=UUID&api_key=API_KEY&lang=ru
Пример запроса JSON(POST):
{"cmd":"userLogon","login":"MYNAME","hash":"MD5HASH","uuid":"UUID","api_key":"API_KEY","lang":"ru"}
Ответ сервера:
{"login":"MyName","vip":0}
