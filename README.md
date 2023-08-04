#### Задача:
Исследовать поведение пользователей мобильного приложения продаж продуктов питания: 
 - изучить воронку продаж:
   - как пользователи доходят до покупки;
   - сколько пользователей доходит до покупки, а сколько — «застревает» на предыдущих шагах? На каких именно?
 - исследовать результаты A/A/B-эксперимента: поменять шрифты во всём приложении.

Пользователей разбили на 3 группы: 2 контрольные со старыми шрифтами и одну экспериментальную — с новыми. Выясните, какой шрифт лучше.

#### Описание данных
 
EventName — название события;
DeviceIDHash — уникальный идентификатор пользователя;
EventTimestamp — время события;
ExpId — номер эксперимента: 246 и 247 — контрольные группы, а 248 — экспериментальная.

#### Выводы: 

На начальном этапе у нас был датасет с небольшим количеством дубликатов (413 шт. 0,17%). Я заменила названия колонок на более корректные. Колонку датой и временем преобразовала в читаемый формат и вынесла отдельно колонку с датой.

Анализ данных показал, что у нас за данный промежуток с 25 июля по 8 августа есть 7551 уникальный пользователей и 243713 событий. В среднем 1 пользователь совершает 32 события, если берем моду, то 5 событий. Разница не большая, учитывая, что есть пользователи, которые совершили очень много событий, больше 2000.

Т.к. у нас частота событий большая была только в августе, то я отбросила до 1 августа все события, чтобы они не искажали данные. Потери данных были небольшими. Далее уже по очищенным данным посмотрели частоту событий. Получилось, что событие Tutorial практически не происходит и не вписывается в сценарий пути пользователя. Это событие я тоже отбросила. Далее построила воронку событий и посмотрела как пользователи перемещаются по ней. Выяснилось, что очень много отсеивается после того, как "набьют" корзину. 
Мои рекомендации: нужно исследовать почему много пользователей не оформляют заказ, может есть неудобство в интерфейсе или же в условиях доставки. Может нужно использовать инструмент "брошенная корзина", чтобы напомнить пользователям о том, что они не оформили заказ.
Дальше я рассмотрела эксперимент со шрифтами. Сравнила все группы друг с другом, а экспериментальную группу В дополнительно сравнила с объединенной контрольной группой (246 и 247). Получилось, что статистически значимых различий между группами на уровне alpha 0,01 не было найдено нигде. Получается, что эксперимент со шрифтами не принес никаких результатов. Таким образом, заказчику исследования нет смысла вкладывать бюджет в изменения шрифтов - изменение не принесет бизнесу дополнительной выручки.
