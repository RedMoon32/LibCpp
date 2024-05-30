## Проект: Консольная система управления библиотекой

### Описание проекта
Консольная система управления библиотекой предназначена для управления библиотечным фондом. Система должна поддерживать различные сущности (книги, журналы, авторы, читатели), предоставлять функции поиска, загрузки данных из файлов, а также функционал выдачи и возврата предметов.

### Основные сущности
1. **Абстрактный класс Item (предмет который можно взять в библиотеке)**
    - ID документа
    - Название
    - Автор (указатель на объект класса Author, Author* author) 
    - Год издания
    - Общее количество
    - Количество доступных

2. **Книга (наследуется от Item)**
    - ISBN
    - Количество страниц

3. **Журнал (наследуется от Item)**
    - Номер выпуска
    - Категория

4. **Автор**
    - Имя
    - Год рождения
    - Список произведений (книги и журналы) - список указателей на Item

5. **Читатель**
    - Имя
    - Фамилия
    - Номер читательского билета (генерируется автоматически, уникальный 5-значный номер)
    - Список взятых предметов (книги и журналы) - список указателей на Item

### Дерево меню в консоли
```plaintext
1. Управление книгами
    1.1. Добавить книгу
    1.2. Поиск книги
    1.3. Список всех книг
2. Управление журналами
    2.1. Добавить журнал
    2.2. Поиск журнала
    2.3. Список всех журналов
3. Управление авторами
    3.1. Добавить автора
    3.2. Список всех авторов (**в лексикографическом порядке**)
4. Управление читателями
    4.1. Добавить читателя
    4.2. Поиск читателя
    4.3. Список всех читателей
5. Выдача предметов читателям
    5.1. Выдать предмет (книга или журнал)
6. Возврат предметов от читателей
    6.1. Вернуть предмет (книга или журнал)
7. Общий поиск по книгам и журналам
    7.1. Поиск по году выхода
8. Загрузка данных
9. Выход
```

### Пример функций добавления

**Добавление книги - перед тем как добавлять книгу мы должны добавить ее автора**
```plaintext
Введите ID книги: 1
Введите название книги: Война и мир
Введите автора книги: Лев Толстой
Введите год издания книги: 1869
Введите общее количество книг: 5
Введите ISBN книги: 978-3-16-148410-0
Введите количество страниц книги: 1225
Книга успешно добавлена.
```

**Добавление журнала**
```plaintext
Введите ID журнала: 1
Введите название журнала: Наука и жизнь
Введите автора журнала: Редакция
Введите год издания журнала: 2024
Введите категорию журнала: Научный
Введите общее количество журналов: 10
Введите номер выпуска журнала: 5
Журнал успешно добавлен.
```

**Добавление читателя**
```plaintext
Введите имя читателя: Иван
Введите фамилию читателя: Иванов
Читатель успешно добавлен. Номер читательского билета: 12345
```

### Пример функций поиска

**Поиск книги**
```plaintext
Введите критерий поиска:
1. По названию
2. По автору
3. По году издания

Введите номер критерия: 1
Введите название книги: Война и мир
Результаты поиска:
1. ID: 1, Война и мир, Лев Толстой, 1869, Роман, Общее количество: 5, Доступно: 2, ISBN: 978-3-16-148410-0, Страниц: 1225
```

**Поиск журнала**
```plaintext
Введите критерий поиска:
1. По названию
2. По автору
3. По категории
4. По году издания

Введите номер критерия: 3
Введите категорию журнала: Научный
Результаты поиска:
1. ID: 1, Наука и жизнь, Редакция, 2024, Научный, Общее количество: 10, Доступно: 7, Номер выпуска: 5
```

**Поиск читателя**
```plaintext
Введите критерий поиска:
1. По имя - фамилия
2. По номеру читательского билета

Введите номер критерия: 1
Введите фамилию читателя: Иван Иванов
Результаты поиска:
1. Иван Иванов, Номер билета: 12345, Взятые предметы: Война и мир (Лев Толстой), Преступление и наказание (Фёдор Достоевский)
```

**Общий поиск по книгам и журналам**
```plaintext
Введите критерий поиска:
1. По году выхода

Введите номер критерия: 1
Введите год выхода: 2024
Результаты поиска:
1. ID: 1, Наука и жизнь, Редакция, 2024, Научный, Общее количество: 10, Доступно: 7, Номер выпуска: 5
2. ID: 2, National Geographic, Редакция, 2024, География, Общее количество: 8, Доступно: 8, Номер выпуска: 6
```

### Пример функций выдачи и возврата предметов

Выдаем первый найденный предмет с таким названием из нашей библиотеки

**Выдача предмета читателю**
```plaintext
Введите номер читательского билета: 12345
Введите название предмета: Война и мир
Книга "Война и мир" успешно выдана читателю Иван Иванов.
```

**Выдача предмета читателю**
```plaintext
Введите номер читательского билета: 12345
Введите название предмета: Наука и космос
Журнал "Наука и космос" успешно выдана читателю Иван Иванов.
```

**Возврат предмета от читателя**
```plaintext
Введите номер читательского билета: 12345
Введите название предмета: Война и мир
Книга "Война и мир" успешно возвращена читателем Иван Иванов.
```

### Пример функций показа всех сущностей

**Показ всех книг**
```plaintext
Список всех книг:
1. ID: 1, Преступление и наказание, Фёдор Достоевский, 1866, Роман, Общее количество: 3, Доступно: 0, ISBN: 978-3-16-148410-1, Страниц: 671
   Читают: Пётр Петров (67890)
2. ID: 2, Война и мир, Лев Толстой, 1869, Роман, Общее количество: 5, Доступно: 2, ISBN: 978-3-16-148410-0, Страниц: 1225
   Читают: Иван Иванов (12345)
```

**Показ всех журналов**
```plaintext
Список всех журналов:
1. ID: 1, Наука и жизнь, Редакция, 2024, Научный, Общее количество: 10, Доступно: 7, Номер выпуска: 5
   Читают: Иван Иванов (12345)
2. ID: 2, National Geographic, Редакция, 2024, География, Общее количество: 8, Доступно: 8, Номер выпуска: 6
```

**Показ всех авторов**
```plaintext
Список всех авторов:
1. Лев Толстой, Год рождения: 1828, Произведения: Война и мир, Анна Каренина
2. Фёдор Достоевский, Год рождения: 1821, Произведения: Преступление и наказание, Идиот
```

**Показ всех читателей**
```plaintext
Список всех читателей:
1. Иван Иванов, Номер билета: 12345, Взятые предметы: Война и мир (Лев Толстой)
2. Пётр Петров, Номер билета: 67890, Взятые предметы: Преступление и наказание (Фёдор Достоевский)
```

### Пример функций сохранения и загрузки данных

**Загрузка данных из файла**
```plaintext
Введите путь к файлу для загрузки данных о книгах: books.csv
Загрузка данных...
Данные успешно загружены.
```

### Пример обработки ошибок при выдаче и возврате предметов

**Попытка взять книгу, которая отсутствует (не найдена)**
```plaintext
Введите номер читательского билета: 12345
Введите название предмета: Наука и жизнь
Ошибка: Предмет "Неизвестная книга" не найдена в библиотеке.
```

**Попытка взять книгу, свободные экземпляры которой закончились**
```plaintext
Введите номер читательского билета: 12345
Введите название предмета: Преступление и наказание
Ошибка: Все экземпляры предмета "Преступление и наказание" уже выданы.
```

**Попытка вернуть книгу, которая не найдена у читателя в списке читаемых**
```plaintext
Введите номер читательского билета: 12345
Введите название предмета: Неизвестная книга
Ошибка: Предмет "Неизвестная книга" не найдена в списке читаемых у читателя Иван Иванов.
```

### Уровни функциональности

#### 1. Минимально ожидаемый функционал
- Управление книгами: можно добавить книгу
- Авторы: можно добавить автора, вывести всех авторов (**в лексикографическом порядке**) и их книги
- Читатели: можно добавить читателя, вывести список всех читателей и книг которые они читают
- Читатель может взять книгу (не давать эту книгу если он уже эту книгу брал или доступные книги закончились), вернуть книгу (если он ее брал)

#### 2. Средний функционал
- Управление книгами: есть поиск по книгам
- Управление журналами: можно добавить журнал, есть поиск по журналамам, список всех журналов
- Читатель может брать журналы, возвращать (в том же окне где он возвращал книги, ищем первый попавшийся документ с таким названием (книгу или журнал)
  и если нашлось выдаем пользователю
- Общий поиск по книгам и журналам
- Поиск по имя - фамилия читателя

#### 3. Высший функционал
- Загрузка сущностей из файлов (CSV). (из 4 файлов в формате csv - readers.csv, books.csv, maganizes.csv, authors.csv)

### Подробное описание пункта "Загрузка из файлов"
Функция загрузки данных из файлов должна поддерживать формат CSV. При загрузке данных необходимо учитывать возможные ошибки формата и некорректные данные.

#### Пример CSV файлов

**books.csv**
```csv
id,title,author,year,genre,total,available,isbn,pages
1,"Война и мир","Лев Толстой",1869,"Роман",5,2,"978-3-16-148410-0",1225
2,"Преступление и наказание","Фёдор Достоевский",1866,"Роман",3,0,"978-3-16-148410-1",671
```

**magazines.csv**
```csv
id,title,author,year,category,total,available,issue_number
1,"Наука и жизнь","Редакция",2024,"Научный",10,7,5
2,"National Geographic","Редакция",2024,"География",8,8,6
```

**authors.csv**
```csv
first_name,last_name,birth_year,works
"Лев","Толстой",1828,"Война и мир,Анна Каренина"
"Фёдор","Достоевский",1821,"Преступление и наказание,Идиот"
```

**readers.csv**
```csv
first_name,last_name,card_number,borrowed_items
"Иван","Иванов",12345,"Война и мир"
"Пётр","Петров",67890,"Преступление и наказание"
```
