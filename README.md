Функционал
1. Запускаются два экземпляра Server’а, которым передаются уникальные
идентификаторы.
2. Запускается Client, который устанавливает соединения с серверами.
3. Потенциально, Client может работать с произвольным количеством экземпляров
Server’а.
4. Номера портов, на которых висят сервера, задаются в конфигурационном файле
(напр. в yaml).
5. Client передает серверам через случайные промежутки времени (от 1 - до 10 сек.)
случайные числа (от 1 - до 10). Каждому серверу - свое число.
6. Server принимает число N и через N секунд отправляет Client’у сообщение:
<идентификатор сервера> - <N>.
7. Client принимает сообщения от Server’ов и выводит на экран.
8. Server и Client должны быть асинхронными (использовать asyncio, явно не создавать
потоки, процессы). Т.е. в действительности у каждого сервера в ожидании может
находиться много запросов, а не 1-ин.
9. Не использовать aiohttp и другие web-фреймворки.
10. Экземляры Server’а запускаются в docker контейнерах.
11. Для запуска docker контейнеров используем docker-compose (соответсвенно
идентификаторы серверов можно передать через переменные окружения или cli в
entrypoint).