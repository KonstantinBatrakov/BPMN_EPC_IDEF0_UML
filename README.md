# BPMN_EPC_IDEF0_UML
## 1-2 это файлы UML диагарммы классов. Созданы в DRAWIO. разобраны 2 примера
1. Пример работы банкомата. Где определены сущности (Банк, Банкомат, Аккаунт, КЛиент, Карта, Транзакция), связи между ними, атрибуты и выделены методы. 
2. Типовой пример с Системой заказов с сущностями, связями, атрибутами и методами.
3. UML-диаграмма последовательности. объекты: Пользователь; страница оплаты сайта учебного центра (Сайт УЦ); СУБД УЦ; Платежный шлюз; Антифрод-система.
Постановка задачи: описание бизнес-процесса
Предположим, пользователь — посетитель сайта хочет купить курс по бизнес-анализу и оплатить его онлайн банковской картой. При этом он может получить скидку, применив промокод. Промокод действует только на определенный курс и ограничен по времени. Данные о промокоде хранятся в СУБД Учебного Центра (УЦ): сам промокод, курс, на который он распространяется, размер скидки, срок действия (дата валидности) и состояние (новый, выдан, использован, истек). Сам процесс оплаты, т.е. непосредственного списания денег с банковской карты выполняется на стороне банковского платежного шлюза. Выполняемую при этом последовательность шагов можно упрощенно представить следующим образом:
4. 



## ПОДРОБНЕЕ по п.3 
— пользователь выбирает курс по бизнес-анализу и нажимает кнопку «Купить»;

— открывается страница оплаты курса на сайте учебного центра с формой договора покупки курса и чек-боксом о наличии промокода;

— пользователь вводит свои данные в форму договора покупки курса;

— пользователь отмечает наличие промокода в чек-боксе;

— открывается поле ввода промокода и кнопка проверки его валидности;

— пользователь вводит промкод;

— пользователь проверяет его валидность, кликнув на кнопку «Проверить»;

— выполняется проверка валидности промокода с учетом данных по нему, которые имеются в СУБД УЦ.

— Если промокод валиден (т.е. привязан к выбранному курсу и дата действия его еще не истекла) и находится в состоянии «выдан», цена курса меняется с учетом скидки по промокоду. Иначе цена курса остается прежней и пользователю показывается сообщение о невозможности применить этот код по одной из следующих причин: уже использован, не применим к выбранному курсу или закончился срок его действия.

— соглашаясь с ценой (пересчитанной или прежней), пользователь нажимает кнопку «Оплатить». При этом в сторону платежного шлюза посылается запрос со всеми параметрами заказа, где сумма списания равна итоговой цене, рассчитанной с учетом скидки по промокоду, если ее удалось применить.

— открывается веб-страница платежного шлюза с формой ввода данных банковской карты пользователя и суммой списания;

— пользователь вводит реквизиты своей банковской карты и нажимает кнопку «Оплатить». При этом на сервер банка в систему «Антифрод» отправляются детали заказа и данные карты, чтобы проверить заказ на мошенничество.

— в платёжный шлюз возвращаются результаты проверки заказа на мошенничество. Если заказ признан мошенническим, оплата отклоняется и платеж считается неуспешным. Иначе платёжный шлюз списывает деньги со счёта клиента.

— Платёжный шлюз возвращает сайту УЦ статус платежа (успешный или неуспешный).

— На странице оплату сайта УЦ отображается статус платежа.

— При успешном платеже в СУБД УЦ меняется состояние промокода на «Использован».


