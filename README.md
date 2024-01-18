# Загрузчик для webinar.ru

Позволяет: 
1) Скачать запись вебинара и сохранить его в формате ".mp4";
2) Скачать сразу несколько записей благодаря пакетной загрузке через txt файл.

## Общая информация

1) Скрипт выгружает вебинары с webinar.ru, если ссылка подходит под паттерны: "https://my.mts-link.ru/*", "https://events.webinar.ru/*";
2) Скрипт создает папку для вебинара, (ВНИМАНИЕ!) выгружает туда все *чанки (у каждого чанка будет свой индекс в названии) и после этого создает новый файл, который состоит из всех скаченных чанков (он будет без индекса);
3) В файле settings.json указаны настройки для скрипта, параметры принимают значения True или False. Можно изменить поведение скрипта, поменяв значение настроек в фале settings.json;
4) Скрипт самостоятельно обращается к сайту, следовательно, не имеет смысла параллельно запускать видео вручную из браузера. Это может только замедлить скорость выгрузки вебинара!

* В контексте данного скрипта чанк - это кусок вебинара, который образовался из-за того, что лектор на некоторое время
прервал или приостановил трансляцию (например, для взятия перерыва). Если лектор ни разу не прервал вебинар, 
значит чанк будет всего один, в следствии после выгрузки, в данном случае всего 1 чанка, нет нужды запускать 
другой скрипт для склейки этих чанков.   

## Режимы работы скрипта
1) Выгрузить запись вебинара;
2) Запустить процесс слияние чанков;
3) Выгрузить несколько вебинаров, используя пакетную загрузку.
Для использования пакетной загрузки нужно передать программе путь до файла с расширением '.txt', 
в котором все ссылки будут разделены символом новой строки (кнопка 'Enter').


## Для подготовки к запуску необходимо:

1) Создать директорию на компьютере для программы и открыть в ней терминал;
2) Скачать репозиторий при помощи команды:

```commandline
  git clone https://github.com/Alex-FIR-IT/Loader_for_webinar.ru
```

3) Открыть терминал в директории скрипта;
4) Прописать следующую команду:

```commandline
  pip install -r requirements.txt
```

## Для запуска скрипта необходимо:

1) Открыть терминал в директории скрипта;
2) Прописать следующую команду:

```commandline
  python main.py
```
ИЛИ

```commandline
  python3 main.py
```

## Пользовательская настройка скрипта
На данный момент в файл settings.json доступно 2 параметра для настройки:

1) auto_files_merging. Если true, тогда после скачивания чанков вебинара автоматически начнет их слияние.
Если false, тогда при запуске программы спросит нужно ли запускать слияние чанков после их выгрузки (по умолчанию false);
2) remove_mp3_after_merging_chunks. Если true, тогда после слияния чанков в формат mp4 удалит ОТДЕЛЬНЫЙ звуковой файл формата mp3.
Если false, тогда после слияния чанков останется и файл формата mp4, и файл формата mp3 (по умолчанию false).