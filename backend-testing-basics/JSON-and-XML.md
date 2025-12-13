Когда клиент и сервер обмениваются данными, они используют специальные форматы. Самые популярные в backend-тестировании:

+ **JSON (JavaScript Object Notation)**
+ **XML (eXtensible Markup Language)**

Оба служат **для передачи структурированных данных**, но выглядят и работают по-разному.

 
# JSON

**JSON** – лёгкий формат обмена данными, основанный на синтаксисе JavaScript‑объектов.

**Синтаксис**:

+ **Объекты** – пары «ключ: значение» в фигурных скобках `{}`.
+ **Массивы** – список значений в квадратных скобках `[]`.
+ **Значения** – строки, числа, логические значения, `null`, объекты, массивы.
+ **Ключи** – всегда строки в двойных кавычках.

**Правила**:

+ только двойные кавычки (`"string"`);
+ запятые между элементами;
+ последний элемент без запятой.

Простой объект:
```
{
  "name": "Анна",
  "age": 30,
  "isStudent": false
}
```
                  
Массив объектов:
```
[
  {
    "id": 1,
    "title": "Пост 1"
  },
  {
    "id": 2,
    "title": "Пост 2"
  }
]
```
                  
Вложенная структура:
```
{
  "user": {
    "name": "Иван",
    "contacts": {
      "email": "ivan@example.com",
      "phone": "+79991234567"
    }
  },
  "posts": 5
}
```
                  
 

**Пример HTTP запроса с JSON**:

+ Клиент отправляет данные о новом пользователе на сервер
```
POST /api/users HTTP/1.1
Host: example.com
Content-Type: application/json
Content-Length: 56
Accept: application/json


{
  "name": "Анна",
  "email": "anna@example.com",
  "age": 28
}
```
                  
Разбор заголовков:

+ `Content-Type: application/json` – сообщает серверу, что тело запроса в формате JSON.
+ `Accept: application/json` – просит сервер вернуть ответ тоже в JSON.
+ `Content-Length` – длина тела запроса в байтах.

---
# XML

**XML** – расширяемый язык разметки для хранения и передачи структурированных данных.

**Синтаксис**:

+ **Элементы** – теги в угловых скобках `<tag>` и `</tag>`.
+ **Атрибуты** – дополнительные данные внутри открывающего тега.
+ **Текстовое содержимое** — между открывающим и закрывающим тегом.
+ **Комментарии** – `<!-- комментарий -->`.
+ **Декларация XML** – `<?xml version="1.0" encoding="UTF-8"?>` (опционально).

**Правила**:

+ все теги должны быть закрыты;
+ вложенность строго соблюдается;
+ имена тегов чувствительны к регистру;
+ атрибуты в кавычках (`"` или `'`).

Простой документ:
```
<person>
  <name>Анна</name>
  <age>30</age>
  <isStudent>false</isStudent>
</person>
```
                  
С атрибутами:
```
<book id="123" genre="фантастика">
  <title>Дюна</title>
  <author>Фрэнк Герберт</author>
  <year>1965</year>
</book>
```
                  
Вложенная структура:
```
<library>
  <book id="1">
    <title>Война и мир</title>
    <author>Лев Толстой</author>
  </book>
  <book id="2">
    <title>Преступление и наказание</title>
    <author>Фёдор Достоевский</author>
  </book>
</library>
```
                  
 

**Пример HTTP запроса с XLM**:

+ Клиент отправляет заказ на сервер
```
POST /api/orders HTTP/1.1
Host: example.com
Content-Type: application/xml
Content-Length: 158
Accept: application/xml


<?xml version="1.0! encoding="UTF-8"?>
<order>
  <item>Ноутбук</item>
  <quantity>1</quantity>
  <price>79990</price>
  <customer>
    <name>Иван</name>
    <email>ivan@example.com</email>
  </customer>
</order>
```
                  
Разбор заголовков:

+ `Content-Type: application/xml` – тело запроса в формате XML.
+ `Accept: application/xml` – ожидается ответ в XML.
