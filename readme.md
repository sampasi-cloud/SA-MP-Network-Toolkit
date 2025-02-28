# SA-MP-Network-Toolkit

Это набор инструментов, созданных для тех, кто хочет разобраться, как устроены пакеты и RPC в SA:MP. Здесь собрана подробная документация по каждому типу пакетов и RPC, а также скрипты, которые помогут вам провести эксперименты с их блокировкой и увидеть, что меняется в работе клиента и сервера.

## 👨‍💻 Автор

Yurii Krestovskiy

## 📋 Содержание

- [Описание](#описание)
- [Эффекты блокировки пакетов и RPC](#эффекты-блокировки-пакетов-и-rpc)
- [Скрипты](#скрипты)
- [Использование](#использование)

## 📝 Описание

Проект создан для исследователей, разработчиков и энтузиастов, интересующихся внутренней работой SA:MP. Здесь вы найдёте:

- Подробное описание каждого типа пакетов и RPC в SA:MP.
- Объяснение, что происходит, если заблокировать определённые пакеты или RPC.
- Lua-скрипты, позволяющие экспериментировать с блокировкой пакетов и RPC, чтобы на практике увидеть, как это влияет на работу клиента и сервера.

## 🔍 Эффекты блокировки пакетов и RPC

В SA:MP выделяются четыре основных типа взаимодействия:

- **incomingPacket (входящий пакет):** Данные, которые клиент получает от сервера. Блокировка этих пакетов может привести к тому, что обновления от сервера и информация от других игроков не будут доходить до клиента.
- **incomingRPC (входящий RPC):** Удалённые вызовы, отправляемые сервером клиенту. При их блокировке клиент не получит важные команды, что может нарушить корректное выполнение некоторых функций.
- **outcomingPacket (исходящий пакет):** Данные, отправляемые клиентом на сервер. Если заблокировать их, сервер не получит полную информацию о действиях клиента.
- **outcomingRPC (исходящий RPC):** Удалённые вызовы, которые клиент отправляет серверу. Блокировка этих вызовов ограничит возможности сервера корректно обработать команды, исходящие от клиента.

Подробное описание каждого типа пакетов и RPC, а также последствия их блокировки, представлено в файле [samp-packets-nop-effects.md](./samp-packets-nop-effects.md).

## 💻 Скрипты

В репозитории находятся следующие скрипты:

- **bypasser.lua** — скрипт для экспериментов с блокировкой пакетов и RPC.
- **syncer.lua** — инструмент для ложной отправки синхронизации данных.

## 🚀 Использование

### Скрипт Bypasser

1. Распакуйте архив `bypasser.zip` в папку moonloader.
2. Активируйте скрипт с помощью чит-кода **B + P**.

⚠️ **Важно:** Проект предназначен исключительно для образовательных целей. Пользуйтесь инструментами только на тех серверах, где у вас есть разрешение на эксперименты. Мы не несем ответственности за любое неправомерное использование данных инструментов.

# Эффекты блокировки пакетов и RPC в SA:MP

## Блокировка входящих пакетов (incomingPacket)
<details>
  <summary>Нажмите, чтобы раскрыть</summary>

  
- **PACKET_ADVERTISE_SYSTEM** - Не будешь видеть рекламные сообщения системы.
- **PACKET_AIM_SYNC** - Не будешь видеть, куда целятся другие игроки.
- **PACKET_AUTH_KEY** - Не сможешь пройти аутентификацию на сервере.
- **PACKET_BROADCAST_PINGS** - Не будешь получать информацию о пингах других игроков.
- **PACKET_BULLET_SYNC** - Не будешь видеть выстрелы других игроков.
- **PACKET_CONNECTED_PONG** - Сервер может решить, что ты отключился.
- **PACKET_CONNECTION_ATTEMPT_FAILED** - Не узнаешь, что попытка подключения не удалась.
- **PACKET_CONNECTION_BANNED** - Не узнаешь, что ты забанен на сервере.
- **PACKET_CONNECTION_COOKIE** - Не сможешь установить защищенное соединение.
- **PACKET_CONNECTION_LOST** - Не получишь уведомление о потере соединения.
- **PACKET_CONNECTION_REQUEST** - Не сможешь инициировать подключение.
- **PACKET_CONNECTION_REQUEST_ACCEPTED** - Не узнаешь, что запрос на подключение принят.
- **PACKET_DETECT_LOST_CONNECTIONS** - Сервер не сможет определить, что ты все еще онлайн.
- **PACKET_DISCONNECTION_NOTIFICATION** - Не получишь уведомление об отключении.
- **PACKET_INITIALIZE_ENCRYPTION** - Не сможешь настроить шифрование соединения.
- **PACKET_INTERNAL_PING** - Сервер может считать, что у тебя проблемы с соединением.
- **PACKET_INVALID_PASSWORD** - Не узнаешь, что ввел неверный пароль.
- **PACKET_MARKERS_SYNC** - Не будешь видеть маркеры на карте.
- **PACKET_MODIFIED_PACKET** - Не получишь уведомление о модифицированных пакетах.
- **PACKET_NEW_INCOMING_CONNECTION** - Не узнаешь о новых подключениях к серверу.
- **PACKET_NO_FREE_INCOMING_CONNECTIONS** - Не узнаешь, что сервер переполнен.
- **PACKET_OPEN_CONNECTION_REPLY** - Не сможешь завершить процесс открытия соединения.
- **PACKET_OPEN_CONNECTION_REQUEST** - Не сможешь запросить открытие соединения.
- **PACKET_PASSENGER_SYNC** - Не будешь видеть пассажиров в транспорте.
- **PACKET_PING** - Сервер не сможет проверить твою задержку.
- **PACKET_PING_OPEN_CONNECTIONS** - Не будешь получать пинги от сервера.
- **PACKET_PLAYER_SYNC** - Не будешь видеть перемещения других игроков.
- **PACKET_PONG** - Сервер может решить, что ты отключился.
- **PACKET_RCON_COMMAND** - Не сможешь отправлять RCON команды.
- **PACKET_RCON_RESPONSE** - Не будешь получать ответы на RCON команды.
- **PACKET_RECEIVED_STATIC_DATA** - Не получишь статические данные от сервера.
- **PACKET_REMOTE_CONNECTION_LOST** - Не узнаешь о потере соединения с другими игроками.
- **PACKET_REMOTE_DISCONNECTION_NOTIFICATION** - Не получишь уведомление об отключении других игроков.
- **PACKET_REMOTE_EXISTING_CONNECTION** - Не узнаешь о существующих соединениях.
- **PACKET_REMOTE_NEW_INCOMING_CONNECTION** - Не узнаешь о новых игроках на сервере.
- **PACKET_REMOTE_STATIC_DATA** - Не получишь удаленные статические данные.
- **PACKET_REQUEST_STATIC_DATA** - Не сможешь запросить статические данные.
- **PACKET_RPC** - Не будешь получать удаленные вызовы процедур.
- **PACKET_RPC_MAPPING** - Не сможешь получить отображение RPC.
- **PACKET_RPC_REPLY** - Не получишь ответы на RPC запросы.
- **PACKET_RSA_PUBLIC_KEY_MISMATCH** - Не узнаешь о несоответствии RSA ключа.
- **PACKET_SECURED_CONNECTION_CONFIRMATION** - Не сможешь подтвердить защищенное соединение.
- **PACKET_SECURED_CONNECTION_RESPONSE** - Не получишь ответ на запрос защищенного соединения.
- **PACKET_SET_RANDOM_NUMBER_SEED** - Не сможешь синхронизировать генератор случайных чисел с сервером.
- **PACKET_SPECTATOR_SYNC** - Не будешь видеть наблюдателей.
- **PACKET_STATS_UPDATE** - Не будешь получать обновления статистики.
- **PACKET_TIMESTAMP** - Не будешь получать временные метки от сервера.
- **PACKET_TRAILER_SYNC** - Не будешь видеть прицепы у транспортных средств.
- **PACKET_UNOCCUPIED_SYNC** - Не будешь видеть незанятые транспортные средства.
- **PACKET_VEHICLE_SYNC** - Не будешь видеть движения транспортных средств.
- **PACKET_WEAPONS_UPDATE** - Не будешь получать обновления об оружии других игроков.

</details>


## Блокировка входящих RPC (incomingRPC)
<details>
  <summary>Нажмите, чтобы раскрыть</summary>

- **RPC_SCRAPPLYANIMATION** - Не будешь видеть анимации других игроков.
- **RPC_SCRATTACHCAMERATOOBJECT** - Камера не будет прикрепляться к объектам.
- **RPC_SCRATTACHOBJECTTOPLAYER** - Не будешь видеть объекты, прикрепленные к игрокам.
- **RPC_SCRATTACHTRAILERTOVEHICLE** - Не будешь видеть прицепы, прикрепленные к транспорту.
- **RPC_SCRCANCELEDIT** - Не сможешь отменить редактирование объектов.
- **RPC_SCRCHATBUBBLE** - Не будешь видеть пузыри чата над головами игроков.
- **RPC_SCRCLEARANIMATIONS** - Анимации не будут очищаться у других игроков.
- **RPC_SCRCLIENTMESSAGE** - Не будешь получать сообщения от сервера.
- **RPC_SCRCREATE3DTEXTLABEL** - Не будешь видеть 3D текстовые метки.
- **RPC_SCRCREATEEXPLOSION** - Не будешь видеть взрывы.
- **RPC_SCRCREATEOBJECT** - Не будешь видеть создаваемые объекты.
- **RPC_SCRCREATEPICKUP** - Не будешь видеть предметы для подбора.
- **RPC_SCRDEATHMESSAGE** - Не будешь видеть сообщения о смерти других игроков.
- **RPC_SCRDESTROYOBJECT** - Объекты не будут исчезать после уничтожения.
- **RPC_SCRDESTROYPICKUP** - Предметы для подбора не будут исчезать.
- **RPC_SCRDETACHTRAILERFROMVEHICLE** - Прицепы не будут отсоединяться от транспорта.
- **RPC_SCRDISABLECHECKPOINT** - Контрольные точки не будут отключаться.
- **RPC_SCRDISABLERACECHECKPOINT** - Гоночные контрольные точки не будут отключаться.
- **RPC_SCRDISPLAYGAMETEXT** - Не будешь видеть текст на экране.
- **RPC_SCRENABLESTUNTBONUSFORPLAYER** - Не получишь бонусы за трюки.
- **RPC_SCRFORCECLASSSELECTION** - Не будешь принудительно перенаправлен к выбору класса.
- **RPC_SCRGAMEMODERESTART** - Игра не будет перезапускаться для тебя при рестарте сервера.
- **RPC_SCRGANGZONECREATE** - Не будешь видеть зоны банд.
- **RPC_SCRGANGZONEDESTROY** - Зоны банд не будут исчезать после уничтожения.
- **RPC_SCRGANGZONEFLASH** - Зоны банд не будут мигать.
- **RPC_SCRGANGZONESTOPFLASH** - Зоны банд продолжат мигать.
- **RPC_SCRGIVEPLAYERMONEY** - Не получишь деньги от сервера.
- **RPC_SCRGIVEPLAYERWEAPON** - Не получишь оружие от сервера.
- **RPC_SCRHIDEMENU** - Меню не будут скрываться.
- **RPC_SCRINITGAME** - Игра не инициализируется правильно.
- **RPC_SCRINITMENU** - Меню не будут инициализироваться.
- **RPC_SCRINTERPOLATECAMERA** - Камера не будет плавно перемещаться.
- **RPC_SCRIPTCASH** - Не будет изменяться сумма денег.
- **RPC_SCRLINKVEHICLETOINTERIOR** - Транспорт не будет привязан к интерьеру.
- **RPC_SCRMOVEOBJECT** - Объекты не будут двигаться.
- **RPC_SCRPLAYAUDIOSTREAM** - Не будешь слышать аудиопотоки.
- **RPC_SCRPLAYCRIMEREPORT** - Не будешь слышать сообщения о преступлениях.
- **RPC_SCRPLAYERSPECTATEPLAYER** - Не сможешь наблюдать за другими игроками.
- **RPC_SCRPLAYERSPECTATEVEHICLE** - Не сможешь наблюдать за транспортными средствами.
- **RPC_SCRPLAYSOUND** - Не будешь слышать звуки, запущенные сервером.
- **RPC_SCRPUTPLAYERINVEHICLE** - Не будешь помещен в транспортное средство.
- **RPC_SCRREMOVEBUILDINGFORPLAYER** - Здания не будут удаляться для тебя.
- **RPC_SCRREMOVEPLAYERFROMVEHICLE** - Не будешь удален из транспортного средства.
- **RPC_SCRREMOVEPLAYERMAPICON** - Значки на карте не будут удаляться.
- **RPC_SCRREMOVEVEHICLECOMPONENT** - Компоненты не будут удаляться с транспортных средств.
- **RPC_SCRRESETPLAYERMONEY** - Твои деньги не будут сбрасываться.
- **RPC_SCRRESETPLAYERWEAPONS** - Твое оружие не будет сбрасываться.
- **RPC_SCRSERVERJOIN** - Не будешь видеть подключение других игроков.
- **RPC_SCRSERVERQUIT** - Не будешь видеть отключение других игроков.
- **RPC_SCRSETCAMERABEHINDPLAYER** - Камера не будет возвращаться за спину игрока.
- **RPC_SCRSETCHECKPOINT** - Не будешь видеть контрольные точки.
- **RPC_SCRSETGRAVITY** - Гравитация не будет меняться.
- **RPC_SCRSETNUMBERPLATE** - Не будешь видеть измененные номерные знаки.
- **RPC_SCRSETOBJECTMATERIAL** - Не будешь видеть измененные материалы объектов.
- **RPC_SCRSETOBJECTPOS** - Объекты не будут перемещаться на новые позиции.
- **RPC_SCRSETOBJECTROT** - Объекты не будут поворачиваться.
- **RPC_SCRSETPLAYERAMMO** - Количество патронов не будет меняться.
- **RPC_SCRSETPLAYERARMEDWEAPON** - Не будет меняться активное оружие.
- **RPC_SCRSETPLAYERARMOUR** - Уровень брони не будет меняться.
- **RPC_SCRSETPLAYERATTACHEDOBJECT** - Не будешь видеть прикрепленные объекты.
- **RPC_SCRSETPLAYERCAMERALOOKAT** - Камера не будет направляться в указанную точку.
- **RPC_SCRSETPLAYERCAMERAPOS** - Камера не будет перемещаться на указанную позицию.
- **RPC_SCRSETPLAYERCOLOR** - Не будешь видеть цвета других игроков.
- **RPC_SCRSETPLAYERDRUNKLEVEL** - Не будешь видеть эффект опьянения.
- **RPC_SCRSETPLAYERFACINGANGLE** - Игроки не будут поворачиваться в нужном направлении.
- **RPC_SCRSETPLAYERFIGHTINGSTYLE** - Стиль борьбы не будет меняться.
- **RPC_SCRSETPLAYERHEALTH** - Уровень здоровья не будет меняться.
- **RPC_SCRSETPLAYERINTERIOR** - Не будешь перемещаться в интерьеры.
- **RPC_SCRSETPLAYERMAPICON** - Не будешь видеть значки игроков на карте.
- **RPC_SCRSETPLAYERNAME** - Не будешь видеть измененные имена игроков.
- **RPC_SCRSETPLAYERPOS** - Не будешь телепортироваться на указанную позицию.
- **RPC_SCRSETPLAYERPOSFINDZ** - Не будешь телепортироваться с автоматическим определением высоты.
- **RPC_SCRSETPLAYERSHOPNAME** - Не будешь видеть названия магазинов.
- **RPC_SCRSETPLAYERSKILLLEVEL** - Уровни навыков не будут меняться.
- **RPC_SCRSETPLAYERSKIN** - Не будешь видеть измененные скины игроков.
- **RPC_SCRSETPLAYERSPECIALACTION** - Не будешь видеть специальные действия игроков.
- **RPC_SCRSETPLAYERTEAM** - Команда игрока не будет меняться.
- **RPC_SCRSETPLAYERTIME** - Время для игрока не будет меняться.
- **RPC_SCRSETPLAYERVELOCITY** - Скорость игрока не будет меняться.
- **RPC_SCRSETPLAYERWANTEDLEVEL** - Уровень розыска не будет меняться.
- **RPC_SCRSETPLAYERWORLDBOUNDS** - Границы мира не будут устанавливаться.
- **RPC_SCRSETRACECHECKPOINT** - Не будешь видеть гоночные контрольные точки.
- **RPC_SCRSETSPAWNINFO** - Информация о спавне не будет устанавливаться.
- **RPC_SCRSETVEHICLEHEALTH** - Здоровье транспортных средств не будет меняться.
- **RPC_SCRSETVEHICLEPARAMSEX** - Расширенные параметры транспорта не будут меняться.
- **RPC_SCRSETVEHICLEPARAMSFORPLAYER** - Параметры транспорта для игрока не будут меняться.
- **RPC_SCRSETVEHICLEPOS** - Транспортные средства не будут телепортироваться.
- **RPC_SCRSETVEHICLEVELOCITY** - Скорость транспортных средств не будет меняться.
- **RPC_SCRSETVEHICLEZANGLE** - Угол Z транспортных средств не будет меняться.
- **RPC_SCRSETWEATHER** - Погода не будет меняться.
- **RPC_SCRSETWORLDTIME** - Время в мире не будет меняться.
- **RPC_SCRSHOWDIALOG** - Не будешь видеть диалоги.
- **RPC_SCRSHOWMENU** - Не будешь видеть меню.
- **RPC_SCRSHOWPLAYERNAMETAGFORPLAYER** - Не будешь видеть ники других игроков.
- **RPC_SCRSHOWTEXTDRAW** - Не будешь видеть текстдравы.
- **RPC_SCRSOMEUPDATE** - Не будешь получать какие-то обновления.
- **RPC_SCRSTOPAUDIOSTREAM** - Аудиопотоки не будут останавливаться.
- **RPC_SCRSTOPOBJECT** - Объекты не будут останавливаться.
- **RPC_SCRTEXTDRAWHIDEFORPLAYER** - Текстдравы не будут скрываться.
- **RPC_SCRTEXTDRAWSETSTRING** - Тексты в текстдравах не будут обновляться.
- **RPC_SCRTOGGLECLOCK** - Часы не будут переключаться.
- **RPC_SCRTOGGLEPLAYERCONTROLLABLE** - Возможность управления игроком не будет переключаться.
- **RPC_SCRTOGGLEPLAYERSPECTATING** - Режим наблюдения не будет переключаться.
- **RPC_SCRUPDATE3DTEXTLABEL** - 3D текстовые метки не будут обновляться.
- **RPC_SCRWORLDPLAYERADD** - Не будешь видеть новых игроков.
- **RPC_SCRWORLDPLAYERDEATH** - Не будешь видеть смерти игроков.
- **RPC_SCRWORLDPLAYERREMOVE** - Не будешь видеть исчезновение игроков.
- **RPC_SCRWORLDVEHICLEADD** - Не будешь видеть новые транспортные средства.
- **RPC_SCRWORLDVEHICLEREMOVE** - Не будешь видеть исчезновение транспортных средств.
</details>

## Блокировка исходящих пакетов (outcomingPacket)
<details>
  <summary>Нажмите, чтобы раскрыть</summary>

- **PACKET_ADVERTISE_SYSTEM** - Не сможешь отправлять рекламные сообщения.
- **PACKET_AIM_SYNC** - Сервер не будет знать, куда ты целишься.
- **PACKET_AUTH_KEY** - Не сможешь аутентифицироваться на сервере.
- **PACKET_BROADCAST_PINGS** - Не сможешь транслировать свой пинг.
- **PACKET_BULLET_SYNC** - Сервер не будет знать о твоих выстрелах.
- **PACKET_CONNECTED_PONG** - Сервер может решить, что ты отключился.
- **PACKET_CONNECTION_ATTEMPT_FAILED** - Не сможешь сообщить о неудачной попытке подключения.
- **PACKET_CONNECTION_BANNED** - Не сможешь получить информацию о бане.
- **PACKET_CONNECTION_COOKIE** - Не сможешь установить защищенное соединение.
- **PACKET_CONNECTION_LOST** - Не сможешь сообщить о потере соединения.
- **PACKET_CONNECTION_REQUEST** - Не сможешь запросить подключение.
- **PACKET_CONNECTION_REQUEST_ACCEPTED** - Не сможешь подтвердить принятие запроса.
- **PACKET_DETECT_LOST_CONNECTIONS** - Не сможешь обнаружить потерянные соединения.
- **PACKET_DISCONNECTION_NOTIFICATION** - Не сможешь уведомить о своем отключении.
- **PACKET_INITIALIZE_ENCRYPTION** - Не сможешь инициализировать шифрование.
- **PACKET_INTERNAL_PING** - Не сможешь отправлять внутренние пинги.
- **PACKET_INVALID_PASSWORD** - Не сможешь получить уведомление о неверном пароле.
- **PACKET_MARKERS_SYNC** - Не сможешь синхронизировать маркеры.
- **PACKET_MODIFIED_PACKET** - Не сможешь отправлять модифицированные пакеты.
- **PACKET_NEW_INCOMING_CONNECTION** - Не сможешь сообщить о новом входящем соединении.
- **PACKET_NO_FREE_INCOMING_CONNECTIONS** - Не сможешь сообщить об отсутствии свободных соединений.
- **PACKET_OPEN_CONNECTION_REPLY** - Не сможешь ответить на запрос открытия соединения.
- **PACKET_OPEN_CONNECTION_REQUEST** - Не сможешь запросить открытие соединения.
- **PACKET_PASSENGER_SYNC** - Не будет синхронизироваться твоя активность как пассажира.
- **PACKET_PING** - Не сможешь отправлять пинги.
- **PACKET_PING_OPEN_CONNECTIONS** - Не сможешь пинговать открытые соединения.
- **PACKET_PLAYER_SYNC** - Не будет синхронизироваться твоя позиция и действия.
- **PACKET_PONG** - Не сможешь отвечать на пинги.
- **PACKET_RCON_COMMAND** - Не сможешь отправлять RCON команды.
- **PACKET_RCON_RESPONCE** - Не сможешь получать ответы на RCON команды.
- **PACKET_RECEIVED_STATIC_DATA** - Не сможешь подтвердить получение статических данных.
- **PACKET_REMOTE_CONNECTION_LOST** - Не сможешь сообщить о потере удаленного соединения.
- **PACKET_REMOTE_DISCONNECTION_NOTIFICATION** - Не сможешь уведомить об удаленном отключении.
- **PACKET_REMOTE_EXISTING_CONNECTION** - Не сможешь сообщить о существующем соединении.
- **PACKET_REMOTE_NEW_INCOMING_CONNECTION** - Не сможешь сообщить о новом удаленном соединении.
- **PACKET_REMOTE_STATIC_DATA** - Не сможешь отправлять удаленные статические данные.
- **PACKET_REQUEST_STATIC_DATA** - Не сможешь запрашивать статические данные.
- **PACKET_RPC** - Не сможешь отправлять RPC пакеты.
- **PACKET_RPC_MAPPING** - Не сможешь отображать RPC.
- **PACKET_RPC_REPLY** - Не сможешь отвечать на RPC запросы.
- **PACKET_RSA_PUBLIC_KEY_MISMATCH** - Не сможешь сообщить о несоответствии RSA ключа.
- **PACKET_SECURED_CONNECTION_CONFIRMATION** - Не сможешь подтвердить защищенное соединение.
- **PACKET_SECURED_CONNECTION_RESPONSE** - Не сможешь ответить на запрос защищенного соединения.
- **PACKET_SET_RANDOM_NUMBER_SEED** - Не сможешь установить сид для генерации случайных чисел.
- **PACKET_SPECTATOR_SYNC** - Не будет синхронизироваться твоя активность как наблюдателя.
- **PACKET_STATS_UPDATE** - Не сможешь обновлять статистику.
- **PACKET_TIMESTAMP** - Не сможешь отправлять временные метки.
- **PACKET_TRAILER_SYNC** - Не будут синхронизироваться прицепы.
- **PACKET_UNOCCUPIED_SYNC** - Не будут синхронизироваться незанятые транспортные средства.
- **PACKET_VEHICLE_SYNC** - Не будут синхронизироваться твои действия в транспорте.
- **PACKET_WEAPONS_UPDATE** - Не будет обновляться информация о твоем оружии.
</details>

## Блокировка исходящих RPC (outcomingRPC)
<details>
  <summary>Нажмите, чтобы раскрыть</summary>

- **RPC_CHAT** - Не сможешь отправлять сообщения в чат.
- **RPC_CLICKPLAYER** - Не сможешь кликать по игрокам.
- **RPC_CLICKTEXTDRAW** - Не сможешь кликать по текстдравам.
- **RPC_CLIENTCHECK** - Сервер не сможет проверить твой клиент.
- **RPC_CLIENTJOIN** - Не сможешь присоединиться к серверу.
- **RPC_DAMAGEVEHICLE** - Не сможешь наносить урон транспортным средствам.
- **RPC_DEATH** - Сервер не узнает о твоей смерти.
- **RPC_DIALOGRESPONSE** - Не сможешь отвечать на диалоги.
- **RPC_EDITATTACHEDOBJECT** - Не сможешь редактировать прикрепленные объекты.
- **RPC_EDITOBJECT** - Не сможешь редактировать объекты.
- **RPC_ENTEREDITOBJECT** - Не сможешь входить в режим редактирования объектов.
- **RPC_ENTERVEHICLE** - Не сможешь входить в транспортные средства.
- **RPC_EXITVEHICLE** - Не сможешь выходить из транспортных средств.
- **RPC_GIVETAKEDAMAGE** - Не сможешь получать или наносить урон.
- **RPC_MAPMARKER** - Не сможешь устанавливать маркеры на карте.
- **RPC_MENUQUIT** - Не сможешь выходить из меню.
- **RPC_MENUSELECT** - Не сможешь выбирать пункты в меню.
- **RPC_NPCJOIN** - NPC не сможет присоединиться к серверу.
- **RPC_PICKEDUPPICKUP** - Не сможешь подбирать предметы.
- **RPC_REQUESTCLASS** - Не сможешь запрашивать класс.
- **RPC_REQUESTSPAWN** - Не сможешь запрашивать спавн.
- **RPC_SCMEVENT** - Не сможешь отправлять события скриптмода.
- **RPC_SERVERCOMMAND** - Не сможешь отправлять серверные команды.
- **RPC_SETINTERIORID** - Не сможешь менять ID интерьера.
- **RPC_SPAWN** - Не сможешь спавниться.
- **RPC_SRVNETSTATS** - Не сможешь получать сетевую статистику сервера.
- **RPC_UPDATESCORESPINGSIPS** - Не сможешь обновлять очки, пинги и IP-адреса.
- **RPC_VEHICLEDESTROYED** - Не сможешь сообщить о уничтожении транспортного средства.
- **RPC_WEAPONPICKUPDESTROY** - Не сможешь уничтожать подбираемое оружие.
</details>