# AZSValidator
Валидатор автозаправок  
Результат работы валидатора https://mapillaryby.github.io/AZSValidator/result.html  

Принцип работы:  
* с сайта Белоруснефть получаем список всех заправок с их свойствами (виды топлива, наличие магазина и др.)
* для каждой станции создается список ключей, описывающих официальную информацию
    * АЗС или электрозаправка (amenity=fuel или amenity=charging_station)
    * brand=Белоруснефть (зашито)
    * operator=* (название организации со страницы детальной информации о заправке)
    * телефон contact_phone=+375[пробел][код города][пробел][местный номер] (скобки и тире удаляются)
    
    * виды топлива fuel:*=yes (поддерживаются diesel, octane_92, octane_95, octane_98, adblue)
    * магазин shop=convenience
    * пылесос vacuum_cleaner=yes
    * подкачка колес compressed_air=yes
    * бесплатный Wi-Fi internet_access=wlan+internet_access:fee=no
    * терминал самообслуживания self_service=yes
    * время работы opening_hours=* (24/7 либо дни недели и часы если неполный рабочий день)
    * электрические разъемы для зарядки socket:*=[количесво] (поддерживаются type2, type2_combo, chademo, значение ЕвропаSaeCombo2 мапиться в unknown)
    * уникальный номер автозаправки guid:belorisneft=[номер]
* ищем в OpenStreetMap заправку по специальному ключу, если не найден, то запрашиваем в примерной области нахождения заправки объекты, содержащие слово Белоруснефть
* в созданом списке ключей раскрашиваем красным ключи, отсутсвующие у найденого объекта 
    * сейчас раскрашиваются не все ключи, только виды топлива, наличие магазина, подкачки колес, пылесоса и интернета, терминал саммобслуживания, время работы
* список сохраняется в файл и публикуется как GitHub страница

