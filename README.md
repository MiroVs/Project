# Парсинг новостного портала
### Проект: https://colab.research.google.com/drive/1e0n9qWXYjtF54irXxzzT5Cfqjy51Vdqi?usp=sharing
### Видео: https://drive.google.com/drive/folders/1jdA0eR-hRqTKPi5gUK0cLfLrW57AEgsJ?usp=sharing
##### Описание:
Данный проект создавался для того, чтобы производить парсинг новостного портала (конкретно в моем случае - игровые новости) и проводить последующий анализ.
К сожалению, сделать универсальный код, которыйы парсил бы сайты по любой ссылке сложно (или невозможно), так как структура большинства сайтов уникальна, поэтому, если мы захотим использовать мой код для парсинга другого сайта (не из примера), то придется также менять части кода страниц, которые этот код парсит.
Как же в принципе работает данный код?
Существуют специальные библиотеки для парсинга, которые будут вытягивать всю нужную (и не очень нужную) информацию, а затем обрабатывать их в читаемый вид. Для этих целей мы импортируем get из библиотеки requests (отвечает за вытягивание кода страницы) и BeautifulSoup из библиотеки bs4 (отвечает за обработку кода). Библиотека pandas поможет нам в визуализации полученных результатов парсинга, а counter из collections - в создании облака слов.
Основное тело программы (main) представляет из себя парсинг, обработку полученных результатов и их расфасовку в по спискам. Сначала программа парсит наш новостной портал, затем происходит обработка с помощью BeautifulSoup и в этом обработанном коде мы ищем блоки каждой новости, которые есть на странице (если посмотреть на код страницы сайта, то каждый новостной блок находится в div с классом item-grid not-img). После этого мы создали списки (делаем их глобальными, чтобы другие функции могли к ним обращаться) с текстами, заголовками, датой и тэгами, чтобы заполнить их с помощью цикла, который идет далее. Внутри каждого новостного блока каждый элемент (заголовок, текст и т.д.) находятся в своей части кода (например, заголовок находится в h2). Соответственно, цикл проверяет каждый новостной блок и добавляет в списки всю найденную нужную информацию исходя из их атрибутов. При вызове функции main результата мы не увидим, так как его необходимо визуализировать, чем будут заниматься следующие функции.
Функция df (сокращено от dataframe) помогает с визуализацией - она строит таблицу из тех списков, что были образованы в функции main, а также импортирует эту таблицу в эксель на ваш компьютер.
Функция bag создает облако слов - конкретно в этом коде она считает количество тэгов, которые были найдены, то есть можно посмотреть, сколько новостей относилось к той или иной тематике.
Функция last_post выдает информацию о самом новом посте с новостного портала.
