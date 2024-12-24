### Примерные показатели:

| Показатель | Значение |
|---|---|
| Region | Сахалинская область |
| Population | 500,000 |
| DAU (Daily Active Users) | 75,000 |
| RPS (Requests Per Second) | ~1 |

### User Story
<p>1.Как клиент автомойки, я хочу получать уведомление о возможных акциях и специальных предложениях, чтобы максимально экономить на услугах мойки автомобиля.</p>
<p>2.Как клиент автомойки, я хочу иметь возможность бронировать услугу мойки онлайн, чтобы сэкономить время.</p>
<p>3.Как клиент автомойки, я хочу иметь возможность выбирать вид очистки салона машины (химчистка, пароочистка и т.д.), чтобы поддерживать комфорт в салоне.</p>
<p>4.Как клиент автомойки, я хочу, чтобы персонал был дружелюбным и приветливым, чтобы оставаться довольным обслуживанием.</p>
<p>5.Как клиент автомойки, я хочу иметь возможность купить абонемент на мойку автомобиля, чтобы экономить на регулярных процедурах уборки.</p>
<p>6.Как клиент автомойки, я хочу иметь возможность оплачивать услугу мойки онлайн, чтобы избежать очередей и сэкономить время.</p>
<p>7.Как клиент автомойки, я хочу иметь возможность заказать дополнительные услуги (полировка, нанесение защитного покрытия), чтобы автомобиль выглядел как новый.</p>
<p>8.Как клиент автомойки, я хочу, чтобы мой автомобиль был вымыт вручную, чтобы избежать повреждений кузова от автоматических моек.</p>
<p>9.Как клиент автомойки, я хочу, чтобы на автомойке была зона отдыха, чтобы я мог отдохнуть, пока мой автомобиль моется.</p>
<p>10.Как клиент автомойки, я хочу видеть чистоту и порядок на территории автомойки, чтобы быть уверенным в профессионализме и ответственности персонала.</p>

### Функциональные требования:
### Use Case 

![image](https://github.com/user-attachments/assets/0ef1878f-b764-4153-97c0-9de30895115d)

<details>
  <summary> Код для Use Cases (PlantTextUML)</summary>
	
```
@startuml
actor "Клиент" as fc
left to right direction
rectangle "ВсеМойки.ру"  {
  rectangle "Платёжная штука" as plata
  usecase "UC1: Записаться на мойку" as UC1
	usecase "UC1.1: Найти и выбрать автомойку" as UC2
	usecase "UC1.2: Выбрать дату и время" as UC3
	usecase "UC1.3: Выбрать услугу" as UC4
	usecase "UC1.4: Оплатить" as UC6
	usecase "UC2: Отменить услугу" as UC7
}
fc --> UC1
fc --> UC7
UC7 <. UC1:(extend)
UC1 ..> UC2:(include)
UC1 ..> UC3:(include)
UC1 ..> UC4:(include)
UC1 ..> UC6:(include)
UC6 -->plata
@enduml
```
</details>


### Сценарии использования:  
### UC1: Записаться на мойку 
- Участники: пользователь приложения
- Предусловия: пользователь нашел и  выбрал автомойку из списка, выбрал дату и время, выбрал услугу, ввел данные, подтвердил свои персональные данные
- Условия для запуска сценария: пользователь приложения нажал кнопку Записаться, ввел данные, подтвердил номер телефона
- Признак успешности: пользователь записался на мойку, высвечивается уведомление Вы успешно записаны на автомойку!
 ### Базовый сценарий:	
 <ol>
<li> Выходит окно, что пользователь успешно записался на автомойку </li>
<p>🔄 1.1. Альтернативный сценарий: Нет соединения с Интернетом: Выдать пользователю ошибку соединения. Можно позвонить администратору Автомойки и записаться. </p>
<p>🔄 1.2. Альтернативный сценарий : Ошибка на сервере: Собщить пользователю, что ведутся технические работы в системе. Попросить зайти позже. Либо позвонить администратору автомойки и записаться по телефону.</p>
	 </ol>
  
 ### UC1_1: Найти и выбрать автомойку 
- Участники: пользователь приложения
- Предусловия: пользователь зашел в приложение
- Условия для запуска сценария: пользователь приложения нажимает кнопку Найти мойку
- Признак успешности: Пользователь видит список моек на экране и из списка выбирает одну
 ### Базовый сценарий:	
 <ol>
<li> Система предлагает использовать геолокацию пользователя </li>
	 <li>Eсли пользователь согласился дать геолокацию, то:  
	 <ul>
				<li>Система ищет ближайшие к пользователю автомойки на карте </li>
				<li>Система возвращает карту или список ближайших автомоек</li>
			</ul>
	 </li>
	 <li>Если пользователь отказался:
			<ul>
				<li>Система выводит список всех автомоек его города </li>
			</ul>
		 </li>
		<li>Пользователь выбирает автомойку из списка или указывает ее на карте.</li>
	</ol>
<p>🔄 1_1.1. Альтернативный сценарий: Нет соединения с Интернетом: Выдать пользователю ошибку соединения. Можно позвонить администратору Автомойки и записаться. </p>
<p>🔄 1_1.2. Альтернативный сценарий: Ошибка на сервере: Собщить пользователю, что ведутся технические работы в системе. Попросить зайти позже. Либо позвонить администратору автомойки и записаться по телефону.</p>
<p>🔄 1_1.3. Альтернативный сценарий: Выбраная мойка закрыта: Сообщить пользователю что выбранная им мойка закрыта и предложить ему выбрать другую.</p>
	 </ol>
  
  ### UC1_2: Выбрать дату и время 
- Участники: пользователь приложения
- Предусловия: пользователь выбрал автомойку из списка
- Условия для запуска сценария: пользователь приложения нажимает кнопку "Выбрать дату и время"
- Признак успешности: Пользователь видит список свободных слотов на запись
 ### Базовый сценарий:	
 <ol>
<li> Система находит указанную мойку в базе данных и выводит список дат, в которые можно записаться </li>
<li>Пользователь выбирает определенную дату и время из списка свободных записей </li>		
	</ol>
<p>🔄 1_2.1. Альтернативный сценарий: Нет соединения с Интернетом: Выдать пользователю ошибку соединения. Можно позвонить администратору Автомойки и записаться. </p>
<p>🔄 1_2.2. Альтернативный сценарий: Ошибка на сервере: Собщить пользователю, что ведутся технические работы в системе. Попросить зайти позже. Либо позвонить администратору автомойки и записаться по телефону.</p>
<p>🔄 1_2.3. Альтернативный сценарий: Выбраная мойка закрыта: Сообщить пользователю что выбранная им мойка закрыта и предложить ему выбрать другую.</p>
	 </ol>
  
  ### UC1_3: Выбрать услугу 
- Участники: пользователь приложения
- Предусловия: пользователь выбрал автомойку из списка, затем выбрал дату и время записи и подтвердил свои данные
- Условия для запуска сценария: пользователь приложения нажимает кнопку "Выбрать услугу"
- Признак успешности: Пользователь видит список услуг, предоставляемых данной мойкой и выбирает подходящую 
 ### Базовый сценарий:	
 <ol>
<li> Система находит указанную мойку в БД и выводит услуги, которые она предоставляет </li>
<li> Пользователь выбирает услугу из списка и нажимает кнопку "записаться" </li>		
	</ol>
<p>🔄 1_3.1. Альтернативный сценарий: Нет соединения с Интернетом: Выдать пользователю ошибку соединения. Можно позвонить администратору Автомойки и записаться. </p>
<p>🔄 1_3.2. Альтернативный сценарий: Ошибка на сервере: Собщить пользователю, что ведутся технические работы в системе. Попросить зайти позже. Либо позвонить администратору автомойки и записаться по телефону.</p>
<p>🔄 1_3.3. Альтернативный сценарий: Выбранная услуга в данный момент недоступна: Сообщить пользователю, что выбранная им услуга недоступна и предложить ему выбрать другую.</p>
	 </ol>
  
  ### UC1_4: Оплатить 
- Участники: пользователь приложения
- Предусловия: пользователь выбрал автомойку из списка, выбрал дату и время, выбрал услугу, ввел данные, подтвердил номер телефона
- Условия для запуска сценария: пользователь нажал кнопку "записаться", ввел данные и подтвердил запись
- Признак успешности: оплата  прошла успешно либо пользователь выбрал другой способ оплаты (наличными).
 ### Базовый сценарий:	
 <ol> 
<p>Если пользователь выбрал оплатить онлайн, то: </p>
<li> Пользователю выводится стоимость всех услуг </li>
<li> Пользователь выбирает способ оплаты, оплачивает </li>
<li>Уведомление пользователя об успешной операции.</li>  </ol>	
<ol><p>Иначе, если пользователь выбрал офлайн оплату:</p>
<li>Пользователю выводится стоимость всех услуг</li>	
<li>Пользователь нажимает кнопку "Оплатить на мойке" </li>
<li>Уведомление пользователя об успешном выборе</li>
	</ol>
<p>🔄 1_4.1. Альтернативный сценарий: Нет соединения с Интернетом: Выдать пользователю ошибку соединения. Можно позвонить администратору Автомойки и записаться. </p>
<p>🔄 1_4.2. Альтернативный сценарий: Ошибка на сервере: Собщить пользователю, что ведутся технические работы в системе. Попросить зайти позже. Либо позвонить администратору автомойки и записаться по телефону.</p>
<p>🔄 1_4.3. Альтернативный сценарий: Ошибка, оплата не прошла: Сообщить пользователю, что оплата не прошла, попросить оплатить офлайн на мойке либо попробовать еще раз.</p>
	 </ol>
  
### UC2: Отменить услугу
- Участники: пользователь приложения
- Предусловия: пользователь записался на мойку
- Условия для запуска сценария: пользователь приложения нажал кнопку "Отменить запись"
- Признак успешности: запись пользователя отменяется
 ### Базовый сценарий:	
 <ol> 
<li> Пользователь вводит свой номер телефона и подтверждает его </li>
<li> Пользователь нажимает на кнопку "Мои услуги" </li>
<li> Система обращается к базе данных и выводит список услуг по данному номеру с текущей даты</li>  
<li>Пользователь выбирает запись и нажимает кнопку "отменить"</li>   
<li>Уведомление пользователя об успешной отмене записи</li>  
	 
<p>🔄 2_1. Альтернативный сценарий: Нет соединения с Интернетом: Выдать пользователю ошибку соединения. Можно позвонить администратору Автомойки и записаться. </p>
<p>🔄 2_2. Альтернативный сценарий: Ошибка на сервере: Собщить пользователю, что ведутся технические работы в системе. Попросить зайти позже. Либо позвонить администратору автомойки и записаться по телефону.</p>
</ol>

 ### UC3: ТехПоддержка
- Участники: пользователь приложения
- Предусловия: пользователь велл номер телефона и подтвердил его
- Условия для запуска сценария: пользователь приложения нажал кнопку "Техническая поддержка"
- Признак успешности: пользователь связался с технической поддержкой
 ### Базовый сценарий:	
 <ol> 
<li> Пользователь вводит свой номер телефона и подтверждает его </li>
<li> Пользователь нажимает на кнопку "Техническая поддержка" </li>
<li> Система проверяет список свободных сотрудников</li>  
<li>Система создает чат технической поддержки между свободным сотрудником и пользователем</li>   
<li>Система организует передачу сообщений между пользователем и технической поддержкой</li>  
	 
<p>🔄 2_1. Альтернативный сценарий: Нет соединения с Интернетом: Выдать пользователю ошибку соединения. Можно позвонить администратору Автомойки и записаться. </p>
<p>🔄 2_2. Альтернативный сценарий: Ошибка на сервере: Собщить пользователю, что ведутся технические работы в системе. Попросить зайти позже. Либо позвонить администратору автомойки и записаться по телефону.</p>
	
</ol>
	

### ER-Модель:
                            
 


![image](https://github.com/user-attachments/assets/9e4f01f6-948d-4d8b-9ac6-48c7f0ec4019)





### C4 model

#### C1 - System Context
![image](https://github.com/user-attachments/assets/547b94e1-6d4a-48cf-906f-17a3a8cbb8e3)



#### C2 - Containers
![image](https://github.com/user-attachments/assets/2f651453-550c-463d-80b9-8a329a53a404)



### Sequense Diagram

![image](https://github.com/user-attachments/assets/03ac302d-9318-4bf9-ad65-fdc8f6d58cc8)

<details>
  <summary> Код Sequense Diagram (PlantTextUML)</summary>

```
@startuml
' Участники
actor "Клиент" as Client
participant "Веб-приложуха/Мобилка" as CarWashSystem
participant "API" as ServiceOrderAPI
database "БазаДанных" as Database
participant "ПлатежнаяСистема" as PaymentSystem
participant "Техподдержка" as Support

' Запрос на выбор автомойки
Client -> CarWashSystem: Запрос на выбор автомойки
CarWashSystem -> Database: Запрос на выбор автомойки
Database --> CarWashSystem: Список автомоек
CarWashSystem -> CarWashSystem: Сортировка списка автомоек
CarWashSystem -> Client: Список автомоек

' Запрос на выбор услуги
Client -> ServiceOrderAPI: Запрос на выбор услуги
ServiceOrderAPI -> Database: Запрос на услуги
Database --> ServiceOrderAPI: Список услуг
ServiceOrderAPI --> Client: Список услуг

' Запрос на выбор даты и времени
Client -> ServiceOrderAPI: Запрос на выбор даты и времени
ServiceOrderAPI --> Client: Подтверждение даты и времени

' Подтверждение записи
Client -> ServiceOrderAPI: Запрос на подтверждение записи
ServiceOrderAPI -> Database: Запрос на добавление записи в БД
Database --> ServiceOrderAPI: Подтверждение добавления
ServiceOrderAPI --> Client: Запись подтверждена

' Запрос на оплату заказа
Client -> PaymentSystem: Запрос на оплату заказа
PaymentSystem -> Database: Запрос на получение информации о заказе
Database --> PaymentSystem: Информация о заказе
PaymentSystem --> Client: Способ оплаты
Client -> PaymentSystem: Выбор способа оплаты

' Обработка оплаты
PaymentSystem -> PaymentSystem: Запрос на оплату заказа
alt Успешная оплата
    PaymentSystem --> Client: Подтверждение оплаты
    PaymentSystem -> ServiceOrderAPI: Обновление статуса заказа
    ServiceOrderAPI -> Database: Запрос на изменение статуса заказа
    Database --> ServiceOrderAPI: Изменение статуса заказа
    ServiceOrderAPI --> PaymentSystem: Статус заказа изменён
    PaymentSystem --> Client: Заказ оплачен
else Ошибка оплаты
    PaymentSystem --> Client: Ошибка оплаты
    Client -> Support: Обращение в техподдержку
    Support -> Client: Поддержка клиента
end

@enduml

```
</details>

 ### API  
 <details>
	 <summary> Код API (PlantTextUML)</summary>
	 
	 
  ```

 openapi: 3.0.0
info:
  title: "Сервис записи на автомойку"
  version: "0.1"
paths:
  /users:
    get:
      summary: "Список пользователей"
      tags:
        - Пользователи
      operationId: getAllUsers
      responses: 
        "200":
          description: "Успешный ответ со списком пользователей"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Users"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    post:
      summary: "Создать пользователя"
      tags:
        - Пользователи
      operationId: createUser
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: "#/components/schemas/User"
      responses: 
        "201":
          description: "Успешный ответ с созданным пользователем"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/User"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"            
  /users/{user_id}:
    get:
      summary: "Вывод по пользователя по ID"
      tags:
        - Пользователи
      operationId: getUserById
      parameters:
        - name: user_id
          in: path
          required: True
          description: "ID Пользователя"
          schema:
            type: integer
          example: 1
      responses: 
        "200":
          description: "Успешный ответ с ID пользователя"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/User"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    delete:
      summary: "Удаление пользователей по ID"
      tags:
        - Пользователи
      operationId: deleteUser
      parameters:
          - name: user_id
            in: path
            required: True
            description: "Идентификатор клиента"
            schema:
              type: integer
            example: 1
      responses:
        "200":
            description: "Успешный удаление"
            content:
              application/json: {}
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    put:
      summary: "Изменить пользователя"
      tags:
        - Пользователи
      operationId: updateUserById
      parameters:
        - name: user_id
          in: path
          required: True
          description: "ID пользователя"
          schema:
            type: integer
          example: 1
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: "#/components/schemas/User"
      responses: 
        "200":
          description: "Операция прошла успешно"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/User"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
                
  /carwashers:
    get:
      summary: "Список автомоек"
      tags:
        - Автомойки
      operationId: getAllCarwashes
      responses: 
        "200":
          description: "Успешный ответ со списком автомоек"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/CarWashes"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    post:
      summary: "Создать автомойку"
      tags:
        - Автомойки
      operationId: createCarWash
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: "#/components/schemas/CarWash"
      responses: 
        "201":
          description: "Успешный ответ с созданной автомойкой"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/CarWash"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"            
  /carwashes/{carwash_id}:
    get:
      summary: "Поиск автомойки по ID"
      tags:
        - Автомойки
      operationId: getCarwashById
      parameters:
        - name: carwash_id
          in: path
          required: True
          description: "ID автомойки"
          schema:
            type: integer
          example: 1
      responses: 
        "200":
          description: "Успешный ответ с IDавтомойкой"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/CarWash"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    delete:
      summary: Удаление автомойки по ID
      tags:
        - Автомойки
      operationId: deleteСarWash
      parameters:
          - name: carwash_id
            in: path
            required: True
            description: "ID автомойки"
            schema:
              type: integer
            example: 1
      responses:
        "200":
            description: "Успешное удаление автомойки"
            content:
              application/json: {}
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    put:
      summary: " Изменения данных автомойки по ID"
      tags:
        - Автомойки
      operationId: updateCarWashById
      parameters:
        - name: carwash_id
          in: path
          required: True
          description: "ID автомойки"
          schema:
            type: integer
          example: 1
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: "#/components/schemas/CarWash"
      responses: 
        "200":
          description: "Успешное изменение данных автомойки"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/User"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
                
  
  /services:
    get:
      summary: "Список услуг"
      tags:
        - Услуги
      operationId: getAllServices
      responses: 
        "200":
          description: "Успешный ответ со списком услуг"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Services"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    post:
      summary: "Создать услугу"
      tags:
        - Услуги
      operationId: createService
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: "#/components/schemas/Service"
      responses: 
        "201":
          description: "Успешный ответ с созданной услугой"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Service"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"        
  /services/{service_id}:
    get:
      summary: "Поиск услуги  по ID"
      tags:
        - Услуги
      operationId: getServiceById
      parameters:
        - name: service_id
          in: path
          required: True
          description: "ID услуги"
          schema:
            type: integer
          example: 1
      responses: 
        "200":
          description: "Успешный ответ с одной услугой"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Service"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    delete:
      summary: Удаление услуги по ID
      tags:
        - Услуги
      operationId: deleteService
      parameters:
          - name: service_id
            in: path
            required: True
            description: "ID услуги"
            schema:
              type: integer
            example: 1
      responses:
        "200":
            description: "Успешное удаление"
            content:
              application/json: {}
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    put:
      summary: " Изменениe данных услуги по ID"
      tags:
        - Услуги
      operationId: replaceServiceById
      parameters:
        - name: service_id
          in: path
          required: True
          description: "ID услуги"
          schema:
            type: integer
          example: 1
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: "#/components/schemas/Service"
      responses: 
        "200":
          description: "Успешное изменение данных услуги"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Service"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    
    
  /registrations:
    get:
      summary: "Список всех записей"
      tags:
        - Регестрация
      operationId: getAllRegistrations
      responses: 
        "200":
          description: "Успешный ответ со списком записей"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Registrations"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    post:
      summary: "Создать запись"
      tags:
        - Регестрация
      operationId: createRegistration
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: "#/components/schemas/Registration"
      responses: 
        "201":
          description: "Успешный ответ с созданной записью"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Registration"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"            
  /registrations/{registration_id}:
    get:
      summary: "Запись по ID"
      tags:
        - registrations
      operationId: getRegistrationById
      parameters:
        - name: registration_id
          in: path
          required: True
          description: "ID записи"
          schema:
            type: integer
          example: 1
      responses: 
        "200":
          description: "Успешный ответ с одной записью"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Registration"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    delete:
      summary: Eдалениe записи по ID
      tags:
        - registrations
      operationId: deleteRegistration
      parameters:
          - name: registration_id
            in: path
            required: True
            description: "ИID  записи"
            schema:
              type: integer
            example: 1
      responses:
        "200":
            description: "Успешный удаление"
            content:
              application/json: {}
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"
    patch:
      summary: "Изменение данных записи по ID"
      tags:
        - registrations
      operationId: updateRegistrationById
      parameters:
        - name: registration_id
          in: path
          required: True
          description: "ID  записи"
          schema:
            type: integer
          example: 1
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: "#/components/schemas/Registration"
      responses: 
        "200":
          description: "Успешное изменение данных записи"
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Registration"
        "default":
          description: Ошибки
          content:
            application/json:
              schema:
                $ref: "#/components/schemas/Error"            
            
components:
  schemas:
    User:
      type: object
      required:
        - phone
      properties:
        user_id:
          type: integer
          example: 1
        phone:
          type: string
          example: "+7914231854"
    Users:
      type: array
      items:
        $ref: "#/components/schemas/User"
    Error:
      type: object
      required:
        - code
        - message
      properties:
        code:
          type: integer
          example: "404"
        message:
          type: string
          example: "Cервак умер :c"
    CarWash:
      type: object
      required:
        - name
        - address
        - phoneNumber
      properties:
        carWash_id:
          type: integer
          example: 1
        name:
          type: string
          example: "Лакшери автомойка"
        address:
          type: string
          example: "Южно-сахалинская 29, г. Южно-Сахалинск"
        phoneNumber:
          type: string
          example: "24-34-22"
    CarWashes:
      type: array
      items:
        $ref: "#/components/schemas/CarWash"
        
     
        
    Service:
      type: object
      required:
        - name
        - cost
      properties:
        service_id:
          type: integer
          example: 1
        name:
          type: string
          example: "Мойка три в одном"
        cost:
          type: integer
          example: 600
        duration:
          type: integer
          example: 15
        description:
          type: string
          example: "Мойка, шлефовка, палировка"
    Services:
      type: array
      items:
        $ref: "#/components/schemas/Service"
        
  
          
    Registration:
      type: object
      required:
        - user_id
        - carwash_id
        - carbox_id
        - service_id
        - gosauto_number
        - register_date
        - status
        
      properties:
        id:
          type: integer
          example: 1
        user_id:
          type: integer
          example: 1
        carwash_id:
          type: integer
          example: 1
        carbox_id:
          type: integer
          example: 1
        service_id:
          type: integer
          example: 1
        gosauto_number:
          type: string
          example: "рус324бек"
        register_date:
          type: string
          example: '24.01.2024'
        status:
          type: string
          example: 'Готово'
        
    Registrations:
      type: array
      items:
        $ref: "#/components/schemas/Registration"   
	
  ```
 </details>

