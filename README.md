# Rsa-Works-with-very-large-numbers-
## Описание проекта
>Данный проект демонстрирует базовую реализацию шифрования RSA с использованием класса для работы с большими числами. Проект может быть расширен для поддержки дополнительных функций, таких как работа с большими текстами и улучшенная обработка ошибок.и. Проект состоит из двух основных файлов: `main.cpp` и `Rsa.h`.

## Файлы

### 1. `main.cpp`

В этом файле реализована основная логика программы, включая генерацию ключей RSA, шифрование и дешифрование сообщений.

#### Функции:

- **`void generateKey(BigNum& e, BigNum& d, BigNum& n)`**
  - Генерирует открытый и закрытый ключи для алгоритма RSA.
  - **Параметры:**
    - `e`: открытая экспонент (e).
    - `d`: закрытая экспонент (d).
    - `n`: модуль (n), произведение двух простых чисел.
  - **Описание:**
    1. Устанавливает значения для простых чисел `p` и `q`.
    2. Вычисляет `n = p * q`.
    3. Вычисляет `phi = (p - 1) * (q - 1)`.
    4. Определяет открытую экспоненту `e`, такой что `Nod(e, phi) = 1`.
    5. Вычисляет закрытую экспоненту `d`, используя формулу `d = (1 + k * phi) / e`.

- **`std::vector<BigNum> Rsa(const std::string& mes, BigNum e, BigNum n)`**
  - Шифрует сообщение с использованием открытого ключа.
  - **Параметры:**
    - `mes`: строка с сообщением для шифрования.
    - `e`: открытая экспонент.
    - `n`: модуль.
  - **Возвращает:** вектор зашифрованных чисел (BigNum).
  - **Описание:**
    1. Преобразует каждую букву сообщения в её ASCII-код и шифрует с помощью формулы `C = M^e mod n`.
    2. Возвращает вектор зашифрованных чисел.

- **`std::string DeRsa(const std::vector<BigNum>& mes, BigNum d, BigNum n)`**
  - Дешифрует зашифрованное сообщение с использованием закрытого ключа.
  - **Параметры:**
    - `mes`: вектор зашифрованных чисел.
    - `d`: закрытая экспонент.
    - `n`: модуль.
  - **Возвращает:** строку с дешифрованным сообщением.
  - **Описание:**
    1. Применяет формулу `M = C^d mod n` для каждого зашифрованного числа.
    2. Преобразует результаты обратно в символы и формирует строку.

- **`int main()`**
  - Основная функция, которая выполняет программу.
  - Генерирует ключи, шифрует сообщение, выводит зашифрованное сообщение и затем дешифрует его, выводя оригинал.
---
### 2. `Rsa.h`

Этот файл содержит определение класса `BigNum`, который используется для работы с большими целыми числами, необходимыми для алгоритма RSA.

#### Класс `BigNum`

- **`BigNum()`**
  - Конструктор по умолчанию, инициализирующий число равным "0".

- **`BigNum(const string& value)`**
  - Конструктор, инициализирующий объект класса `BigNum` с заданным значением.

- **`void Print() const`**
  - Выводит значение числа в консоль.

- **`bool isSmaller(const string& str1, const string& str2) const`**
  - Сравнивает две строки чисел и определяет, является ли первая строка меньше второй.

- **`BigNum operator+(const BigNum& str) const`**
  - Перегрузка оператора сложения для суммирования двух больших чисел.

- **`string Minus(const string& str1, const string& str2) const`**
  - Вычитает второе число из первого (строковое представление).

- **`BigNum operator-(const BigNum& str) const`**
  - Перегрузка оператора вычитания.

- **`friend BigNum operator%(const BigNum& dividend, const BigNum& divisor)`**
  - Перегрузка оператора взятия остатка от деления.

- **`bool operator!=(const BigNum& other) const`**
  - Проверяет, не равны ли два числа.

- **`bool operator==(const BigNum& other) const`**
  - Проверяет, равны ли два числа.

- **`bool operator>(const BigNum& other) const`**
  - Проверяет, больше ли одно число другого.

- **`static BigNum Nod(BigNum a, BigNum b)`**
  - Вычисляет наибольший общий делитель (НОД) двух чисел.

- **`BigNum operator/(const BigNum& divisor) const`**
  - Перегрузка оператора деления.

- **`BigNum operator*(const BigNum& other) const`**
  - Перегрузка оператора умножения.

- **`static BigNum PowNum(BigNum base, BigNum exp, BigNum mod)`**
  - Вычисляет `base^exp mod mod` с использованием метода быстрого возведения в степень.

- **`char toASCII() const`**
  - Преобразует значение числа в соответствующий ASCII-символ.


--- 
