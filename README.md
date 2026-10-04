

# SmartSurface

**Мобильный робот для исследования стен и автоматизации отделочных работ**

![ROS 2](https://img.shields.io/badge/ROS_2-22314E?style=for-the-badge&logo=ros&logoColor=white)
![Raspberry Pi 5](https://img.shields.io/badge/Raspberry_Pi_5-C51A4A?style=for-the-badge&logo=raspberrypi&logoColor=white)
![Arduino Mega](https://img.shields.io/badge/Arduino_Mega-00979D?style=for-the-badge&logo=arduino&logoColor=white)

[![Архитектура](https://img.shields.io/badge/Архитектура-8B6FE8?style=flat-square)](docs/ARCHITECTURE.md)
[![ROS и API](https://img.shields.io/badge/ROS_и_API-8B6FE8?style=flat-square)](docs/ROS_AND_WEB_API.md)
[![Arduino](https://img.shields.io/badge/Arduino-8B6FE8?style=flat-square)](docs/ARDUINO_PROTOCOL.md)
[![Компьютерное зрение](https://img.shields.io/badge/Компьютерное_зрение-8B6FE8?style=flat-square)](docs/COMPUTER_VISION.md)



![Прототип SmartSurface у стены](assets/prototype-from-presentation.png)

## Идея

SmartSurface вырос из простой задачи: облегчить работу со стенами, которую обычно выполняют вручную. Робот должен перемещаться вдоль поверхности, собирать данные и помогать оператору находить дефекты. Следующий шаг - связать обследование стены с её обработкой.

В основе проекта - мобильная платформа с четырьмя всенаправленными колёсами, Raspberry Pi 5, Arduino Mega, лидар и камера. Оператор управляет роботом через браузер и видит видео и данные датчиков в одной панели.

## Возможности и состояние проекта

В технических материалах описаны ручное управление через веб-панель, обратная связь от четырёх энкодеров, колёсная одометрия с EKF, сканы лидара и видеопоток камеры. Для обнаружения трещин предусмотрена сегментация YOLOv8-seg; Hailo рассматривается как вариант ускорения.

Базовая архитектура использует одометрию. Полноценные SLAM и Nav2 относятся к расширению навигации. В материалах также описаны экспериментальные сценарии поиска стены, сканирования и работы инструментом.

**Сейчас в открытой части проекта собраны документация и изображения.** Исходники, прошивка и воспроизводимая инструкция сборки ещё не опубликованы. Описание основано на предоставленных технических материалах; измеренные FPS, точность и производительность отделки пока не приведены.

## Как всё связано

Браузер отправляет команды веб-узлу, тот публикует их в ROS 2. Мост передаёт команды Arduino, а контроллер управляет моторами и возвращает данные энкодеров. Камера и лидар независимо поставляют данные для панели и экспериментальных сценариев.

![Общая структура системы из презентации](assets/architecture-from-presentation.png)

Схема показывает концепцию из презентации. Подробное описание текущего графа узлов и различий между одометрией и SLAM находится в [документе по архитектуре](docs/ARCHITECTURE.md).

## Программная часть

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Vue 3](https://img.shields.io/badge/Vue_3-184D40?style=flat-square&logo=vuedotjs&logoColor=4FC08D)
![Nuxt 4](https://img.shields.io/badge/Nuxt_4-002E3B?style=flat-square&logo=nuxt&logoColor=00DC82)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-0F172A?style=flat-square&logo=tailwindcss&logoColor=38BDF8)
![Flask](https://img.shields.io/badge/Flask-252525?style=flat-square&logo=flask&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-536DFE?style=flat-square&logo=opencv&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

- **ROS 2 и Python** - узлы, сообщения датчиков, управление и связь с контроллером.
- **Nuxt 4, Vue 3 и Tailwind CSS** - интерфейс оператора.
- **Flask и Socket.IO** - HTTP API, телеметрия и обмен с панелью.
- **MJPEG и OpenCV** - передача и обработка видеопотока.
- **robot_localization** - фильтрация одометрии.
- **YOLOv8-seg** - экспериментальное обнаружение трещин.
- **PostgreSQL** - авторизация в описанной конфигурации веб-узла.



## Документация

Начните с [архитектуры](docs/ARCHITECTURE.md), затем выберите нужный раздел:

- [ROS 2 и веб API](docs/ROS_AND_WEB_API.md) - топики, сервисы, HTTP, Socket.IO и видео.
- [Arduino и одометрия](docs/ARDUINO_PROTOCOL.md) - Serial-протокол, оси, энкодеры и управление.
- [Компьютерное зрение](docs/COMPUTER_VISION.md) - обработка кадров, CPU и Hailo, оценка качества.
- [Конфигурация и эксплуатация](docs/OPERATIONS.md) - параметры, диагностика и требования к воспроизводимой сборке.

