## Завдання 1. Перевірка унікальності паролів за допомогою фільтра Блума

Створіть функцію для перевірки унікальності паролів за допомогою фільтра Блума. Ця функція має визначати, чи використовувався пароль раніше, без необхідності зберігати самі паролі.

**Технічні умови**

1. Реалізуйте клас `BloomFilter`, який забезпечує додавання елементів до фільтра та перевірку наявності елемента у фільтрі.
2. Реалізуйте функцію `check_password_uniqueness`, яка використовує екземпляр `BloomFilter` та перевіряє список нових паролів на унікальність. Вона має повертати результат перевірки для кожного пароля.
3. Забезпечте коректну обробку всіх типів даних. Паролі слід обробляти просто як рядки, без хешування. Порожні або некоректні значення також мають бути враховані та оброблені належним чином.
4. Функція та клас мають працювати з великими наборами даних, використовуючи мінімум пам’яті.

**Приклад використання**

```
if __name__ == "__main__":
    # Ініціалізація фільтра Блума
    bloom = BloomFilter(size=1000, num_hashes=3)

    # Додавання існуючих паролів
    existing_passwords = ["password123", "admin123", "qwerty123"]
    for password in existing_passwords:
        bloom.add(password)

    # Перевірка нових паролів
    new_passwords_to_check = ["password123", "newpassword", "admin123", "guest"]
    results = check_password_uniqueness(bloom, new_passwords_to_check)

    # Виведення результатів
    for password, status in results.items():
        print(f"Пароль '{password}' - {status}.")

```

**Результат**

![result](./assets//task01.jpg)

## Завдання 2. Порівняння продуктивності HyperLogLog із точним підрахунком унікальних елементів

Створіть скрипт для порівняння точного підрахунку унікальних елементів та підрахунку за допомогою `HyperLogLog`.

**Технічні умови**

1. Завантажте набір даних із реального лог-файлу `lms-stage-access.log`, що містить інформацію про IP-адреси.
2. Реалізуйте метод для точного підрахунку унікальних IP-адрес за допомогою структури set.
3. Реалізуйте метод для наближеного підрахунку унікальних IP-адрес за допомогою `HyperLogLog`.
4. Проведіть порівняння методів за часом виконання.

**Приклад виводу результатів**

```
Результати порівняння:
                       Точний підрахунок   HyperLogLog
Унікальні елементи              100000.0      99652.0
Час виконання (сек.)                0.45          0.1
```

**Результат**

![result](./assets//task02.jpg)
