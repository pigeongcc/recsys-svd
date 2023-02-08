# Рекомендательная система (SVD)

Мое решение тестового задания на стажировку в Университете Иннополис.

## Задание
Построить рекомендательную систему для предложения пользователям релевантных компьютерных игр. Входные данные:
- *user.csv*
  - ID пользователя
  - ID игры
  - рейтинг: оценка пользователем данной игры
- *games.csv*
  - ID игры
  - название игры
  - жанр игры
  - цена (в $, либо Free)

## Решение

- Предобработка данных: проверки на
  - кодировку текста
  - отсутствующие значения
  - дубликаты
- Вывод новых признаков:
  - is_free (флаг бесплатной игры)
  - год выхода игры
- Векторизация жанра игры (one-hot encoding). Сведение редких жанров (встречаются реже заданного порога) в новый жанр Rare.
- Построение модели
  - Singular Value Decomposition
  - RMSE для предсказания рейтинга 2.76 (по 10-балльной шкале). Адекватный результат при равномерном разбросе рейтинга по датасету от 1 до 10, учитывая cold start problem (разреженная матрица рейтингов).
- Интерфейс для вывода рекомендаций
