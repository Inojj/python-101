# Домашнее задание: Модули и функции в Python

## Структура проекта:
```
homework_project/
├── main.py                           # Главный файл запуска
├── core/                            # Основные функции
│   ├── __init__.py
│   ├── basic_functions.py           # Функции с разными аргументами
│   └── advanced_functions.py        # Комбинированные функции
├── utils/                           # Утилиты
│   ├── __init__.py
│   ├── decorators.py               # Декораторы
│   ├── file_operations.py          # Работа с файлами
│   └── validators.py               # Функции валидации
├── data/                           # Модули для работы с данными
│   ├── __init__.py
│   ├── processors.py               # Обработка данных
│   └── formatters.py               # Форматирование данных
├── tests/                          # Тесты
│   ├── __init__.py
│   ├── test_core.py               # Тесты основных функций
│   └── test_utils.py              # Тесты утилит
└── config/                        # Конфигурация
    ├── __init__.py
    └── settings.py                # Настройки проекта
```

## Задание 1: Создание структуры пакетов

### 1.1 Создайте все папки и файлы __init__.py
Создайте все папки согласно структуре выше. В каждой папке должен быть файл `__init__.py`, который делает папку Python пакетом. Пока оставьте эти файлы пустыми или с простым комментарием о назначении пакета.

## Задание 2: Основные функции (core/basic_functions.py)

Реализуйте следующие функции:

### Функция create_profile
- Принимает обязательные аргументы: `name` (строка) и `age` (число)
- Принимает необязательные аргументы: `email` (по умолчанию None) и `city` (по умолчанию "Москва")
- Добавьте валидацию: проверьте, что возраст положительный и меньше 150
- Если передан email, проверьте что он содержит символ "@"
- Возвращает словарь со всеми переданными данными
- Добавьте к результату поле `created_at` с текущей датой

### Функция calculate_discount
- Первый аргумент `price` - обязательный позиционный
- Все остальные аргументы должны быть именованными (используйте `*`)
- `discount_percent` (по умолчанию 10) - размер скидки в процентах
- `membership` (по умолчанию "обычный") - тип членства клиента
- Если membership равно "премиум", добавьте дополнительно 5% к скидке
- Если membership равно "vip", добавьте дополнительно 10% к скидке
- Возвращает словарь с исходной ценой, размером скидки, финальной ценой и типом членства

### Функция format_name  
- Первые два аргумента `first_name` и `last_name` должны быть только позиционными (используйте `/`)
- Третий аргумент `middle_name` необязательный и может передаваться любым способом
- Параметр `format_style` (по умолчанию "short") определяет стиль форматирования
- При "short": возвращает "Фамилия И.О." или "Фамилия И." если нет отчества
- При "full": возвращает "Фамилия Имя Отчество" полностью
- При "reverse": возвращает "Имя Фамилия" или "Имя Отчество Фамилия"

## Задание 3: Продвинутые функции (core/advanced_functions.py)

### Функция process_data
- Первый аргумент `data` - список данных для обработки
- Принимает произвольное количество операций через `*operations`
- Поддерживаемые операции: "sort", "unique", "reverse", "filter_positive", "double"
- Именованный параметр `reverse` (по умолчанию False) для обратной сортировки
- Дополнительные параметры через `**options` могут включать `min_value`, `max_value` для фильтрации
- Применяет операции в порядке их указания
- Возвращает обработанный список

### Функция create_report
- Обязательный аргумент `title` - заголовок отчета
- Произвольное количество разделов через `*sections`
- Именованные параметры: `author` (по умолчанию "Система"), `format` (по умолчанию "text")
- Дополнительные метаданные через `**metadata`
- Если format="text": возвращает простой текстовый отчет
- Если format="html": оборачивает разделы в HTML теги
- Добавляет в отчет дату создания и все переданные метаданные

### Функция send_notification
- Обязательные аргументы: `recipient` (получатель) и `message` (текст)
- Произвольное количество дополнительных получателей через `*cc_recipients`
- Именованный параметр `urgent` (по умолчанию False)
- Именованный параметр `delivery_method` (по умолчанию "email") 
- Дополнительные опции через `**options` (subject, retry_count, etc.)
- Возвращает словарь с информацией об отправке, включая количество получателей и статус

## Задание 4: Обработчики данных (data/processors.py)

### Функция sum_numbers
- Принимает произвольное количество чисел через `*numbers`
- Если чисел нет, возвращает 0
- Игнорирует значения, которые не являются числами, но выводит предупреждение
- Поддерживает целые и дробные числа

### Функция find_extremes
- Принимает произвольное количество значений через `*values`
- Именованный параметр `return_type` (по умолчанию "both")
- При "both": возвращает кортеж (минимум, максимум)
- При "min": возвращает только минимум
- При "max": возвращает только максимум
- Если значений нет, возвращает None

### Функция create_sentence
- Принимает произвольное количество слов через `*words`
- Именованный параметр `separator` (по умолчанию " ")
- Именованный параметр `end_mark` (по умолчанию ".")
- Именованный параметр `capitalize_first` (по умолчанию True)
- Объединяет слова через разделитель, добавляет знак препинания
- При необходимости делает первую букву заглавной

### Функция calculate_statistics
- Принимает произвольное количество чисел через `*numbers`
- Именованные параметры для выбора статистик: `mean`, `median`, `mode` (все по умолчанию True)
- Дополнительные параметры через `**options`
- Возвращает словарь с запрошенными статистиками

## Задание 5: Форматтеры (data/formatters.py)

### Функция build_url
- Обязательный аргумент `base_url`
- Произвольные параметры запроса через `**params`
- Правильно кодирует специальные символы в параметрах
- Возвращает готовый URL с параметрами

### Функция format_table
- Обязательный аргумент `data` - список списков или словарей
- Именованные параметры: `headers` (заголовки), `align` (выравнивание)
- Дополнительные опции через `**formatting_options`
- Возвращает отформатированную таблицу в виде строки

### Функция log_message
- Обязательный аргумент `message`
- Именованный параметр `level` (по умолчанию "INFO")
- Именованный параметр `timestamp` (по умолчанию True) - добавлять ли время
- Дополнительная информация через `**details`
- Возвращает отформатированную строку лога

### Функция create_config
- Принимает произвольные настройки через `**settings`
- Именованный параметр `prefix` (по умолчанию "config_") для добавления к ключам
- Именованный параметр `validate` (по умолчанию True) для проверки настроек
- Возвращает словарь конфигурации

## Задание 6: Декораторы (utils/decorators.py)

### Декоратор timer
- Измеряет время выполнения функции
- Выводит результат в формате: "Функция {название} выполнилась за {время} секунд"
- Должен сохранять оригинальное имя и документацию функции

### Декоратор logger
- Логирует вызов функции с аргументами и результат
- Выводит информацию о входящих аргументах и возвращаемом значении
- При ошибке в функции логирует исключение

### Декоратор validate_types
- Принимает ожидаемые типы аргументов
- Проверяет типы всех переданных аргументов
- Выбрасывает TypeError при несоответствии типов

## Задание 7: Файловые операции (utils/file_operations.py)

### Функция read_file
- Обязательный аргумент `filename`
- Именованный параметр `encoding` (по умолчанию "utf-8")
- Дополнительные опции через `**options` (например, `strip_lines`, `skip_empty`)
- Обрабатывает ошибки чтения файла
- Возвращает содержимое файла или список строк

### Функция write_data
- Обязательный аргумент `filename`
- Произвольное количество данных для записи через `*data`
- Именованный параметр `separator` (по умолчанию "\n")
- Именованный параметр `mode` (по умолчанию "w")
- Дополнительные опции через `**options`

### Функция process_csv
- Обязательный аргумент `filename`
- Произвольное количество функций-обработчиков через `*processors`
- Именованные параметры: `delimiter`, `skip_header`, `encoding`
- Применяет обработчики к каждой строке
- Возвращает обработанные данные

## Задание 8: Валидаторы (utils/validators.py)

### Функция validate_email
- Проверяет корректность email адреса
- Должен содержать @ и точку в домене
- Проверяет базовую структуру email

### Функция validate_phone
- Проверяет российские номера телефонов
- Поддерживает разные форматы: +7, 8, 7
- Проверяет количество цифр

### Функция validate_data
- Принимает данные для валидации
- Произвольное количество функций-валидаторов через `*validators`
- Дополнительные параметры через `**validation_options`
- Возвращает результат валидации и список ошибок

## Задание 9: Главный файл (main.py)

Создайте главный файл, который демонстрирует:

### Различные способы импорта
- Импорт отдельных функций
- Импорт целых модулей
- Импорт с алиасами
- Импорт из подпакетов

### Демонстрацию работы с аргументами
- Примеры вызова функций только с позиционными аргументами
- Примеры с именованными аргументами
- Примеры с смешанным использованием
- Демонстрацию keyword-only и positional-only аргументов
- Использование *args и **kwargs
- Распаковку списков и словарей

### Работу декораторов
- Применение декораторов к функциям
- Демонстрацию их эффектов

### Обработку конфигурации
- Чтение и изменение настроек
- Использование настроек в разных модулях

## Требования к выполнению:

### Качество кода
- Следование PEP 8
- Понятные имена переменных и функций
- Логическое разделение функциональности по модулям

### Демонстрация понимания
- Правильное использование всех типов аргументов
- Понимание области видимости и импорта модулей
- Эффективное использование возможностей Python