# Отчет по лабораторной работе №1
**Тема:** Создание и развертывание статического сайта на базе MkDocs с публикацией на GitHub Pages  
**Выполнил:** Студент группы P3124 Потёмкин Платон

---

## 🔗 Ссылки на проект

1.  **Репозиторий с исходным кодом:**  
    [https://github.com/platonpotemkin51-source/platonpotemkin51-source.github.io](https://github.com/platonpotemkin51-source/platonpotemkin51-source.github.io) 

2.  **Развернутый статический сайт:**  
    [https://platonpotemkin51-source.github.io](https://platonpotemkin51-source.github.io) 

---

## 1. Цель работы
Освоить процесс создания статического сайта с использованием генератора документации MkDocs, научиться организовывать структуру документации проекта, изучить базовые принципы работы с Git/GitHub и развернуть сайт на GitHub Pages.

## 2. Ход выполнения работы

### 2.1. Подготовка репозитория
1.  Был создан публичный репозиторий на GitHub.
2.  В настройках репозитория (**Settings -> Pages**) в качестве источника (Source) была выбрана ветка `main` и каталог `/docs`.

### 2.2. Локальная настройка окружения
1.  Репозиторий был клонирован на локальную машину:
    ```bash
    git clone https://github.com/platonpotemkin51-source/platonpotemkin51-source.github.io.git
    ```
2.  В папке проекта создано и активировано виртуальное окружение Python для изоляции зависимостей:
    ```bash
    python -m venv venv
    # Активация (Windows)
    venv\Scripts\activate
    ```
3.  Установлен генератор сайтов **MkDocs** и тема оформления **Material**:
    ```bash
    pip install mkdocs mkdocs-material
    ```
4.  Создан файл `.gitignore`, в который добавлены исключения: `venv/`, `__pycache__/`, `site/`.

### 2.3. Создание сайта

Инициализирован новый проект в папке `source`:

```bash
mkdocs new source
```

### 2.4. Настройка конфигурации (mkdocs.yml)
Файл `source/mkdocs.yml` был отредактирован. 
**Выбор темы:** Была выбрана тема `material`.
*Обоснование:* Это современная, адаптивная тема с поддержкой темной версии, удобной навигацией и широкими возможностями кастомизации (admonitions, иконки), что идеально подходит для портфолио.

Конфигурации:
```yaml
site_name: Портфолио - Потёмкин Платон
theme:
  name: material
  language: ru
nav:
  - Главная: index.md
  - Об авторе: about.md
  - Лабораторные работы:
    - Лабораторная 1: labs/lab1.md
    - Лабораторная 2: labs/lab2.md
    - Лабораторная 3: labs/lab3.md
```

Также была настроена тематика и оформление сайта:
```yaml
theme:
  name: material
  features:
    - navigation.instant
    - navigation.instant.prefetch
    - content.action.edit
  language: ru
  palette:
    scheme: default
    primary: grey
    accent: light blue
  icon:
    repo: fontawesome/brands/github
    edit: material/pencil-box
    view: material/eye

markdown_extensions:
  - pymdownx.emoji:
      emoji_index: !!python/name:materialx.emoji.twemoji
      emoji_generator: !!python/name:materialx.emoji.to_svg
  - admonition
  - pymdownx.details
  - pymdownx.superfences
```

### 2.5. Наполнение контентом
Были созданы следующие страницы:
1.  **Главная (`index.md`)**: Страница с приветствием и отображением статусов лабораторных.
2.  **Об авторе (`about.md`)**: Информация (ИСУ, контакты, навыки) с использованием красивых блоков оформления.
3.  **Лабораторные работы**: Создана структура папок `docs/labs/` и файлы-заглушки для трех лабораторных работ.
4.  Для первой лабораторной работы (`lab1.md`) оформлен данный отчет.

### 2.6. Сборка и Деплой
1.  Проверка сайта выполнялась локально командой:
    ```bash
    cd source
    mkdocs serve
    ```
2.  Сборка статических файлов выполнялась в папку `../docs` (корень репозитория), как того требует задание:
    ```bash
    mkdocs build -d ../docs
    ```
3.  Результаты работы (исходники в `source` и сборка в `docs`) были отправлены в удаленный репозиторий:
    ```bash
    git add .
    git commit -m "Закончил lab 1 отчет и создание сайта"
    git push
    ```

## 3. Выводы
В ходе выполнения лабораторной работы я:
- Познакомился с принципом работы генераторов статических сайтов (SSG) на примере MkDocs.
- Научился разделять исходный код (Markdown) и результат сборки (HTML).
- Настроил автоматическую публикацию сайта через GitHub Pages, используя папку `/docs`.
- Освоил синтаксис Markdown и конфигурацию `mkdocs.yml` для создания структурированной документации.
- Создал базу для своего будущего портфолио лабораторных работ.