# hospital-data-base
<ol>
<li><strong> Постановка задачи</strong></li>
</ol>
<p><strong>1.1. Тема задачи и предметная область</strong></p>
<p>&nbsp;</p>
<p>Задача 2.32. Тема: &laquo;Больница&raquo;.</p>
<p>&nbsp;</p>
<p>Персонал. Должности. Специализации. Пациенты. Палаты. Операции.</p>
<p>&nbsp;</p>
<p><strong>1.2. Описание предметной области и требования к базе данных</strong></p>
<p>&nbsp;</p>
<p>Пациенты могут быть госпитализированы несколько раз по нескольким специализациям. Специализация подбирается в зависимости от того какой диагноз у пациента и исходя из этого подбирается нужный врач и палата. В зависимости от диагноза, некоторые пациенты могут быть прооперированы. У каждого врача есть своя должность, а должности, как и диагнозы, закреплены за специализацией.</p>
<p>&nbsp;</p>
<p>Нужно спроектировать базу данных, которая будет хранить данные о госпитализациях, врачах,&nbsp; видах специализаций и госпитализируемых пациентах.&nbsp; Основная задача-&nbsp; хранение информации о больнице и удобного доступа к ее архиву.</p>
<p>&nbsp;</p>
<ol start="2">
<li><strong> Моделирование базы данных </strong></li>
</ol>
<p><strong>2.1. Сущности и связи</strong></p>
<img src="https://github.com/DR-Dock/hospital-data-base/blob/master/%D1%81%D1%85%D0%B5%D0%BC%D0%B00.png">
<p>&nbsp;</p>
<p><strong>2.2. Схема </strong><strong>ER</strong><strong>-модели</strong></p>
<img src="https://github.com/DR-Dock/hospital-data-base/blob/master/%D1%81%D1%85%D0%B5%D0%BC%D0%B01.png">
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>2.3. Детализация </strong><strong>ER</strong><strong>-модели </strong></p>
<p><strong>2.3.1. Ключи</strong></p>
<p>&nbsp;</p>
<p>K0: Должность (№ Должности)</p>
<p>K1:&nbsp; Должность (№ Должности)</p>
<p>K2: Обслуживающий персонал (№ Кадра)</p>
<p>K3: Специализированные должности(№ Должности, № Специализации )</p>
<p>K5: Специализации (№ Специализации )</p>
<p>К55: Обслуживающий персонал (№ Специализации )</p>
<p>K6:&nbsp; Специализированные должности(№ Специализации)</p>
<p>K9: Палаты (№ Палаты, № Специализации)</p>
<p>K8: Палаты (№ Номер специализации)</p>
<p>K4: Лечащий персонал (№ Должности)</p>
<p>K15: Лечащий персонал (№ Кадра, № Специализации)</p>
<p>K66: Диагнозы ( № Диагноза, № Специализации)</p>
<p>K7: Диагнозы (№ Специализации)</p>
<p>K11: Пациенты (№ Пациента)</p>
<p>K30: Диапазоны (№ Даты)</p>
<p>K25: Диапазоны (№ Госпитализации)</p>
<p>K31: Операции (№ Даты)</p>
<p>K19: Операции (№ Операции)</p>
<p>К21: Операции (№ Госпитализации)</p>
<p>К13: Госпитализации (№ Диагноза)</p>
<p>К12: Госпитализации (№ Пациента)</p>
<p>К16: Госпитализации (№ Кадра)</p>
<p>К10: Госпитализации (№ Палаты)</p>
<p>К123: Госпитализации (№ Госпитализации)</p>
<p>К124: Госпитализации (№ Специализации)</p>
<p>&nbsp;</p>
<p><strong>2.3.2. Связи</strong></p>
<p>&nbsp;</p>
<p>C0 [1-N]: Должности (№ Должности) Должности без специализации.К0(№ Должности)</p>
<p>C1 [1-N]: Должности без специализации (№ Должности) &reg; Обслуживающий персонал.K1 (№ Должности)</p>
<p>C2 [1-N]: Должности (№ Должности) &reg; Специализированные должности.K0 (№ Должности)</p>
<p>C3 [1-N]: Специализации (№ Специализации) &reg; Специализированные должности.K6 (№ Типа)</p>
<p>C4 [1-N]: Специализации (№ Специализации) &reg; Палаты.K7 ((№ Специализации)</p>
<p>C22 [1-N]: Специализации(№ Специализации) &reg; Обслуживающий персонал.K5 (№ Специализации)</p>
<p>C33 [1-N]: Специализированные должности (№ Должности, № специализации) &reg;Лечащий персонал.K3 (№ Должности, № специализации)</p>
<p>C6 [1-N]: Специализированные должности (№ Номер Специализации) &reg; Диагнозы.К6(№ Номер специализации)</p>
<p>C11 [1-N]: Лечащий персонал (№ Кадра, № Номер специализации) &reg; Госпитализации.К15 (№ Кадра, № Номер специализации)</p>
<p>C7 [1-N]: Диагнозы(№ Диагноза, № Специализации) &reg; Госпитализации.K66 (№ Диагноза, № Специализации)</p>
<p>C8 [1-N]: Палаты (№ Палаты, № Специализации) &reg; Госпитализации.K9 (№ Палаты, № Специализации)</p>
<p>C9 [1-N]: Пациенты (№ Пациента) &reg; Госпитализации.K11 (№ Пациента)</p>
<p>C30 [1-N]: Госпитализации (№ Госпитализации) &reg; Диапазоны .K20 (№ Госпитализации)</p>
<p>C31 [1-N]: Диапазоны (№ Номер госпитализации, № Даты) &reg; Операции.K31 (№ Номер госпитализации, № Даты)</p>
<p>C10 [1-N]: Госпитализации(№ Номер госпитализации) &reg; Операции.K20 (№ Госпитализации)</p>
<p>C15 [1-N]: Тип Медали(№ Типа) &reg; Медали.K3 (№ Типа)</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>2.3.3. Свойства сущностей</strong></p>
<p>&nbsp;</p>
<p>Должность</p>
<table width="650">
<tbody>
<tr>
<td width="159">
<p>Атрибут</p>
</td>
<td width="160">
<p>Тип</p>
</td>
<td width="132">
<p>Ключ</p>
</td>
<td width="198">
<p>Описание</p>
</td>
</tr>
<tr>
<td width="159">
<p>№ Должности</p>
</td>
<td width="160">
<p>Числовой, счетчик</p>
</td>
<td width="132">
<p>К0</p>
</td>
<td width="198">
<p>Идентификатор должности</p>
</td>
</tr>
<tr>
<td width="159">
<p>Название</p>
</td>
<td width="160">
<p>Текс</p>
</td>
<td width="132">
<p>&nbsp;</p>
</td>
<td width="198">
<p>Название должности</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Специализация</p>
<table width="651">
<tbody>
<tr>
<td width="157">
<p>Атрибут</p>
</td>
<td width="156">
<p>Тип</p>
</td>
<td width="156">
<p>Ключ</p>
</td>
<td width="182">
<p>Описание</p>
</td>
</tr>
<tr>
<td width="157">
<p>№ Специализации</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>К5</p>
</td>
<td width="182">
<p>Идентификатор специализации</p>
</td>
</tr>
<tr>
<td width="157">
<p>Название</p>
</td>
<td width="156">
<p>Текст</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="182">
<p>Название специализации</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Палата</p>
<table width="650">
<tbody>
<tr>
<td width="156">
<p>Атрибут</p>
</td>
<td width="156">
<p>Тип</p>
</td>
<td width="156">
<p>Ключ</p>
</td>
<td width="182">
<p>Описание</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Специализации</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="182">
<p>Идентификатор специализации</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Палаты</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="182">
<p>Идентификатор палаты</p>
</td>
</tr>
<tr>
<td width="156">
<p>Количество мест</p>
</td>
<td width="156">
<p>Числовой</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="182">
<p>Количество мест в палате</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Специализированная должность</p>
<table width="650">
<tbody>
<tr>
<td width="156">
<p>Атрибут</p>
</td>
<td width="156">
<p>Тип</p>
</td>
<td width="156">
<p>Ключ</p>
</td>
<td width="182">
<p>Описание</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Специализации</p>
</td>
<td width="156">
<p>Числовой,счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="182">
<p>Идентификатор специализации</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Должности</p>
</td>
<td width="156">
<p>Числовой,счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="182">
<p>Идентификатор должности</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Должность без специализации</p>
<table width="650">
<tbody>
<tr>
<td width="156">
<p>Атрибут</p>
</td>
<td width="156">
<p>Тип</p>
</td>
<td width="156">
<p>Ключ</p>
</td>
<td width="182">
<p>Описание</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Должности</p>
</td>
<td width="156">
<p>Числовой,счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="182">
<p>№ должности без определённой специализации</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Обслуживающий персонал</p>
<table width="624">
<tbody>
<tr>
<td width="156">
<p>Атрибут</p>
</td>
<td width="156">
<p>Тип</p>
</td>
<td width="156">
<p>Ключ</p>
</td>
<td width="156">
<p>Описание</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Должности</p>
</td>
<td width="156">
<p>Числовой,счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор должности для работника</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Кадра</p>
</td>
<td width="156">
<p>Числовой,счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор кадра (работника)</p>
</td>
</tr>
<tr>
<td width="156">
<p>Фамилия</p>
</td>
<td width="156">
<p>Текст</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Фамилия кадра</p>
</td>
</tr>
<tr>
<td width="156">
<p>Имя</p>
</td>
<td width="156">
<p>Текст</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Имя кадра</p>
</td>
</tr>
<tr>
<td width="156">
<p>Отчество</p>
</td>
<td width="156">
<p>Текст</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Отчество кадра</p>
</td>
</tr>
<tr>
<td width="156">
<p>Номер специализации</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор специализации в которой работает данный кадр</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Пациент</p>
<table width="624">
<tbody>
<tr>
<td width="156">
<p>Атрибут</p>
</td>
<td width="156">
<p>Тип</p>
</td>
<td width="156">
<p>Ключ</p>
</td>
<td width="156">
<p>Описание</p>
</td>
</tr>
<tr>
<td width="156">
<p>Фамилия</p>
</td>
<td width="156">
<p>Текст</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Фамилия пациента</p>
</td>
</tr>
<tr>
<td width="156">
<p>Имя</p>
</td>
<td width="156">
<p>Текст</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Имя пациента</p>
</td>
</tr>
<tr>
<td width="156">
<p>Отчество</p>
</td>
<td width="156">
<p>Текст</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Отчество пациента</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ пациента</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>К11</p>
</td>
<td width="156">
<p>Идентификатор пациента</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Диагноз</p>
<table width="624">
<tbody>
<tr>
<td width="156">
<p>Атрибут</p>
</td>
<td width="156">
<p>Тип</p>
</td>
<td width="156">
<p>Ключ</p>
</td>
<td width="156">
<p>Описание</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Диагноза</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>К66</p>
</td>
<td width="156">
<p>Идентификатор диагноза</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Специализации</p>
</td>
<td width="156">
<p>Числовой Идентификатор</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор специализации для диагноза</p>
</td>
</tr>
<tr>
<td width="156">
<p>Название</p>
</td>
<td width="156">
<p>Текст</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Название диагноза</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Диапазон</p>
<table width="624">
<tbody>
<tr>
<td width="156">
<p>Атрибут</p>
</td>
<td width="156">
<p>Тип</p>
</td>
<td width="156">
<p>Ключ</p>
</td>
<td width="156">
<p>Описание</p>
</td>
</tr>
<tr>
<td width="156">
<p>Номер госпитализации</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="156">
<p>Дата</p>
</td>
<td width="156">
<p>Дата</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Дата для госпитализации</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Даты</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>К30</p>
</td>
<td width="156">
<p>Идентификатор даты</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>Лечащий персонал</p>
<table width="624">
<tbody>
<tr>
<td width="156">
<p>Атрибут</p>
</td>
<td width="156">
<p>Тип</p>
</td>
<td width="156">
<p>Ключ</p>
</td>
<td width="156">
<p>Описание</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Должности</p>
</td>
<td width="156">
<p>Числовой,счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор должности для врача</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Кадра</p>
</td>
<td width="156">
<p>Числовой,счётчик</p>
</td>
<td width="156">
<p>К15</p>
</td>
<td width="156">
<p>Идентификатор врача</p>
</td>
</tr>
<tr>
<td width="156">
<p>Фамилия</p>
</td>
<td width="156">
<p>Текст</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Фамилия врача</p>
</td>
</tr>
<tr>
<td width="156">
<p>Имя</p>
</td>
<td width="156">
<p>Текст</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Имя врача</p>
</td>
</tr>
<tr>
<td width="156">
<p>Отчество</p>
</td>
<td width="156">
<p>Текст</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Отчество врача</p>
</td>
</tr>
<tr>
<td width="156">
<p>Номер специализации</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор специализации в которой работает данный врач</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Госпитализация</p>
<table width="624">
<tbody>
<tr>
<td width="156">
<p>Атрибут</p>
</td>
<td width="156">
<p>Тип</p>
</td>
<td width="156">
<p>Ключ</p>
</td>
<td width="156">
<p>Описание</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Диагноза</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор диагноза для госпитализации</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Специализации</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор специализации</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Пациента</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор госпитализированного пациента</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Палаты</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор палаты для госпитализации</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Госпитаализации</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор госпитализации</p>
</td>
</tr>
<tr>
<td width="156">
<p>№ Кадра</p>
</td>
<td width="156">
<p>Числовой, счётчик</p>
</td>
<td width="156">
<p>&nbsp;</p>
</td>
<td width="156">
<p>Идентификатор кадра (лечащего врача)</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Операция</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<h2>3.Примеры данных</h2>
<p>Должности</p>
<table width="624">
<tbody>
<tr>
<td width="312">
<p>№ Должности</p>
</td>
<td width="312">
<p>Название</p>
</td>
</tr>
<tr>
<td width="312">
<p>1</p>
</td>
<td width="312">
<p>Мытьё.полов</p>
</td>
</tr>
<tr>
<td width="312">
<p>2</p>
</td>
<td width="312">
<p>Медсестра/Медбрат</p>
</td>
</tr>
<tr>
<td width="312">
<p>3</p>
</td>
<td width="312">
<p>Травмотолог</p>
</td>
</tr>
<tr>
<td width="312">
<p>4</p>
</td>
<td width="312">
<p>Доктор</p>
</td>
</tr>
<tr>
<td width="312">
<p>5</p>
</td>
<td width="312">
<p>Мастер по лёгким</p>
</td>
</tr>
<tr>
<td width="312">
<p>6</p>
</td>
<td width="312">
<p>Глазной</p>
</td>
</tr>
<tr>
<td width="312">
<p>7</p>
</td>
<td width="312">
<p>Выпрямитель</p>
</td>
</tr>
<tr>
<td width="312">
<p>8</p>
</td>
<td width="312">
<p>Пульманолог</p>
</td>
</tr>
<tr>
<td width="312">
<p>9</p>
</td>
<td width="312">
<p>Хирург</p>
</td>
</tr>
<tr>
<td width="312">
<p>10</p>
</td>
<td width="312">
<p>Окулист</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Специализации</p>
<table width="624">
<tbody>
<tr>
<td width="312">
<p>№ специализации</p>
</td>
<td width="312">
<p>Название</p>
</td>
</tr>
<tr>
<td width="312">
<p>1</p>
</td>
<td width="312">
<p>Пульманология</p>
</td>
</tr>
<tr>
<td width="312">
<p>2</p>
</td>
<td width="312">
<p>Травматология</p>
</td>
</tr>
<tr>
<td width="312">
<p>3</p>
</td>
<td width="312">
<p>Офтальмология</p>
</td>
</tr>
<tr>
<td width="312">
<p>4</p>
</td>
<td width="312">
<p>Хирургия</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Должности без специализации</p>
<table width="624">
<tbody>
<tr>
<td width="624">
<p>Номер должности</p>
</td>
</tr>
<tr>
<td width="624">
<p>1</p>
</td>
</tr>
<tr>
<td width="624">
<p>2</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Специализированные должности</p>
<table width="624">
<tbody>
<tr>
<td width="312">
<p>Номер должности</p>
</td>
<td width="312">
<p>Номер специализации</p>
</td>
</tr>
<tr>
<td width="312">
<p>3</p>
</td>
<td width="312">
<p>2</p>
</td>
</tr>
<tr>
<td width="312">
<p>4</p>
</td>
<td width="312">
<p>4</p>
</td>
</tr>
<tr>
<td width="312">
<p>5</p>
</td>
<td width="312">
<p>1</p>
</td>
</tr>
<tr>
<td width="312">
<p>6</p>
</td>
<td width="312">
<p>3</p>
</td>
</tr>
<tr>
<td width="312">
<p>7</p>
</td>
<td width="312">
<p>2</p>
</td>
</tr>
<tr>
<td width="312">
<p>8</p>
</td>
<td width="312">
<p>1</p>
</td>
</tr>
<tr>
<td width="312">
<p>9</p>
</td>
<td width="312">
<p>4</p>
</td>
</tr>
<tr>
<td width="312">
<p>10</p>
</td>
<td width="312">
<p>3</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Обслуживающий персонал</p>
<table width="624">
<tbody>
<tr>
<td width="104">
<p>№Кадра</p>
</td>
<td width="104">
<p>Фамилия</p>
</td>
<td width="104">
<p>Имя</p>
</td>
<td width="104">
<p>Отчество</p>
</td>
<td width="104">
<p>№Должности</p>
</td>
<td width="104">
<p>№Специализации</p>
</td>
</tr>
<tr>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>И</p>
</td>
<td width="104">
<p>А</p>
</td>
<td width="104">
<p>А</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>П</p>
</td>
<td width="104">
<p>Б</p>
</td>
<td width="104">
<p>Б</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>В</p>
</td>
<td width="104">
<p>В</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
<tr>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>Н</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>И</p>
</td>
<td width="104">
<p>М</p>
</td>
<td width="104">
<p>М</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>П</p>
</td>
<td width="104">
<p>Н</p>
</td>
<td width="104">
<p>Н</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>7</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>П</p>
</td>
<td width="104">
<p>П</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
<tr>
<td width="104">
<p>8</p>
</td>
<td width="104">
<p>Н</p>
</td>
<td width="104">
<p>Г</p>
</td>
<td width="104">
<p>Г</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>9</p>
</td>
<td width="104">
<p>Н</p>
</td>
<td width="104">
<p>Л</p>
</td>
<td width="104">
<p>Л</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>10</p>
</td>
<td width="104">
<p>Д</p>
</td>
<td width="104">
<p>М</p>
</td>
<td width="104">
<p>М</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>11</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>Т</p>
</td>
<td width="104">
<p>Т</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
<tr>
<td width="104">
<p>12</p>
</td>
<td width="104">
<p>Д</p>
</td>
<td width="104">
<p>З</p>
</td>
<td width="104">
<p>П</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Лечащий персонал</p>
<table width="624">
<tbody>
<tr>
<td width="104">
<p>№ Врача</p>
</td>
<td width="104">
<p>Фамилия</p>
</td>
<td width="104">
<p>Имя</p>
</td>
<td width="104">
<p>Очество</p>
</td>
<td width="104">
<p>№Должности</p>
</td>
<td width="104">
<p>№ Специализации</p>
</td>
</tr>
<tr>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>К</p>
</td>
<td width="104">
<p>Т</p>
</td>
<td width="104">
<p>Т</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>З</p>
</td>
<td width="104">
<p>В</p>
</td>
<td width="104">
<p>В</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>З</p>
</td>
<td width="104">
<p>М</p>
</td>
<td width="104">
<p>М</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>З</p>
</td>
<td width="104">
<p>Г</p>
</td>
<td width="104">
<p>Г</p>
</td>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
<tr>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>Д</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>7</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>Т</p>
</td>
<td width="104">
<p>П</p>
</td>
<td width="104">
<p>П</p>
</td>
<td width="104">
<p>8</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>7</p>
</td>
<td width="104">
<p>Т</p>
</td>
<td width="104">
<p>Р</p>
</td>
<td width="104">
<p>Р</p>
</td>
<td width="104">
<p>9</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>8</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>Ц</p>
</td>
<td width="104">
<p>Ц</p>
</td>
<td width="104">
<p>10</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
<tr>
<td width="104">
<p>9</p>
</td>
<td width="104">
<p>Г</p>
</td>
<td width="104">
<p>Ы</p>
</td>
<td width="104">
<p>Ы</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>10</p>
</td>
<td width="104">
<p>В</p>
</td>
<td width="104">
<p>Ш</p>
</td>
<td width="104">
<p>Ш</p>
</td>
<td width="104">
<p>7</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>11</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>Х</p>
</td>
<td width="104">
<p>Х</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>12</p>
</td>
<td width="104">
<p>В</p>
</td>
<td width="104">
<p>Ч</p>
</td>
<td width="104">
<p>Ч</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>13</p>
</td>
<td width="104">
<p>Г</p>
</td>
<td width="104">
<p>Я</p>
</td>
<td width="104">
<p>Я</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>14</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>А</p>
</td>
<td width="104">
<p>А</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>15</p>
</td>
<td width="104">
<p>П</p>
</td>
<td width="104">
<p>Д</p>
</td>
<td width="104">
<p>Д</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>16</p>
</td>
<td width="104">
<p>Н</p>
</td>
<td width="104">
<p>Ф</p>
</td>
<td width="104">
<p>Ф</p>
</td>
<td width="104">
<p>10</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Палаты</p>
<table width="624">
<tbody>
<tr>
<td width="208">
<p>№Палаты</p>
</td>
<td width="208">
<p>№Специализации</p>
</td>
<td width="208">
<p>Количество мест</p>
</td>
</tr>
<tr>
<td width="208">
<p>1</p>
</td>
<td width="208">
<p>1</p>
</td>
<td width="208">
<p>2</p>
</td>
</tr>
<tr>
<td width="208">
<p>2</p>
</td>
<td width="208">
<p>2</p>
</td>
<td width="208">
<p>3</p>
</td>
</tr>
<tr>
<td width="208">
<p>3</p>
</td>
<td width="208">
<p>3</p>
</td>
<td width="208">
<p>4</p>
</td>
</tr>
<tr>
<td width="208">
<p>4</p>
</td>
<td width="208">
<p>4</p>
</td>
<td width="208">
<p>2</p>
</td>
</tr>
<tr>
<td width="208">
<p>5</p>
</td>
<td width="208">
<p>1</p>
</td>
<td width="208">
<p>4</p>
</td>
</tr>
<tr>
<td width="208">
<p>6</p>
</td>
<td width="208">
<p>2</p>
</td>
<td width="208">
<p>2</p>
</td>
</tr>
<tr>
<td width="208">
<p>7</p>
</td>
<td width="208">
<p>3</p>
</td>
<td width="208">
<p>4</p>
</td>
</tr>
<tr>
<td width="208">
<p>8</p>
</td>
<td width="208">
<p>4</p>
</td>
<td width="208">
<p>3</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Диагнозы</p>
<table width="624">
<tbody>
<tr>
<td width="208">
<p>№ Диагноза</p>
</td>
<td width="208">
<p>Название</p>
</td>
<td width="208">
<p>№Специализации</p>
</td>
</tr>
<tr>
<td width="208">
<p>1</p>
</td>
<td width="208">
<p>Воспаление лёгких</p>
</td>
<td width="208">
<p>1</p>
</td>
</tr>
<tr>
<td width="208">
<p>2</p>
</td>
<td width="208">
<p>Помутнение кристалика</p>
</td>
<td width="208">
<p>3</p>
</td>
</tr>
<tr>
<td width="208">
<p>3</p>
</td>
<td width="208">
<p>Апендицит</p>
</td>
<td width="208">
<p>4</p>
</td>
</tr>
<tr>
<td width="208">
<p>4</p>
</td>
<td width="208">
<p>Перелом</p>
</td>
<td width="208">
<p>2</p>
</td>
</tr>
<tr>
<td width="208">
<p>5</p>
</td>
<td width="208">
<p>Ушиб</p>
</td>
<td width="208">
<p>2</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Пациенты</p>
<table width="624">
<tbody>
<tr>
<td width="156">
<p>№ Пациента</p>
</td>
<td width="156">
<p>Фамилия</p>
</td>
<td width="156">
<p>Имя</p>
</td>
<td width="156">
<p>Отчество</p>
</td>
</tr>
<tr>
<td width="156">
<p>1</p>
</td>
<td width="156">
<p>С</p>
</td>
<td width="156">
<p>А</p>
</td>
<td width="156">
<p>А</p>
</td>
</tr>
<tr>
<td width="156">
<p>2</p>
</td>
<td width="156">
<p>Н</p>
</td>
<td width="156">
<p>В</p>
</td>
<td width="156">
<p>В</p>
</td>
</tr>
<tr>
<td width="156">
<p>3</p>
</td>
<td width="156">
<p>З</p>
</td>
<td width="156">
<p>Ф</p>
</td>
<td width="156">
<p>Ф</p>
</td>
</tr>
<tr>
<td width="156">
<p>4</p>
</td>
<td width="156">
<p>С</p>
</td>
<td width="156">
<p>Т</p>
</td>
<td width="156">
<p>Т</p>
</td>
</tr>
<tr>
<td width="156">
<p>5</p>
</td>
<td width="156">
<p>П</p>
</td>
<td width="156">
<p>Г</p>
</td>
<td width="156">
<p>Г</p>
</td>
</tr>
<tr>
<td width="156">
<p>6</p>
</td>
<td width="156">
<p>Л</p>
</td>
<td width="156">
<p>Н</p>
</td>
<td width="156">
<p>Н</p>
</td>
</tr>
<tr>
<td width="156">
<p>7</p>
</td>
<td width="156">
<p>П</p>
</td>
<td width="156">
<p>Л</p>
</td>
<td width="156">
<p>Л</p>
</td>
</tr>
<tr>
<td width="156">
<p>8</p>
</td>
<td width="156">
<p>Б</p>
</td>
<td width="156">
<p>Ш</p>
</td>
<td width="156">
<p>Ш</p>
</td>
</tr>
<tr>
<td width="156">
<p>9</p>
</td>
<td width="156">
<p>Г</p>
</td>
<td width="156">
<p>Х</p>
</td>
<td width="156">
<p>Х</p>
</td>
</tr>
<tr>
<td width="156">
<p>10</p>
</td>
<td width="156">
<p>О</p>
</td>
<td width="156">
<p>Ц</p>
</td>
<td width="156">
<p>Ц</p>
</td>
</tr>
</tbody>
</table>
<p>Госпитализации</p>
<table width="624">
<tbody>
<tr>
<td width="104">
<p>№ Госпитализации</p>
</td>
<td width="104">
<p>№ Специализации</p>
</td>
<td width="104">
<p>№ Палаты</p>
</td>
<td width="104">
<p>№ Пациента</p>
</td>
<td width="104">
<p>№ Врача</p>
</td>
<td width="104">
<p>№ Диагноза</p>
</td>
</tr>
<tr>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>7</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>8</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>11</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
<tr>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>5</p>
</td>
</tr>
<tr>
<td width="104">
<p>7</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>7</p>
</td>
<td width="104">
<p>7</p>
</td>
<td width="104">
<p>8</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>8</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>8</p>
</td>
<td width="104">
<p>8</p>
</td>
<td width="104">
<p>9</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
<tr>
<td width="104">
<p>9</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>9</p>
</td>
<td width="104">
<p>12</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>10</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>10</p>
</td>
<td width="104">
<p>10</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>11</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>16</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>12</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
<tr>
<td width="104">
<p>13</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>12</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>14</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>15</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
<tr>
<td width="104">
<p>15</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>16</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>16</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>15</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>Диапазоны</p>
<table width="624">
<tbody>
<tr>
<td width="208">
<p>№ Госпитализации</p>
</td>
<td width="208">
<p>Дата</p>
</td>
<td width="208">
<p>№ Даты</p>
</td>
</tr>
<tr>
<td width="208">
<p>12</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>1</p>
</td>
</tr>
<tr>
<td width="208">
<p>12</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>2</p>
</td>
</tr>
<tr>
<td width="208">
<p>13</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>3</p>
</td>
</tr>
<tr>
<td width="208">
<p>13</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>4</p>
</td>
</tr>
<tr>
<td width="208">
<p>13</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>5</p>
</td>
</tr>
<tr>
<td width="208">
<p>14</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>6</p>
</td>
</tr>
<tr>
<td width="208">
<p>14</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>7</p>
</td>
</tr>
<tr>
<td width="208">
<p>14</p>
</td>
<td width="208">
<p>4.03.2007</p>
</td>
<td width="208">
<p>8</p>
</td>
</tr>
<tr>
<td width="208">
<p>15</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>9</p>
</td>
</tr>
<tr>
<td width="208">
<p>15</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>10</p>
</td>
</tr>
<tr>
<td width="208">
<p>16</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>11</p>
</td>
</tr>
<tr>
<td width="208">
<p>16</p>
</td>
<td width="208">
<p>4.03.2007</p>
</td>
<td width="208">
<p>12</p>
</td>
</tr>
<tr>
<td width="208">
<p>11</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>13</p>
</td>
</tr>
<tr>
<td width="208">
<p>11</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>14</p>
</td>
</tr>
<tr>
<td width="208">
<p>11</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>15</p>
</td>
</tr>
<tr>
<td width="208">
<p>10</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>16</p>
</td>
</tr>
<tr>
<td width="208">
<p>10</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>17</p>
</td>
</tr>
<tr>
<td width="208">
<p>10</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>18</p>
</td>
</tr>
<tr>
<td width="208">
<p>9</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>19</p>
</td>
</tr>
<tr>
<td width="208">
<p>9</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>20</p>
</td>
</tr>
<tr>
<td width="208">
<p>1</p>
</td>
<td width="208">
<p>1.03.2006</p>
</td>
<td width="208">
<p>21</p>
</td>
</tr>
<tr>
<td width="208">
<p>1</p>
</td>
<td width="208">
<p>2.03.2006</p>
</td>
<td width="208">
<p>22</p>
</td>
</tr>
<tr>
<td width="208">
<p>1</p>
</td>
<td width="208">
<p>3.03.2006</p>
</td>
<td width="208">
<p>23</p>
</td>
</tr>
<tr>
<td width="208">
<p>2</p>
</td>
<td width="208">
<p>3.03.2006</p>
</td>
<td width="208">
<p>24</p>
</td>
</tr>
<tr>
<td width="208">
<p>2</p>
</td>
<td width="208">
<p>4.03.2006</p>
</td>
<td width="208">
<p>25</p>
</td>
</tr>
<tr>
<td width="208">
<p>2</p>
</td>
<td width="208">
<p>5.03.2006</p>
</td>
<td width="208">
<p>26</p>
</td>
</tr>
<tr>
<td width="208">
<p>3</p>
</td>
<td width="208">
<p>2.03.2006</p>
</td>
<td width="208">
<p>27</p>
</td>
</tr>
<tr>
<td width="208">
<p>3</p>
</td>
<td width="208">
<p>3.03.2006</p>
</td>
<td width="208">
<p>28</p>
</td>
</tr>
<tr>
<td width="208">
<p>3</p>
</td>
<td width="208">
<p>4.03.2006</p>
</td>
<td width="208">
<p>29</p>
</td>
</tr>
<tr>
<td width="208">
<p>4</p>
</td>
<td width="208">
<p>2.03.2006</p>
</td>
<td width="208">
<p>30</p>
</td>
</tr>
<tr>
<td width="208">
<p>4</p>
</td>
<td width="208">
<p>3.03.2006</p>
</td>
<td width="208">
<p>31</p>
</td>
</tr>
<tr>
<td width="208">
<p>4</p>
</td>
<td width="208">
<p>4.03.2006</p>
</td>
<td width="208">
<p>32</p>
</td>
</tr>
<tr>
<td width="208">
<p>5</p>
</td>
<td width="208">
<p>1.03.2006</p>
</td>
<td width="208">
<p>33</p>
</td>
</tr>
<tr>
<td width="208">
<p>5</p>
</td>
<td width="208">
<p>2.03.2006</p>
</td>
<td width="208">
<p>34</p>
</td>
</tr>
<tr>
<td width="208">
<p>5</p>
</td>
<td width="208">
<p>3.03.2006</p>
</td>
<td width="208">
<p>35</p>
</td>
</tr>
<tr>
<td width="208">
<p>6</p>
</td>
<td width="208">
<p>1.03.2006</p>
</td>
<td width="208">
<p>36</p>
</td>
</tr>
<tr>
<td width="208">
<p>6</p>
</td>
<td width="208">
<p>2.03.2006</p>
</td>
<td width="208">
<p>37</p>
</td>
</tr>
<tr>
<td width="208">
<p>7</p>
</td>
<td width="208">
<p>3.03.2006</p>
</td>
<td width="208">
<p>38</p>
</td>
</tr>
<tr>
<td width="208">
<p>7</p>
</td>
<td width="208">
<p>4.03.2006</p>
</td>
<td width="208">
<p>39</p>
</td>
</tr>
<tr>
<td width="208">
<p>8</p>
</td>
<td width="208">
<p>3.03.2006</p>
</td>
<td width="208">
<p>40</p>
</td>
</tr>
<tr>
<td width="208">
<p>8</p>
</td>
<td width="208">
<p>4.03.2006</p>
</td>
<td width="208">
<p>41</p>
</td>
</tr>
<tr>
<td width="208">
<p>8</p>
</td>
<td width="208">
<p>5.03.2006</p>
</td>
<td width="208">
<p>42</p>
</td>
</tr>
</tbody>
</table>
<p>Операции</p>
<table width="624">
<tbody>
<tr>
<td width="156">
<p>№ Операции</p>
</td>
<td width="248">
<p>№ Госпитализации</p>
</td>
<td width="142">
<p>№ Даты</p>
</td>
</tr>
<tr>
<td width="156">
<p>1</p>
</td>
<td width="248">
<p>4</p>
</td>
<td width="142">
<p>30</p>
</td>
</tr>
<tr>
<td width="156">
<p>2</p>
</td>
<td width="248">
<p>12</p>
</td>
<td width="142">
<p>1</p>
</td>
</tr>
<tr>
<td width="156">
<p>3</p>
</td>
<td width="248">
<p>14</p>
</td>
<td width="142">
<p>6</p>
</td>
</tr>
<tr>
<td width="156">
<p>4</p>
</td>
<td width="248">
<p>16</p>
</td>
<td width="142">
<p>11</p>
</td>
</tr>
<tr>
<td width="156">
<p>5</p>
</td>
<td width="248">
<p>8</p>
</td>
<td width="142">
<p>40</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<h2>4.Решение задач</h2>
<h3>4.1. Найти все переполненные палаты.</h3>
<p>Исходные данные &ndash; см. п. 3. Пусть сегодня &ndash; 1.03.2007.</p>
<p>1.Находим все текущие госпитализации:</p>
<p>R1 := &rdquo;Диапазоны&rdquo; WHERE СЕГОДНЯ() &lt; = &ldquo;Дата&rdquo;</p>
<p>R1</p>
<table width="624">
<tbody>
<tr>
<td width="208">
<p>№ Госпитализации</p>
</td>
<td width="208">
<p>Дата</p>
</td>
<td width="208">
<p>№ Даты</p>
</td>
</tr>
<tr>
<td width="208">
<p>12</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>1</p>
</td>
</tr>
<tr>
<td width="208">
<p>12</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>2</p>
</td>
</tr>
<tr>
<td width="208">
<p>13</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>3</p>
</td>
</tr>
<tr>
<td width="208">
<p>13</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>4</p>
</td>
</tr>
<tr>
<td width="208">
<p>13</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>5</p>
</td>
</tr>
<tr>
<td width="208">
<p>14</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>6</p>
</td>
</tr>
<tr>
<td width="208">
<p>14</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>7</p>
</td>
</tr>
<tr>
<td width="208">
<p>14</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>8</p>
</td>
</tr>
<tr>
<td width="208">
<p>15</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>9</p>
</td>
</tr>
<tr>
<td width="208">
<p>15</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>10</p>
</td>
</tr>
<tr>
<td width="208">
<p>16</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>11</p>
</td>
</tr>
<tr>
<td width="208">
<p>16</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>12</p>
</td>
</tr>
<tr>
<td width="208">
<p>11</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>13</p>
</td>
</tr>
<tr>
<td width="208">
<p>11</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>14</p>
</td>
</tr>
<tr>
<td width="208">
<p>11</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>15</p>
</td>
</tr>
<tr>
<td width="208">
<p>10</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>16</p>
</td>
</tr>
<tr>
<td width="208">
<p>10</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>17</p>
</td>
</tr>
<tr>
<td width="208">
<p>10</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>18</p>
</td>
</tr>
<tr>
<td width="208">
<p>9</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>19</p>
</td>
</tr>
<tr>
<td width="208">
<p>9</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>20</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R2 := R1[&ldquo;№ Госпитализации&rdquo;]</p>
<p>R2</p>
<table width="624">
<tbody>
<tr>
<td width="624">
<p>№ Госпитализации</p>
</td>
</tr>
<tr>
<td width="624">
<p>12</p>
</td>
</tr>
<tr>
<td width="624">
<p>13</p>
</td>
</tr>
<tr>
<td width="624">
<p>14</p>
</td>
</tr>
<tr>
<td width="624">
<p>15</p>
</td>
</tr>
<tr>
<td width="624">
<p>16</p>
</td>
</tr>
<tr>
<td width="624">
<p>11</p>
</td>
</tr>
<tr>
<td width="624">
<p>10</p>
</td>
</tr>
<tr>
<td width="624">
<p>9</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R3 := R2 JOIN &ldquo;Госпитализации&rdquo;</p>
<p>R3</p>
<table width="622">
<tbody>
<tr>
<td width="102">
<p>№ Госпитализации</p>
</td>
<td width="104">
<p>№ Специализации</p>
</td>
<td width="104">
<p>№ Палаты</p>
</td>
<td width="104">
<p>№ Пациента</p>
</td>
<td width="103">
<p>№ Врача</p>
</td>
<td width="105">
<p>№ Диагноза</p>
</td>
</tr>
<tr>
<td width="102">
<p>9</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>9</p>
</td>
<td width="103">
<p>12</p>
</td>
<td width="105">
<p>1</p>
</td>
</tr>
<tr>
<td width="102">
<p>10</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>10</p>
</td>
<td width="103">
<p>10</p>
</td>
<td width="105">
<p>4</p>
</td>
</tr>
<tr>
<td width="102">
<p>11</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="103">
<p>16</p>
</td>
<td width="105">
<p>2</p>
</td>
</tr>
<tr>
<td width="102">
<p>12</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="103">
<p>2</p>
</td>
<td width="105">
<p>3</p>
</td>
</tr>
<tr>
<td width="102">
<p>13</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="103">
<p>12</p>
</td>
<td width="105">
<p>1</p>
</td>
</tr>
<tr>
<td width="102">
<p>14</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="103">
<p>15</p>
</td>
<td width="105">
<p>3</p>
</td>
</tr>
<tr>
<td width="102">
<p>15</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="103">
<p>16</p>
</td>
<td width="105">
<p>2</p>
</td>
</tr>
<tr>
<td width="102">
<p>16</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>6</p>
</td>
<td width="103">
<p>15</p>
</td>
<td width="105">
<p>3</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>2.Находим количество пациентов в каждой палате:</p>
<p>R4 := SUMARIZE R3 BY (&ldquo;№ Палаты&rdquo;) ADD COUNT() AS &ldquo;Всего_пациентов&rdquo;</p>
<p>&nbsp;</p>
<p>R4</p>
<table width="624">
<tbody>
<tr>
<td width="312">
<p>№ Палаты</p>
</td>
<td width="312">
<p>Всего_пациентов</p>
</td>
</tr>
<tr>
<td width="312">
<p>5</p>
</td>
<td width="312">
<p>2</p>
</td>
</tr>
<tr>
<td width="312">
<p>6</p>
</td>
<td width="312">
<p>1</p>
</td>
</tr>
<tr>
<td width="312">
<p>3</p>
</td>
<td width="312">
<p>2</p>
</td>
</tr>
<tr>
<td width="312">
<p>4</p>
</td>
<td width="312">
<p>3</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>R5 := R4 JOIN &ldquo;Палаты&rdquo;</p>
<p>R5</p>
<table width="624">
<tbody>
<tr>
<td width="156">
<p>№ Палаты</p>
</td>
<td width="156">
<p>Всего_пациентов</p>
</td>
<td width="156">
<p>Количество мест</p>
</td>
<td width="156">
<p>№ Специализации</p>
</td>
</tr>
<tr>
<td width="156">
<p>3</p>
</td>
<td width="156">
<p>2</p>
</td>
<td width="156">
<p>4</p>
</td>
<td width="156">
<p>3</p>
</td>
</tr>
<tr>
<td width="156">
<p>4</p>
</td>
<td width="156">
<p>3</p>
</td>
<td width="156">
<p>2</p>
</td>
<td width="156">
<p>4</p>
</td>
</tr>
<tr>
<td width="156">
<p>5</p>
</td>
<td width="156">
<p>2</p>
</td>
<td width="156">
<p>4</p>
</td>
<td width="156">
<p>1</p>
</td>
</tr>
<tr>
<td width="156">
<p>6</p>
</td>
<td width="156">
<p>1</p>
</td>
<td width="156">
<p>2</p>
</td>
<td width="156">
<p>2</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>3.Сравниваем количество мест с пациентами</p>
<p>R6 := R5 WHERE &ldquo;Всего_пациентов&rdquo; &gt; &ldquo;Количество мест&rdquo;</p>
<p>R6</p>
<table width="624">
<tbody>
<tr>
<td width="156">
<p>№ Палаты</p>
</td>
<td width="156">
<p>Всего_пациентов</p>
</td>
<td width="156">
<p>Количество мест</p>
</td>
<td width="156">
<p>№ Специализации</p>
</td>
</tr>
<tr>
<td width="156">
<p>4</p>
</td>
<td width="156">
<p>3</p>
</td>
<td width="156">
<p>2</p>
</td>
<td width="156">
<p>4</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R7 := R6[&ldquo;Номер палаты&rdquo;]</p>
<p>R7</p>
<table width="624">
<tbody>
<tr>
<td width="624">
<p>№ Палаты</p>
</td>
</tr>
<tr>
<td width="624">
<p>4</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<h3>4.2 Найти лечащего врача у которого нет пациентов</h3>
<p>1.Находим все текущие госпитализации</p>
<p>R1 := &rdquo;Диапазоны&rdquo; WHERE СЕГОДНЯ() &lt; = &ldquo;Дата&rdquo;</p>
<p>R1</p>
<table width="624">
<tbody>
<tr>
<td width="208">
<p>№ Госпитализации</p>
</td>
<td width="208">
<p>Дата</p>
</td>
<td width="208">
<p>№ Даты</p>
</td>
</tr>
<tr>
<td width="208">
<p>12</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>1</p>
</td>
</tr>
<tr>
<td width="208">
<p>12</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>2</p>
</td>
</tr>
<tr>
<td width="208">
<p>13</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>3</p>
</td>
</tr>
<tr>
<td width="208">
<p>13</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>4</p>
</td>
</tr>
<tr>
<td width="208">
<p>13</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>5</p>
</td>
</tr>
<tr>
<td width="208">
<p>14</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>6</p>
</td>
</tr>
<tr>
<td width="208">
<p>14</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>7</p>
</td>
</tr>
<tr>
<td width="208">
<p>14</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>8</p>
</td>
</tr>
<tr>
<td width="208">
<p>15</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>9</p>
</td>
</tr>
<tr>
<td width="208">
<p>15</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>10</p>
</td>
</tr>
<tr>
<td width="208">
<p>16</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>11</p>
</td>
</tr>
<tr>
<td width="208">
<p>16</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>12</p>
</td>
</tr>
<tr>
<td width="208">
<p>11</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>13</p>
</td>
</tr>
<tr>
<td width="208">
<p>11</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>14</p>
</td>
</tr>
<tr>
<td width="208">
<p>11</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>15</p>
</td>
</tr>
<tr>
<td width="208">
<p>10</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>16</p>
</td>
</tr>
<tr>
<td width="208">
<p>10</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>17</p>
</td>
</tr>
<tr>
<td width="208">
<p>10</p>
</td>
<td width="208">
<p>3.03.2007</p>
</td>
<td width="208">
<p>18</p>
</td>
</tr>
<tr>
<td width="208">
<p>9</p>
</td>
<td width="208">
<p>1.03.2007</p>
</td>
<td width="208">
<p>19</p>
</td>
</tr>
<tr>
<td width="208">
<p>9</p>
</td>
<td width="208">
<p>2.03.2007</p>
</td>
<td width="208">
<p>20</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R2 := R1[&ldquo;№ Госпитализации&rdquo;]</p>
<p>R2</p>
<table width="624">
<tbody>
<tr>
<td width="624">
<p>№ Госпитализации</p>
</td>
</tr>
<tr>
<td width="624">
<p>12</p>
</td>
</tr>
<tr>
<td width="624">
<p>13</p>
</td>
</tr>
<tr>
<td width="624">
<p>14</p>
</td>
</tr>
<tr>
<td width="624">
<p>15</p>
</td>
</tr>
<tr>
<td width="624">
<p>16</p>
</td>
</tr>
<tr>
<td width="624">
<p>11</p>
</td>
</tr>
<tr>
<td width="624">
<p>10</p>
</td>
</tr>
<tr>
<td width="624">
<p>9</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R3 := R2 JOIN &ldquo;Госпитализации&rdquo;</p>
<p>R3</p>
<table width="622">
<tbody>
<tr>
<td width="102">
<p>№ Госпитализации</p>
</td>
<td width="104">
<p>№ Специализации</p>
</td>
<td width="104">
<p>№ Палаты</p>
</td>
<td width="104">
<p>№ Пациента</p>
</td>
<td width="103">
<p>№ Врача</p>
</td>
<td width="105">
<p>№ Диагноза</p>
</td>
</tr>
<tr>
<td width="102">
<p>9</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>9</p>
</td>
<td width="103">
<p>12</p>
</td>
<td width="105">
<p>1</p>
</td>
</tr>
<tr>
<td width="102">
<p>10</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>10</p>
</td>
<td width="103">
<p>10</p>
</td>
<td width="105">
<p>4</p>
</td>
</tr>
<tr>
<td width="102">
<p>11</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="103">
<p>16</p>
</td>
<td width="105">
<p>2</p>
</td>
</tr>
<tr>
<td width="102">
<p>12</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>2</p>
</td>
<td width="103">
<p>2</p>
</td>
<td width="105">
<p>3</p>
</td>
</tr>
<tr>
<td width="102">
<p>13</p>
</td>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="103">
<p>12</p>
</td>
<td width="105">
<p>1</p>
</td>
</tr>
<tr>
<td width="102">
<p>14</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="103">
<p>15</p>
</td>
<td width="105">
<p>3</p>
</td>
</tr>
<tr>
<td width="102">
<p>15</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="103">
<p>16</p>
</td>
<td width="105">
<p>2</p>
</td>
</tr>
<tr>
<td width="102">
<p>16</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>6</p>
</td>
<td width="103">
<p>15</p>
</td>
<td width="105">
<p>3</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>2.Берем всехврачей, которые лечат пациентов по текущим госпитализациям</p>
<p>R4 := R3[&ldquo;Номер врача&rdquo;]</p>
<p>R4</p>
<table width="622">
<tbody>
<tr>
<td width="622">
<p>№ Врача</p>
</td>
</tr>
<tr>
<td width="622">
<p>10</p>
</td>
</tr>
<tr>
<td width="622">
<p>2</p>
</td>
</tr>
<tr>
<td width="622">
<p>12</p>
</td>
</tr>
<tr>
<td width="622">
<p>15</p>
</td>
</tr>
<tr>
<td width="622">
<p>16</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>3.Берем всех врачей в этой больнице</p>
<p>R5 := &ldquo;Лечащий персонал&rdquo;[&ldquo;Номер врача&rdquo;]</p>
<p>R5</p>
<table width="624">
<tbody>
<tr>
<td width="624">
<p>№ Врача</p>
</td>
</tr>
<tr>
<td width="624">
<p>1</p>
</td>
</tr>
<tr>
<td width="624">
<p>2</p>
</td>
</tr>
<tr>
<td width="624">
<p>3</p>
</td>
</tr>
<tr>
<td width="624">
<p>4</p>
</td>
</tr>
<tr>
<td width="624">
<p>5</p>
</td>
</tr>
<tr>
<td width="624">
<p>6</p>
</td>
</tr>
<tr>
<td width="624">
<p>7</p>
</td>
</tr>
<tr>
<td width="624">
<p>8</p>
</td>
</tr>
<tr>
<td width="624">
<p>9</p>
</td>
</tr>
<tr>
<td width="624">
<p>10</p>
</td>
</tr>
<tr>
<td width="624">
<p>11</p>
</td>
</tr>
<tr>
<td width="624">
<p>12</p>
</td>
</tr>
<tr>
<td width="624">
<p>13</p>
</td>
</tr>
<tr>
<td width="624">
<p>14</p>
</td>
</tr>
<tr>
<td width="624">
<p>15</p>
</td>
</tr>
<tr>
<td width="624">
<p>16</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<ol start="4">
<li>Вычитаем из множества всех врачей множество занятых</li>
</ol>
<p>R6 := R5 MINUS R4</p>
<p>&nbsp;</p>
<table width="624">
<tbody>
<tr>
<td width="624">
<p>№ Врача</p>
</td>
</tr>
<tr>
<td width="624">
<p>1</p>
</td>
</tr>
<tr>
<td width="624">
<p>3</p>
</td>
</tr>
<tr>
<td width="624">
<p>4</p>
</td>
</tr>
<tr>
<td width="624">
<p>5</p>
</td>
</tr>
<tr>
<td width="624">
<p>6</p>
</td>
</tr>
<tr>
<td width="624">
<p>7</p>
</td>
</tr>
<tr>
<td width="624">
<p>8</p>
</td>
</tr>
<tr>
<td width="624">
<p>9</p>
</td>
</tr>
<tr>
<td width="624">
<p>11</p>
</td>
</tr>
<tr>
<td width="624">
<p>13</p>
</td>
</tr>
<tr>
<td width="624">
<p>14</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<ol start="5">
<li>Находим их Ф.И.О</li>
</ol>
<p>R7 := R6 JOIN &ldquo;Лечащий персонал&rdquo;</p>
<p>R7</p>
<table width="624">
<tbody>
<tr>
<td width="104">
<p>№ Врача</p>
</td>
<td width="104">
<p>Фамилия</p>
</td>
<td width="104">
<p>Имя</p>
</td>
<td width="104">
<p>Очество</p>
</td>
<td width="104">
<p>№Должности</p>
</td>
<td width="104">
<p>№ Специализации</p>
</td>
</tr>
<tr>
<td width="104">
<p>1</p>
</td>
<td width="104">
<p>К</p>
</td>
<td width="104">
<p>Т</p>
</td>
<td width="104">
<p>Т</p>
</td>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>3</p>
</td>
<td width="104">
<p>З</p>
</td>
<td width="104">
<p>М</p>
</td>
<td width="104">
<p>М</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>З</p>
</td>
<td width="104">
<p>Г</p>
</td>
<td width="104">
<p>Г</p>
</td>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
<tr>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>Д</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>7</p>
</td>
<td width="104">
<p>2</p>
</td>
</tr>
<tr>
<td width="104">
<p>6</p>
</td>
<td width="104">
<p>Т</p>
</td>
<td width="104">
<p>П</p>
</td>
<td width="104">
<p>П</p>
</td>
<td width="104">
<p>8</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
<tr>
<td width="104">
<p>7</p>
</td>
<td width="104">
<p>Т</p>
</td>
<td width="104">
<p>Р</p>
</td>
<td width="104">
<p>Р</p>
</td>
<td width="104">
<p>9</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>8</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>Ц</p>
</td>
<td width="104">
<p>Ц</p>
</td>
<td width="104">
<p>10</p>
</td>
<td width="104">
<p>3</p>
</td>
</tr>
<tr>
<td width="104">
<p>9</p>
</td>
<td width="104">
<p>Г</p>
</td>
<td width="104">
<p>Ы</p>
</td>
<td width="104">
<p>Ы</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>11</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>Х</p>
</td>
<td width="104">
<p>Х</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>13</p>
</td>
<td width="104">
<p>Г</p>
</td>
<td width="104">
<p>Я</p>
</td>
<td width="104">
<p>Я</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>14</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>А</p>
</td>
<td width="104">
<p>А</p>
</td>
<td width="104">
<p>5</p>
</td>
<td width="104">
<p>1</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R8 := R7[&ldquo;Фамилия&rdquo;,&rdquo;Имя&rdquo;,&rdquo;Отчество&rdquo;]</p>
<p>R8</p>
<table width="624">
<tbody>
<tr>
<td width="208">
<p>Фамилия</p>
</td>
<td width="208">
<p>Имя</p>
</td>
<td width="208">
<p>Очество</p>
</td>
</tr>
<tr>
<td width="208">
<p>К</p>
</td>
<td width="208">
<p>Т</p>
</td>
<td width="208">
<p>Т</p>
</td>
</tr>
<tr>
<td width="208">
<p>З</p>
</td>
<td width="208">
<p>М</p>
</td>
<td width="208">
<p>М</p>
</td>
</tr>
<tr>
<td width="208">
<p>З</p>
</td>
<td width="208">
<p>Г</p>
</td>
<td width="208">
<p>Г</p>
</td>
</tr>
<tr>
<td width="208">
<p>Д</p>
</td>
<td width="208">
<p>С</p>
</td>
<td width="208">
<p>С</p>
</td>
</tr>
<tr>
<td width="208">
<p>Т</p>
</td>
<td width="208">
<p>П</p>
</td>
<td width="208">
<p>П</p>
</td>
</tr>
<tr>
<td width="208">
<p>Т</p>
</td>
<td width="208">
<p>Р</p>
</td>
<td width="208">
<p>Р</p>
</td>
</tr>
<tr>
<td width="208">
<p>С</p>
</td>
<td width="208">
<p>Ц</p>
</td>
<td width="208">
<p>Ц</p>
</td>
</tr>
<tr>
<td width="208">
<p>Г</p>
</td>
<td width="208">
<p>Ы</p>
</td>
<td width="208">
<p>Ы</p>
</td>
</tr>
<tr>
<td width="208">
<p>С</p>
</td>
<td width="208">
<p>Х</p>
</td>
<td width="208">
<p>Х</p>
</td>
</tr>
<tr>
<td width="208">
<p>Г</p>
</td>
<td width="208">
<p>Я</p>
</td>
<td width="208">
<p>Я</p>
</td>
</tr>
<tr>
<td width="208">
<p>С</p>
</td>
<td width="208">
<p>А</p>
</td>
<td width="208">
<p>А</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<h3>4.3 Какой хирург проводит больше всего операций</h3>
<p>1.Берем номера всех госпитализаций в которых были операции (за всё время).</p>
<p>R1 := &ldquo;Операции&rdquo;[&ldquo;№ Госпитализации&rdquo;]</p>
<p>R1</p>
<table width="624">
<tbody>
<tr>
<td width="624">
<p>№ Госпитализации</p>
</td>
</tr>
<tr>
<td width="624">
<p>4</p>
</td>
</tr>
<tr>
<td width="624">
<p>8</p>
</td>
</tr>
<tr>
<td width="624">
<p>12</p>
</td>
</tr>
<tr>
<td width="624">
<p>14</p>
</td>
</tr>
<tr>
<td width="624">
<p>16</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>2.Находим врачей, котрые проводили операции</p>
<p>R2 := &ldquo;Госпитализации&rdquo;[&ldquo;№ Госпитализации&rdquo;,&rdquo;№ Врача&rdquo;]</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>R2</p>
<table width="624">
<tbody>
<tr>
<td width="312">
<p>№ Госпитализации</p>
</td>
<td width="312">
<p>№ Врача</p>
</td>
</tr>
<tr>
<td width="312">
<p>1</p>
</td>
<td width="312">
<p>3</p>
</td>
</tr>
<tr>
<td width="312">
<p>2</p>
</td>
<td width="312">
<p>1</p>
</td>
</tr>
<tr>
<td width="312">
<p>3</p>
</td>
<td width="312">
<p>4</p>
</td>
</tr>
<tr>
<td width="312">
<p>4</p>
</td>
<td width="312">
<p>11</p>
</td>
</tr>
<tr>
<td width="312">
<p>5</p>
</td>
<td width="312">
<p>6</p>
</td>
</tr>
<tr>
<td width="312">
<p>6</p>
</td>
<td width="312">
<p>5</p>
</td>
</tr>
<tr>
<td width="312">
<p>7</p>
</td>
<td width="312">
<p>8</p>
</td>
</tr>
<tr>
<td width="312">
<p>8</p>
</td>
<td width="312">
<p>9</p>
</td>
</tr>
<tr>
<td width="312">
<p>9</p>
</td>
<td width="312">
<p>12</p>
</td>
</tr>
<tr>
<td width="312">
<p>10</p>
</td>
<td width="312">
<p>10</p>
</td>
</tr>
<tr>
<td width="312">
<p>11</p>
</td>
<td width="312">
<p>16</p>
</td>
</tr>
<tr>
<td width="312">
<p>12</p>
</td>
<td width="312">
<p>2</p>
</td>
</tr>
<tr>
<td width="312">
<p>13</p>
</td>
<td width="312">
<p>12</p>
</td>
</tr>
<tr>
<td width="312">
<p>14</p>
</td>
<td width="312">
<p>15</p>
</td>
</tr>
<tr>
<td width="312">
<p>15</p>
</td>
<td width="312">
<p>16</p>
</td>
</tr>
<tr>
<td width="312">
<p>16</p>
</td>
<td width="312">
<p>15</p>
</td>
</tr>
</tbody>
</table>
<p>R3 := R1 JOIN R2</p>
<p>R3</p>
<table width="624">
<tbody>
<tr>
<td width="312">
<p>№ Госпитализации</p>
</td>
<td width="312">
<p>№ Врача</p>
</td>
</tr>
<tr>
<td width="312">
<p>4</p>
</td>
<td width="312">
<p>11</p>
</td>
</tr>
<tr>
<td width="312">
<p>8</p>
</td>
<td width="312">
<p>9</p>
</td>
</tr>
<tr>
<td width="312">
<p>12</p>
</td>
<td width="312">
<p>2</p>
</td>
</tr>
<tr>
<td width="312">
<p>14</p>
</td>
<td width="312">
<p>15</p>
</td>
</tr>
<tr>
<td width="312">
<p>16</p>
</td>
<td width="312">
<p>15</p>
</td>
</tr>
</tbody>
</table>
<p>3.Посчитаем операции у каждого врача и найдем максимальное</p>
<p>R4 := SUMMARIZE R3 BY (№ Врача) ADD COUNT() AS &ldquo;Всего_операций&rdquo;</p>
<p>R4</p>
<table width="626">
<tbody>
<tr>
<td width="314">
<p>№ Врача</p>
</td>
<td width="312">
<p>Всего_операций</p>
</td>
</tr>
<tr>
<td width="314">
<p>11</p>
</td>
<td width="312">
<p>1</p>
</td>
</tr>
<tr>
<td width="314">
<p>9</p>
</td>
<td width="312">
<p>1</p>
</td>
</tr>
<tr>
<td width="314">
<p>2</p>
</td>
<td width="312">
<p>1</p>
</td>
</tr>
<tr>
<td width="314">
<p>15</p>
</td>
<td width="312">
<p>2</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
<p>R5 := SUMMARIZE R4 BY() ADD MAX (Всего_операций) AS &ldquo;Максимум&rdquo;</p>
<p>R5</p>
<p>&nbsp;</p>
<table width="624">
<tbody>
<tr>
<td width="312">
<p>№ Врача</p>
</td>
<td width="312">
<p>Максимум</p>
</td>
</tr>
<tr>
<td width="312">
<p>15</p>
</td>
<td width="312">
<p>2</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<ol start="4">
<li>Находим его Ф.И.О</li>
</ol>
<p>R6 := R5 JOIN &ldquo;Лечащий персонал&rdquo;</p>
<p>R6</p>
<table width="624">
<tbody>
<tr>
<td width="89">
<p>Максимум</p>
</td>
<td width="89">
<p>№ Врача</p>
</td>
<td width="89">
<p>Фамилия</p>
</td>
<td width="89">
<p>Имя</p>
</td>
<td width="89">
<p>Очество</p>
</td>
<td width="89">
<p>№Должности</p>
</td>
<td width="89">
<p>№ Специализации</p>
</td>
</tr>
<tr>
<td width="89">
<p>2</p>
</td>
<td width="89">
<p>15</p>
</td>
<td width="89">
<p>П</p>
</td>
<td width="89">
<p>Д</p>
</td>
<td width="89">
<p>Д</p>
</td>
<td width="89">
<p>4</p>
</td>
<td width="89">
<p>4</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R7 := R8[Ф.И.О]</p>
<p>R7</p>
<table width="624">
<tbody>
<tr>
<td width="208">
<p>Фамилия</p>
</td>
<td width="208">
<p>Имя</p>
</td>
<td width="208">
<p>Очество</p>
</td>
</tr>
<tr>
<td width="208">
<p>П</p>
</td>
<td width="208">
<p>Д</p>
</td>
<td width="208">
<p>Д</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<h3>4.4 Найти всех лечащих врачей указанного пациента, который был прооперирован не менее двух раз</h3>
<p>1.Найдём все госпитализации указанного пациента</p>
<p>R1 :=</p>
<table width="624">
<tbody>
<tr>
<td width="208">
<p>Фамилия</p>
</td>
<td width="208">
<p>Имя</p>
</td>
<td width="208">
<p>Отчество</p>
</td>
</tr>
<tr>
<td width="208">
<p>С</p>
</td>
<td width="208">
<p>Т</p>
</td>
<td width="208">
<p>Т</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R2 := R1 JOIN &ldquo;Пациенты&rdquo;</p>
<p>R2</p>
<table width="624">
<tbody>
<tr>
<td width="156">
<p>Фамилия</p>
</td>
<td width="156">
<p>Имя</p>
</td>
<td width="156">
<p>Отчество</p>
</td>
<td width="156">
<p>№ Пациента</p>
</td>
</tr>
<tr>
<td width="156">
<p>Слепов</p>
</td>
<td width="156">
<p>Т</p>
</td>
<td width="156">
<p>Т</p>
</td>
<td width="156">
<p>4</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R3 := R2 JOIN &ldquo;Госпитализации&rdquo;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>R3</p>
<p>&nbsp;</p>
<table width="624">
<tbody>
<tr>
<td width="76">
<p>Фамилия</p>
</td>
<td width="49">
<p>Имя</p>
</td>
<td width="62">
<p>Отчество</p>
</td>
<td width="62">
<p>№ Пациента</p>
</td>
<td width="62">
<p>№ Госпитализации</p>
</td>
<td width="92">
<p>№ Специализации</p>
</td>
<td width="64">
<p>№ Палаты</p>
</td>
<td width="80">
<p>№ Врача</p>
</td>
<td width="76">
<p>№ Диагноза</p>
</td>
</tr>
<tr>
<td width="76">
<p>Слепов</p>
</td>
<td width="49">
<p>Т</p>
</td>
<td width="62">
<p>Т</p>
</td>
<td width="62">
<p>4</p>
</td>
<td width="62">
<p>4</p>
</td>
<td width="92">
<p>4</p>
</td>
<td width="64">
<p>8</p>
</td>
<td width="80">
<p>11</p>
</td>
<td width="76">
<p>3</p>
</td>
</tr>
<tr>
<td width="76">
<p>Слепов</p>
</td>
<td width="49">
<p>Т</p>
</td>
<td width="62">
<p>Т</p>
</td>
<td width="62">
<p>4</p>
</td>
<td width="62">
<p>14</p>
</td>
<td width="92">
<p>4</p>
</td>
<td width="64">
<p>4</p>
</td>
<td width="80">
<p>15</p>
</td>
<td width="76">
<p>3</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>2.Смотрим были ли операции у пациентов с указанным именем и фамилией, и сколько их было</p>
<p>R4 := R3[№ Врача, № Госпитализации, № Пациента]</p>
<p>R4</p>
<table width="624">
<tbody>
<tr>
<td width="208">
<p>№ Врача</p>
</td>
<td width="208">
<p>№ Госпитализации</p>
</td>
<td width="208">
<p>№ Пациента</p>
</td>
</tr>
<tr>
<td width="208">
<p>11</p>
</td>
<td width="208">
<p>4</p>
</td>
<td width="208">
<p>4</p>
</td>
</tr>
<tr>
<td width="208">
<p>15</p>
</td>
<td width="208">
<p>14</p>
</td>
<td width="208">
<p>4</p>
</td>
</tr>
</tbody>
</table>
<p>R5 := R4 JOIN &ldquo;Операциями&rdquo;</p>
<p>R5</p>
<table width="624">
<tbody>
<tr>
<td width="104">
<p>№ Врача</p>
</td>
<td width="104">
<p>№ Пациента</p>
</td>
<td width="132">
<p>№ Госпитализации</p>
</td>
<td width="128">
<p>№ Операции</p>
</td>
<td width="156">
<p>№ Даты</p>
</td>
</tr>
<tr>
<td width="104">
<p>11</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="132">
<p>4</p>
</td>
<td width="128">
<p>1</p>
</td>
<td width="156">
<p>30</p>
</td>
</tr>
<tr>
<td width="104">
<p>15</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="132">
<p>14</p>
</td>
<td width="128">
<p>3</p>
</td>
<td width="156">
<p>6</p>
</td>
</tr>
</tbody>
</table>
<p>R6 := SUMMARIZE R5 BY (№ Пациента) ADD COUNT() AS &ldquo;Всего операций&rdquo;</p>
<p>R6</p>
<table width="624">
<tbody>
<tr>
<td width="312">
<p>№ Пациента</p>
</td>
<td width="312">
<p>Всего операций</p>
</td>
</tr>
<tr>
<td width="312">
<p>4</p>
</td>
<td width="312">
<p>2</p>
</td>
</tr>
</tbody>
</table>
<p>R7 := R6 WHERE Всего_операций &gt; 1</p>
<p>R7</p>
<table width="624">
<tbody>
<tr>
<td width="312">
<p>№ Пациента</p>
</td>
<td width="312">
<p>Всего операций</p>
</td>
</tr>
<tr>
<td width="312">
<p>4</p>
</td>
<td width="312">
<p>2</p>
</td>
</tr>
</tbody>
</table>
<p>3.Проверяем врачей у пациента по всем госпитализациям за всё время</p>
<p>R8 := R7 JOIN &ldquo;Госпитализации&rdquo;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>R8</p>
<table width="622">
<tbody>
<tr>
<td width="87">
<p>№ Госпитализации</p>
</td>
<td width="89">
<p>№ Специализации</p>
</td>
<td width="89">
<p>№ Палаты</p>
</td>
<td width="89">
<p>№ Пациента</p>
</td>
<td width="89">
<p>№ Врача</p>
</td>
<td width="89">
<p>№ Диагноза</p>
</td>
<td width="89">
<p>Всего операций</p>
</td>
</tr>
<tr>
<td width="87">
<p>4</p>
</td>
<td width="89">
<p>4</p>
</td>
<td width="89">
<p>8</p>
</td>
<td width="89">
<p>4</p>
</td>
<td width="89">
<p>11</p>
</td>
<td width="89">
<p>3</p>
</td>
<td width="89">
<p>2</p>
</td>
</tr>
<tr>
<td width="87">
<p>14</p>
</td>
<td width="89">
<p>4</p>
</td>
<td width="89">
<p>4</p>
</td>
<td width="89">
<p>4</p>
</td>
<td width="89">
<p>15</p>
</td>
<td width="89">
<p>3</p>
</td>
<td width="89">
<p>2</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R9 := R8[№ Врача]</p>
<p>R9</p>
<table width="622">
<tbody>
<tr>
<td width="622">
<p>№ Врача</p>
</td>
</tr>
<tr>
<td width="622">
<p>11</p>
</td>
</tr>
<tr>
<td width="622">
<p>15</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R10 := R9 JOIN &ldquo;Лечащий персонал&rdquo;</p>
<p>&nbsp;</p>
<table width="624">
<tbody>
<tr>
<td width="104">
<p>№ Врача</p>
</td>
<td width="104">
<p>Фамилия</p>
</td>
<td width="104">
<p>Имя</p>
</td>
<td width="104">
<p>Очество</p>
</td>
<td width="104">
<p>№Должности</p>
</td>
<td width="104">
<p>№ Специализации</p>
</td>
</tr>
<tr>
<td width="104">
<p>11</p>
</td>
<td width="104">
<p>С</p>
</td>
<td width="104">
<p>Х</p>
</td>
<td width="104">
<p>Х</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
<tr>
<td width="104">
<p>15</p>
</td>
<td width="104">
<p>П</p>
</td>
<td width="104">
<p>Д</p>
</td>
<td width="104">
<p>Д</p>
</td>
<td width="104">
<p>4</p>
</td>
<td width="104">
<p>4</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>R11 := R10[Фамилия,Имя,Отчество]</p>
<p>R11</p>
<p>&nbsp;</p>
<table width="624">
<tbody>
<tr>
<td width="208">
<p>Фамилия</p>
</td>
<td width="208">
<p>Имя</p>
</td>
<td width="208">
<p>Очество</p>
</td>
</tr>
<tr>
<td width="208">
<p>С</p>
</td>
<td width="208">
<p>Х</p>
</td>
<td width="208">
<p>Х</p>
</td>
</tr>
<tr>
<td width="208">
<p>П</p>
</td>
<td width="208">
<p>Д</p>
</td>
<td width="208">
<p>Д</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
