# Домашнее задание к работе 2

## Условие задачи

Дано вещественное число A, содержащее две цифры до запятой и три после. Получить новое число, поменяв в числе A целую и дробную части. (было 21,317 стало 317,21)

## 1. Алгоритм и блок-схема

### Алгоритм

1. **Начало**
2. **Объявить константы:**
   * `DIGITS_BEFORE` = 2 — количество цифр в целой части.
   * `DIGITS_AFTER` = 3 — количество цифр в дробной части.
3. **Задать исходные данные:**
   * `A` — исходное вещественное число (например, 21.317).
4. **Вычислить целую часть числа:**
   * `int_part = (int)A` — отбрасываем дробную часть.
5. **Вычислить дробную часть как целое число:**
   * `frac_part = (int)((A - int_part) * 1000.0f + 0.5f)` — выделяем дробную часть, умножаем на 1000 и округляем.
6. **Сформировать новое число:**
   * `new_A = frac_part + int_part / 100.0f` — дробная часть становится целой, а целая часть делится на 100 (так как в ней 2 цифры).
7. **Вывести результаты расчетов с подстановкой всех значений в текст.**
8. **Конец**

### Блок-схема

https://www.draw.io?lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=%D0%A1%D1%85%D0%B5%D0%BC%D0%B0%20%D0%B4%D0%BB%D1%8F%20%D0%BB%D0%B0%D0%B1%D1%8B2%20%D0%B4%D0%B7.drawio#R5VnJbtswEP0aAU6BGNRuHy07aYGiaIoc2p4CRmIkobQp0PLWr%2B9QolYqtaM4UZoewpDD4fZm3gwpa%2BZ8uf%2FIcRJ9YQGhmoGCvWYuNMPQLWTBPyE55BLXmeSCkMeBVKoEt%2FFvIoVISjdxQNYNxZQxmsZJU%2Biz1Yr4aUOGOWe7ptoDo81VExwSRXDrY6pKv8dBGuXSieFW8k8kDqNiZd2Z5j1LXCjLk6wjHLBdTWReaeacM5bmteV%2BTqgAr8AlH3f9SG%2B5MU5W6SkDvlmLeRwZ3uf59tf2%2Bis12My%2BlLNsMd3IA2sLpE0XovSQttC1iVvUofSy8koeKD0UKMFKYBBoeLsoTsltgn3RswOfAFmULim0dKjK5QhPyf7Rc%2BglOuBWhC1Jyg%2BgIgeYlgRUelSB764yj17IopppJlKGpUeE5cwVaFCRuD0BQ0PFUMFnFcyEM0LLp3i9jv0uWEig%2BOJRUGqntjsOXcg4oTiNt83pu5CQK9ywGBauMJ9Ox3YDdR214FyzDfeJHFd3w9ZUFmqaT7dbE6WYhyRVJgL88KGmlgiF9ZO23CbI8RFWYwRU8l1UvlJaor%2F7mN0UzErPkIQTJUTSjIVT2JRDwcDePYdaKGqjTOO6pu1l5DVrFJ7UKAxBGBn62NTdC8VZIVAlogrehykllIUcL2GNhPAYDkt4u%2B%2Bm6hiA%2F6UDHQsAzksFAOv9B4A2a8v8%2FFz6GyfS%2F1xssxVbwUJ3gLPYYyZAI5AAK9AMyIWXwoFX9%2BskM5LSPgsNVQpytlkFRJwDDZNTB%2BeU83xOwdn54YfAEMK6bP6UkGaNxb7ROsjWqVyEm2jmq385hTtw0m4Y1UR2P84qE7mtic6XsjvXOXlfdkP%2FZdK1qzjmA8d%2BdwQZjSCGoEsxpQwyQvoB%2FuD6hIS6Ad6GwD8vjseWtkafWNOZ74cONuZk6GAzff8JvM0Vy%2BqZwJWJpq%2BbwHX1yboiu7tZSb4GHTN%2B1TM8bCdj31jQryeFxm8xZZd2GIxF%2Bv%2FxEG6gbrevr31p5LQv1C9No8efneD6XufjU%2FLs334ulkAPx5NXfC%2BecEfV7bdEKMc9E6Fc%2FbRL6tkIpb4sM0LNaiTKP6vaGcUc1eav%2BRHVbKGFTmRFj6%2Bo0Ky%2BcudwV78VmFd%2FAA%3D%3D

## 2. Реализация программы

```c
#include <stdio.h>
#include <locale.h>

int main() {
    // Объявление и инициализация констант
    const int DIGITS_BEFORE = 2; // Количество цифр до запятой
    const int DIGITS_AFTER = 3;  // Количество цифр после запятой

    setlocale(LC_CTYPE, "");

    // Шаг 1: Задание исходного значения переменной
    float A; // Исходное число

    printf("Введите вещественное число A (например, 21.317): ");
    scanf("%f", &A);

    // Шаг 2: Разделение числа на целую и дробную части
    // Находим целую часть (отбрасываем дробную)
    int int_part = (int)A; 
    
    // Находим дробную часть как целое число (317) без функции round
    // 1. Вычитаем целую часть, чтобы получить чистую дробь (0.317)
    // 2. Умножаем на 1000, чтобы сместить запятую (317.0)
    // 3. Прибавляем 0.5 и приводим к int для математического округления
    int frac_part = (int)((A - int_part) * 1000.0f + 0.5f); 

    // Шаг 3: Формирование нового числа
    // Дробная часть становится целой, а целая часть делится на 100
    float new_A = (float)frac_part + (float)int_part / 100.0f;

    // Шаг 4: Форматированный вывод результатов
    printf("\nПЕРЕСТАНОВКА ЦЕЛОЙ И ДРОБНОЙ ЧАСТЕЙ ЧИСЛА\n");
    printf("==========================================\n\n");
    printf("УСЛОВИЯ:\n");
    printf("- Исходное число A: %.3f\n", A);
    printf("- Количество цифр до запятой: %d\n", DIGITS_BEFORE);
    printf("- Количество цифр после запятой: %d\n\n", DIGITS_AFTER);

    printf("РАСЧЕТ:\n");
    printf("- Выделенная целая часть: %d\n", int_part);
    printf("- Выделенная дробная часть: %d\n", frac_part);
    printf("- Формула нового числа: %d + %d / 100.0\n", frac_part, int_part);
    printf("==========================================\n");
    printf("НОВОЕ ЧИСЛО: %.2f\n", new_A);

    return 0;
}


## 3. Результаты работы  программы

Введите вещественное число A (например, 21.317): 24.675

ПЕРЕСТАНОВКА ЦЕЛОЙ И ДРОБНОЙ ЧАСТЕЙ ЧИСЛА
==========================================

УСЛОВИЯ:
- Исходное число A: 24.675
- Количество цифр до запятой: 2
- Количество цифр после запятой: 3

РАСЧЕТ:
- Выделенная целая часть: 24
- Выделенная дробная часть: 675
- Формула нового числа: 675 + 24 / 100.0
==========================================
НОВОЕ ЧИСЛО: 675.24

## 4. Информация о разработчике
Щербаков Дмитрий бИЦТ-261
