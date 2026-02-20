```mermaid
graph TD
    %% Начало
    Start([НАЧАЛО]) --> Q1
    
    %% Вопрос 1: Бюджет
    Q1{Вопрос 1: Бюджет?}
    Q1 -->|< 800 000 руб.| A1[Класс A<br>малолитражки]
    Q1 -->|800 000-1,5 млн| A2[Класс B<br>компактные]
    Q1 -->|> 1,5 млн руб.| Q2_1
    
    %% Связующие узлы для сохранения структуры
    A1 --> Q2_2
    A2 --> Q2_2
    
    %% Вопрос 2: Цель (два места в схеме)
    Q2_1{Вопрос 2: Цель?} -->|Город/семья| C1[Класс C /<br>Компактные кроссоверы]
    Q2_1 -->|Бездорожье/дача| C2[Полный привод<br>Клиренс > 180 мм<br>Внедорожники]
    
    Q2_2{Вопрос 2: Цель?} -->|Город| City
    Q2_2 -->|Семья| Family
    Q2_2 -->|Природа| Nature
    
    City[Город] --> Q3
    Family[Семья] --> Q3
    Nature[Природа] --> Q3
    
    C1 --> Q4_2
    C2 --> Q4_2
    
    %% Вопрос 3: Тип кузова
    Q3{Вопрос 3: Тип кузова?} -->|Седан| Sedan[Седан]
    Q3 -->|Хэтчбек| Hatch[Хэтчбек]
    Q3 -->|Универсал| Universal[Универсал]
    
    Sedan --> Q4_1
    Hatch --> Q4_1
    Universal --> Q4_1
    
    %% Вопрос 4: КПП (первый)
    Q4_1{Вопрос 4: Тип КПП?} -->|Автомат| AT1[Автомат]
    Q4_1 -->|Механика| MT1[Механика]
    Q4_1 -->|Не важно| Any1[Не важно]
    
    AT1 --> Q5
    MT1 --> Q5
    Any1 --> Q5
    
    %% Вопрос 4: КПП (второй)
    Q4_2{Вопрос 4: КПП?} -->|Автомат/Механика| ATMT[Автомат/Механика]
    ATMT --> Q5_2
    
    %% Вопрос 5: Двигатель
    Q5_2{Вопрос 5: Двигатель?} -->|Типы| Engine[Бензин/Дизель/<br>Гибрид/Электро]
    Engine --> Q5
    
    %% Вопрос 5: Приоритет
    Q5{Вопрос 5: Приоритет?} -->|Экономичность| Eco[Экономичность]
    Q5 -->|Безопасность| Safe[Безопасность]
    Q5 -->|Комфорт| Comfort[Комфорт]
    
    Eco --> Q6
    Safe --> Q6
    Comfort --> Q6
    
    %% Вопрос 6: Год и пробег
    Q6{Вопрос 6: Год и пробег?} -->|Новый / до 3 лет| New[Новый / до 3 лет]
    Q6 -->|Подержанный > 3 лет| Used[Подержанный > 3 лет]
    
    New --> Q7
    Used --> Q7
    
    %% Вопрос 7: Регион и опции
    Q7{Вопрос 7: Регион и опции?} -->|Северный / холодный| North[Северный / холодный]
    Q7 -->|Южный / средняя полоса| South[Южный / средняя полоса]
    
    North --> Heat[Подогревы: сиденья,<br>руль, зеркала]
    South --> Cond[Кондиционер обязательно]
    
    Heat --> Search[ПОИСК В БАЗЕ ДАННЫХ]
    Cond --> Search
    
    %% Поиск и проверка результатов
    Search --> Found{Найдены варианты?}
    
    Found -->|ДА| Rank[Применить правила ранжирования]
    Found -->|НЕТ| Expand[Расширить параметры<br>увеличить бюджет,<br>снизить требования]
    
    Expand --> Search
    
    Rank --> Top3[ТОП-3 рекомендации]
    
    %% Предупреждения
    Top3 --> Warnings[Добавить предупреждения:<br>- Проверить историю ДТП (для б/у)<br>- Риски по моделям<br>- Налог на роскошь]
    
    %% Финальный результат
    Warnings --> Result[ВЫВОД РЕЗУЛЬТАТА<br>Список автомобилей с:<br>- маркой и моделью<br>- годом и пробегом<br>- ценой<br>- ТТХ<br>- стоимостью обслуживания<br>- обоснованием выбора]
    
    Result --> Finish([КОНЕЦ])
    
    %% Стили для разных типов узлов
    style Start fill:#2980b9,color:#fff
    style Finish fill:#27ae60,color:#fff
    style Q1 fill:#f39c12
    style Q2_1 fill:#f39c12
    style Q2_2 fill:#f39c12
    style Q3 fill:#f39c12
    style Q4_1 fill:#f39c12
    style Q4_2 fill:#f39c12
    style Q5 fill:#f39c12
    style Q5_2 fill:#f39c12
    style Q6 fill:#f39c12
    style Q7 fill:#f39c12
    style Found fill:#e74c3c,color:#fff
    style Search fill:#3498db,color:#fff
    style Result fill:#9b59b6,color:#fff
    style Warnings fill:#e67e22,color:#fff
    style Rank fill:#1abc9c,color:#fff
    style Top3 fill:#1abc9c,color:#fff
    
    %% Стили для узлов с ответами
    style A1 fill:#ecf0f1
    style A2 fill:#ecf0f1
    style C1 fill:#ecf0f1
    style C2 fill:#ecf0f1
    style City fill:#ecf0f1
    style Family fill:#ecf0f1
    style Nature fill:#ecf0f1
    style Sedan fill:#ecf0f1
    style Hatch fill:#ecf0f1
    style Universal fill:#ecf0f1
    style AT1 fill:#ecf0f1
    style MT1 fill:#ecf0f1
    style Any1 fill:#ecf0f1
    style ATMT fill:#ecf0f1
    style Engine fill:#ecf0f1
    style Eco fill:#ecf0f1
    style Safe fill:#ecf0f1
    style Comfort fill:#ecf0f1
    style New fill:#ecf0f1
    style Used fill:#ecf0f1
    style North fill:#ecf0f1
    style South fill:#ecf0f1
    style Heat fill:#ecf0f1
    style Cond fill:#ecf0f1
    style Expand fill:#e74c3c,color:#fff
```
