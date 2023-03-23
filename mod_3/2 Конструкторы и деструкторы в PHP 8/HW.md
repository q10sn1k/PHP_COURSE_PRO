# Домашнее задание

## Задача 1

Напишите класс Car, который будет иметь свойства model, year и color. \
Метод getInfo(), который будет возвращать информацию о машине, и метод paint(), который будет менять цвет машины.
Реализуйте конструктор.

## Решение

```php
<?php

class Car {
  // Свойства класса
  public $model;
  public $year;
  public $color;

  // Конструктор
  public function __construct($model, $year, $color) {
    $this->model = $model;
    $this->year = $year;
    $this->color = $color;
  }

  // Методы класса
  public function getInfo() {
    return "Модель: " . $this->model . ", Год выпуска: " . $this->year . ", Цвет: " . $this->color;
  }

  public function paint($color) {
    $this->color = $color;
  }
}

// Создадим объект класса
$car = new Car("BMW", 2022, "Черный");

echo $car->getInfo() . "<br>";

$car->paint("Белый");

echo $car->getInfo();
```


## Задача 2

Напишите класс BankAccount, который будет иметь свойства balance. /
Методы deposit(), который будет добавлять деньги на счет, и метод withdraw(), который будет снимать деньги со счета.
Реализуйте конструктор.

## Решение

```php
<?php

class BankAccount {
    // Свойства класса
    public $balance;

    // Конструктор
    public function __construct($balance) {
        $this->balance = $balance;
    }

    // Методы класса
    public function deposit($amount) {
        $this->balance += $amount;
    }

    public function withdraw($amount) {
        if ($this->balance >= $amount) {
            $this->balance -= $amount;
        } else {
            echo "Недостаточно средств на счете";
        }
    }
}

// Создадим объект класса
$bankAccount = new BankAccount(1000);

echo "Баланс счета: " . $bankAccount->balance . "<br>";

$bankAccount->deposit(500);
echo "Баланс счета после пополнения: " . $bankAccount->balance . "<br>";

$bankAccount->withdraw(200);
echo "Баланс счета после снятия: " . $bankAccount->balance . "<br>";
$bankAccount->withdraw(2000);
echo  "<br>";
echo "Баланс счета после попытки снятия недостаточной суммы: " . $bankAccount->balance;

```

## Задача 3

Напишите класс Book, который будет иметь свойства title (название), author (автор) и price (цена). \
Методы getInfo(), который будет возвращать информацию о книге, и метод setPrice(), который будет устанавливать цену на книгу.
Реализуйте конструктор.

## Решение

```php
<?php

class Book {
  // Свойства класса
  public $title;
  public $author;
  public $price;

  // Конструктор
  public function __construct($title, $author, $price) {
    $this->title = $title;
    $this->author = $author;
    $this->price = $price;
  }

  // Методы класса
  public function getInfo() {
    return "Название: " . $this->title . ", Автор: " . $this->author . ", Цена: " . $this->price;
  }

  public function setPrice($price) {
    $this->price = $price;
  }
}

// Создадим объект класса
$book = new Book("Мастер и Маргарита", "Михаил Булгаков", 500);

echo $book->getInfo() . "<br>";

$book->setPrice(600);

echo $book->getInfo();
```

## Задача 4

Напишите класс Circle, который будет иметь свойство radius./
Методы getArea(), который будет возвращать площадь круга, и  getCircumference(), который будет возвращать длину окружности.
Реализуйте конструктор.

## Решение

```php
<?php

class Circle {
  // Свойства класса
  public $radius;

  // Конструктор
  public function __construct($radius) {
    $this->radius = $radius;
  }

  // Методы класса
  public function getArea() {
    return pi() * pow($this->radius, 2);
  }

  public function getCircumference() {
    return 2 * pi() * $this->radius;
  }
}

// Создадим объект класса
$circle = new Circle(5);

echo "Площадь круга: " . $circle->getArea() . "<br>";
echo "Длина окружности: " . $circle->getCircumference();

```