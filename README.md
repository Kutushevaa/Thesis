# Thesis in English
Program code for the implementation of the project for the thesis on the graduation topic: "Development of salary systems"

Description of the technologies used to create the site

The business logic of the site is written in the popular IDE (integrated development environment) – IntelliJ IDEA. In the development environment itself, there are many embedded plugins, in our case, the CUBA Studio plugin is used. Various changes between the development environment and the plugin are quickly synchronized, so you can work in both of them. This plugin is used to perform a huge number of tasks related to the future site. Among them are the following:
   - setting up the internal component of projects: project files, build scripts;
   - changing UI design and a variety of data models;
   - create screens based on existing ones on the platform;
   - create a database (database) and enable automatic updates, etc.
CUBA has a three-layer architecture, in which the main (connecting) element is considered metadata-data about the data model in the application. Thanks to this metadata, the visual part of the program understands what data is displayed and how. For example, the table understands that it contains the attributes of the "employee" entity, and columns such as "full name", "mail", "salary" and the like automatically appear, and determines the format of the columns. 
Metadata also helps the visual part of the program to work with the database through ORM (object-relational mapping, or transformation). A person sets graphs for objects that the program needs to load and update in the future. The same actions occur in the security system, in the report sections, and in other parts of the platform.

After describing the main technology used to create a website, we will briefly describe what our corporate website is built on. We have 3 modules: core, global and web.

From the name, it is clear that global stores everything that is available in the entire application, and in core and in the web, entity classes and interfaces (control panel) of services are prescribed. If we look at the web separately, we can see how the screens are written-visually presented how they look and the logic of the site. In core, we mainly have scripts for initializing and updating the Database (DB).

Next, we have all the entities registered in global. Each entity has its own fields, for example, the working field entity has the following fields – "name", "position", "salary", etc. Since our entities are stored in a database, we write code and tell them in which table they are stored, and in the case of fields, in which column the field values are stored.

Accordingly, the annotation above the class:

   - @Table-indicates in which table the entity is stored, the annotation above the field;
  
   - @Column – in which column the field is stored;
  
   - there are also @NamePattern annotations above the entity – what is written in the annotation will light up in the user interface when, for example, the entity is displayed in a table;
  
   - @Entity - the name of the entity, it is necessary for the platform itself, the registration of the entity in the meta information, therefore, and the receipt of data in the screens from the database occurs through the name of the entity.
  
Next, some notation:

   - In fields @NotNull-means that the field cannot be empty;
  
   - @ManyToOne-joining another entity with a many-to-one relationship;
  
   - @JoinColumn, respectively, indicates in which column the key to the joined entity is stored.

The "Date" fields have an annotation that specifies the format in which the date is stored. Full date and time, date only, or time only.

   - @NumberFormat for fields of the BigDecimal type (it can work with integers or real numbers of any precision (bit depth) and tells us in what format the number will be stored.
  
   - We also have @MetaClass, for example, BaseWorkPrice, it is not stored in the database. 
  
   - And accordingly, the fields of such an entity are marked with @MetaProperty. 
  
  This is necessary so that the web layer and the platform as a whole can see this entity (add it to the meta information). Thus, this entity can be displayed in the table in the future without unnecessary problems. 
  
  
# Краткое описание на русском:
  
  Описание технологий, используемых при создании сайта

Бизнес-логика сайта прописывается в популярной IDE (интегрированная среда разработки) – IntelliJ IDEA. В самой среде разработке существует множество встраиваемых плагинов, в нашем случае используется плагин CUBA Studio. Различные изменения между средой разработки и плагином быстро синхронизируются, поэтому можно работать в них обоих. Данный плагин используется для осуществления огромного количества задач, связанных с будущим сайтом. Среди них можно выделить следующие:
   - настройка внутренней составляющей проектов: проектные файлы, скрипты для сборки;
   - изменение дизайна UI и разнообразие моделей данных;
   - создание экранов на основе уже существующих на платформе;
   - создание БД (база данных) и подключение функции автоматического обновления и т.д.
CUBA имеет трехслойную архитектуру, в которой основным (связующим) элементом считаются метаданные – данные о модели данных в приложении. Благодаря этим метаданным визуальная часть программы понимает, какие данные и как отображаются. К примеру, таблица понимает, что в ней находятся атрибуты сущности «работник», и автоматически появляются такие столбцы, как «ФИО», «почта», «оклад» и тому подобное и определяет формат колонок. 

Также метаданные помогают визуальной части программы работать с базой данных через ORM (объектно-реляционное отображение, или преобразование). Человек задает графы для объектов, которые программе необходимо прогрузить и в дальнейшем обновить. Такие же действия происходят в части системы безопасности, в разделах с отчетами и других частях платформы.

Описав главную технологию, используемую для создания сайта, коротко опишем то, на чем строится наш корпоративный сайт. У нас есть 3 модуля: core, global и web.
Из названия понятно, что в global хранится все то, что доступно во всем приложении, и в core и в web прописываются классы сущностей и интерфейсы (пульт управления) сервисов. Если рассматривать отдельно web, то мы можем увидеть, как прописаны экраны – визуально представлено то, как они выглядят и логика работы сайта. В core у нас в основном заложены скрипты инициализации и обновления Базы данных (БД).

Далее в global у нас прописаны все сущности. У каждой сущности свои поля, например, у сущности рабочего поля существуют следующие – «имя», «должность», «зарплата» и т.д. Так как наши сущности хранятся в базе данных, мы прописываем код и указываем им, в какой таблице они хранятся, и в случае полей, в каком столбце хранятся значения полей. 
Соответственно аннотация над классом:
   - @Table – указывает в какой таблице хранится сущность, аннотация над полем;
   - @Column – в какой колонке хранится поле; 
   - так же над сущностью есть аннотации @NamePattern – то что расписано в аннотации будет светится в пользовательском интерфейсе, когда, к примеру сущность выводится в таблицу;
   - @Entity - имя сущности, нужна для самой платформы, регистрация сущности в мета информации, следовательно, и получение данных в экранах из базы происходит через имя сущности.
Далее некоторые обозначения:
   - В полях @NotNull - означает что поле не может быть пустым;
   - @ManyToOne - присоединение другой сущности отношением многого к одному;
   - @JoinColumn, соответственно, указывает в какой колонке хранится ключ на присоединяемую сущность.

У полей «Дата» есть аннотация @Temporal указывает в каком формате хранится дата. Полностью дата и время, только дата или только время.
   - @NumberFormat у полей типа BigDecimal (может работать с целыми или вещественными числами любой точности (разрядности) и указывает нам, в каком формате будет хранится число. 
   - Также у нас существует @MetaClass, к примеру, BaseWorkPrice, оно не хранится в базе.
   - И соответственно, поля у такой сущности обозначены за @MetaProperty. 
   
Это нужно, чтоб web слой и платформа в целом видела эту сущность (добавила в метаинформацию). Таким образом эту сущность в дальнейшем можно без лишних проблем выводить в таблицу.

