# Лабораторная работа № 3. Исследование Cloud Storage

University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru/)\
Course: [Cloud platforms as the basis of technology entrepreneurship](https://ex-itmo-ict-faculty.github.io/cloud-platforms-as-the-basis-of-technology-entrepreneurship/)\
Year: 2026/2027\
Group: U4225\
Author: Элчиян Роман Романович\
Lab: Lab3\
Date of create: 01.11.2026\
Date of finished: 06.11.2026

## Цель работы

Изучить работу объектного хранилища Google Cloud Storage при создании бакета, размещении объектов и настройке публичного чтения. [Задание лабораторной работы № 3](https://github.com/ex-itmo-ict-faculty/cloud-platforms-as-the-basis-of-technology-entrepreneurship/blob/main/docs/education/labs2023-2024/lab3/lab3.md)

## 1. Создание бакета

В Google Cloud Console в проекте `cloud-platforms-as-the-basis` создан бакет со следующими параметрами.

| Параметр | Значение |
| --- | --- |
| Имя бакета | `cloud-platforms-lab3-elchiyan-2026` |
| Регион | `europe-west3` (Frankfurt) |
| Класс хранения | `Standard` |
| Управление доступом | `Uniform` |

## 2. Загрузка изображений

В корень бакета загружены четыре JPG-файла — `Puffer-fish.jpg`, `images (2).jpg`, `images (3).jpg` и `images (4).jpg`.

![Четыре JPG-файла в корне бакета](images/02_images_uploaded.png)

*Рисунок 1 — Список объектов в корне бакета после загрузки.*

![Коллаж из четырёх исходных изображений](images/uploaded-images-collage.jpg)

*Рисунок 2 — Четыре изображения, загруженные в бакет.*

## 3. Создание папки и перемещение файлов

В бакете создана папка `lab3-images fugu`. В неё перемещены все четыре объекта.

![Четыре JPG-файла в папке lab3-images fugu](images/03_images_moved_to_folder.png)

*Рисунок 3 — Объекты в папке после перемещения.*

## 4. Настройка публичного доступа

В политике IAM бакета субъекту `allUsers` назначена роль `Storage Object Viewer` (`roles/storage.objectViewer`). Объекты стали доступны для чтения без авторизации.

## 5. Проверка публичных ссылок

Прямые URL объектов проверены в браузере без авторизации. На рисунке 4 показано открытие `Puffer-fish.jpg` в режиме инкогнито.

![Файл Puffer-fish.jpg открыт по прямому URL в окне инкогнито](images/public-link-incognito.png)

*Рисунок 4 — Проверка публичной ссылки на Puffer-fish.jpg.*

В PowerShell сначала проверены четыре публичных URL через `curl.exe` без авторизации и сохранения файлов. Все запросы вернули `HTTP 200` и тип `image/jpeg`.

![Результаты HTTP-запросов и команда скачивания в PowerShell](images/powershell-public-check.png)

*Рисунок 5 — Проверка четырёх ссылок без сохранения файлов и последующая команда скачивания.*

Затем все четыре JPG-файла скачаны по тем же URL в `Downloads\lab3-images`.

![Четыре скачанных JPG-файла в Проводнике Windows](images/downloaded-files.png)

*Рисунок 6 — Изображения, сохранённые на ПК.*

## 6. Удаление бакета

После проверки удалён бакет `cloud-platforms-lab3-elchiyan-2026`.

## 7. Вывод

После настройки публичного доступа были проверены ссылки на все четыре загруженных изображения. Каждый файл успешно открывался в браузере по прямому URL без авторизации в Google Cloud. На рисунке приведён пример проверки файла Puffer-fish.jpg в режиме инкогнито. После завершения проверки созданный бакет был удалён.
