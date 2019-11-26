# AZSValidator
Валидатор автозаправок  
Результат работы валидатора https://mapillaryby.github.io/AZSValidator/result.html  

Принцип работы:  
* с сайта-источника  получаем список всех заправок с их свойствами (виды топлива, наличие магазина и др.)
* для каждой станции создается список ключей, описывающих официальную информацию
<table>
   <tr>
      <td>Сервис</td><td>Белоруснефть</td><td>Газпромнефть</td><td>Tatneft</td><td>Лукойл</td>
   </tr>
   <tr><td>Вид заправки</td><td>АЗС или электрозаправка</td><td>Заправка</td><td>Заправка</td><td>Заправка</td></tr>
   <tr><td>name=/td><td>Белоруснефть №[номер]</td><td>Газпромнефть №[номер]</td><td>Татнефть №[номер]</td><td>Лукойл  №[номер]</td></tr>
   <tr><td>brand</td><td>Белоруснефть</td><td>Газпромнефть</td><td>Tatneft</td><td>Лукойл</td></tr>
   <tr><td>operator</td><td>с сайта</td><td>ИООО "Газпромнефть-Белнефтепродукт"</td><td>ИООО "Татбелнефтепродукт"</td><td>с сайта</td></tr>
   <tr><td>contact:phone в формате +375[пробел][код города][пробел][местный номер]</td><td>с сайта</td><td></td><td></td><td></td></tr>
   <tr><td>contact:website</td><td>страница заправки</td><td>https://gpnbonus.by/</td><td>https://tatbelneft.by/azs/spisok-azs/</td><td>страница заправки</td></tr>
   <tr><td>fuel:*</td><td>diesel, octane_92, octane_95, octane_98, adblue, adblue:canister, HGV_diesel</td>
                      <td></td><td></td><td></td></tr>
   <tr><td>Пылесос vacuum_cleaner</td><td></td><td></td><td></td><td></td></tr>
   <tr><td>Подкачка compressed_air</td><td></td><td></td><td></td><td></td></tr>
   <tr><td>Wi-Fi</td><td></td><td></td><td></td><td></td></tr>
   <tr><td>терминал самообслуживания self_service</td><td></td><td></td><td></td><td></td></tr>
   <tr><td>opening_hours</td><td>+ (без газа)</td><td>+</td><td>-</td><td>+</td></tr>
   <tr><td>ref</td><td>[тип] [номер]</td><td>[номер]</td><td>[номер]</td><td>[номер]</td></tr>
   <tr><td>спец.теги</td><td>guid:belorisneft=[guid]</td><td>-</td><td>-</td><td>-</td></tr>
   <tr><td>электроразъемы socket:*=[количесво]</td><td>поддерживаются type2, type2_combo, chademo, значение ЕвропаSaeCombo2 мапиться в unknown</td><td>-</td><td>-</td><td>-</td></tr>
   <tr><td>мойка</td><td></td><td></td><td></td><td></td></tr>
   <tr><td>магазин</td><td></td><td></td><td></td><td></td></tr>
   <tr><td>кафе</td><td></td><td></td><td></td><td></td></tr>
   <tr><td>душ</td><td>+</td><td>-</td><td>+</td><td>-</td></tr>
   <tr><td></td><td></td><td></td><td></td><td></td></tr>
   </table>  
   
* ищем в OpenStreetMap заправку по специальному ключу, если не найден, то запрашиваем в примерной области нахождения заправки объекты, название бренда
* в созданом списке ключей раскрашиваем красным ключи, отсутсвующие у найденого объекта 
    * сейчас раскрашиваются не все ключи, только виды топлива, наличие магазина, подкачки колес, пылесоса и интернета, терминал саммобслуживания, время работы
* список сохраняется в файл и публикуется как GitHub страница

