-- Создание функции для форматирования секунд
DELIMITER //

CREATE FUNCTION format_seconds(total_seconds INT)
RETURNS VARCHAR(100)
DETERMINISTIC
BEGIN
    DECLARE days INT;
    DECLARE hours INT;
    DECLARE minutes INT;
    DECLARE seconds INT;

    SET days = total_seconds DIV 86400;
    SET hours = (total_seconds % 86400) DIV 3600;
    SET minutes = (total_seconds % 3600) DIV 60;
    SET seconds = total_seconds % 60;

    RETURN CONCAT(days, ' days ', hours, ' hours ', minutes, ' minutes ', seconds, ' seconds');
END //

DELIMITER ;

-- Пример использования функции
SELECT format_seconds(123456) AS formatted_time;

-- Вывод четных чисел от 1 до 10
SELECT num
FROM (
    SELECT 1 AS num UNION ALL
    SELECT 2 UNION ALL
    SELECT 3 UNION ALL
    SELECT 4 UNION ALL
    SELECT 5 UNION ALL
    SELECT 6 UNION ALL
    SELECT 7 UNION ALL
    SELECT 8 UNION ALL
    SELECT 9 UNION ALL
    SELECT 10
) AS numbers
WHERE num % 2 = 0;
