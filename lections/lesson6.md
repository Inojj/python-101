### **План занятия по классам и объектно-ориентированному программированию (ООП) в Python**  

**Цель занятия**:  
Познакомить участников с основами ООП в Python, научить создавать и использовать классы, объяснить ключевые принципы ООП: инкапсуляция, наследование и полиморфизм.

---

## **1. Введение в ООП (15 минут)**
### 🔹 Что такое ООП?
- Парадигмы программирования: процедурное, функциональное, объектно-ориентированное.
- Основные принципы ООП: **инкапсуляция, наследование, полиморфизм**.
- Примеры использования ООП в реальных проектах.

### 🔹 Зачем нужны классы?
- Понятие объекта и класса.
- Разница между функциями и методами классов.
- Примеры из реальной жизни: объект — машина, класс — шаблон машины.

---

## **2. Основы классов в Python (30 минут)**
### 🔹 Определение класса и создание объектов  
```python
class Car:
    def __init__(self, brand, model, year):
        self.brand = brand
        self.model = model
        self.year = year

    def info(self):
        return f"{self.brand} {self.model}, {self.year}"

# Создание объекта
car1 = Car("Toyota", "Camry", 2020)
print(car1.info())
```
- Разбор примера, объяснение `__init__`, `self`.
- Атрибуты экземпляра и класса.

### 🔹 Методы классов  
- Различие между **методами экземпляра, класса и статическими методами**.
```python
class Example:
    class_variable = "Class Variable"

    def instance_method(self):
        return "Instance method called", self

    @classmethod
    def class_method(cls):
        return "Class method called", cls

    @staticmethod
    def static_method():
        return "Static method called"
```

- Примеры их использования.

---

## **3. Инкапсуляция (20 минут)**
### 🔹 Доступ к атрибутам
- `public`, `protected` и `private` атрибуты:
```python
class Person:
    def __init__(self, name, age):
        self.name = name        # public
        self._protected = age   # protected
        self.__private = age    # private
```
- Как работать с приватными переменными (`getter`, `setter`):
```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance

    def get_balance(self):
        return self.__balance

    def set_balance(self, amount):
        if amount >= 0:
            self.__balance = amount
        else:
            print("Баланс не может быть отрицательным!")

account = BankAccount(1000)
print(account.get_balance())
account.set_balance(2000)
print(account.get_balance())
```

---

## **4. Наследование (20 минут)**
### 🔹 Что такое наследование?
- Зачем нужно наследование?
- Пример базового и дочернего класса:
```python
class Animal:
    def __init__(self, name):
        self.name = name

    def make_sound(self):
        return "Some generic sound"

class Dog(Animal):
    def make_sound(self):
        return "Bark"

dog = Dog("Buddy")
print(dog.name, dog.make_sound())  
```

- Перекрытие (`override`) методов родительского класса.

---

## **5. Полиморфизм (15 минут)**
### 🔹 Понятие полиморфизма
- Один интерфейс – разное поведение.
- Пример полиморфизма с методами:
```python
class Cat:
    def speak(self):
        return "Meow"

class Dog:
    def speak(self):
        return "Bark"

animals = [Cat(), Dog()]
for animal in animals:
    print(animal.speak())  # Разный результат для разных классов
```

---

## **6. Практическое задание (30 минут)**
### Задание: Создать систему управления сотрудниками  
- Создать базовый класс `Employee` с атрибутами `name`, `age`, `salary` и методом `info()`.
- Создать классы `Manager` и `Developer`, унаследованные от `Employee`, с дополнительными атрибутами и переопределением `info()`.
- Написать код, демонстрирующий создание объектов и вызов методов.

**Пример результата**:  
```python
class Employee:
    def __init__(self, name, age, salary):
        self.name = name
        self.age = age
        self.salary = salary

    def info(self):
        return f"{self.name}, {self.age} лет, зарплата: {self.salary}"

class Manager(Employee):
    def __init__(self, name, age, salary, department):
        super().__init__(name, age, salary)
        self.department = department

    def info(self):
        return f"Менеджер {self.name}, отдел: {self.department}, зарплата: {self.salary}"

class Developer(Employee):
    def __init__(self, name, age, salary, language):
        super().__init__(name, age, salary)
        self.language = language

    def info(self):
        return f"Разработчик {self.name}, язык: {self.language}, зарплата: {self.salary}"

dev = Developer("Алексей", 25, 80000, "Python")
manager = Manager("Ирина", 35, 100000, "Продажи")

print(dev.info())
print(manager.info())
```

---

## **7. Вопросы и обсуждение (10-15 минут)**
- Разбор трудностей, вопросов.
- Как использовать ООП в реальных проектах?
- Обзор дополнительных тем: **абстрактные классы, интерфейсы, миксины**.

---

## **8. Дополнительные материалы и домашнее задание**
### **📖 Домашнее задание**
1. **Создать систему учета студентов и преподавателей**:
   - Базовый класс `Person` (имя, возраст).
   - Классы `Student` и `Teacher`, унаследованные от `Person`.
   - `Student` должен иметь атрибут `grade`, `Teacher` — `subject`.
   - Перезаписать метод `info()`.

2. **Изучить дополнительные темы**:
   - `@property`, `@staticmethod`, `@classmethod`.
   - Исключения в ООП (`try-except` в методах).
   - Работа с `__str__` и `__repr__`.

---

### **🔹 Итог**
Этот план занятия поможет слушателям понять основы ООП в Python и начать применять их на практике. 🚀