# Домашнее задание

## Задача 1

Напишите класс Car, который будет иметь свойства model, year и color. \
Метод getInfo(), который будет возвращать информацию о машине, и метод paint(), который будет менять цвет машины.

## Решение

```php
class Car {
  // Свойства класса
  public $model;
  public $year;
  public $color;

  // Методы класса
  public function getInfo() {
    return "Модель: " . $this->model . ", Год выпуска: " . $this->year . ", Цвет: " . $this->color;
  }

  public function paint($color) {
    $this->color = $color;
  }
}

// Создадим объект класса
$car = new Car();
$car->model = "Toyota";
$car->year = 2020;
$car->color = "красный";

echo $car->getInfo() . "<br>";
$car->paint("синий");
echo $car->getInfo();

```
## Задача 2

Необходимо написать класс Calculator с методами add(), subtract(), multiply() и divide(), которые будут производить математические операции сложения, вычитания, умножения и деления соответственно.\
Методы должны принимать два числовых аргумента и возвращать результат выполненной операции.\
Для выполнения арифметических операций можно использовать стандартные математические операторы (+, -, *, /).

## Решение

```php
class Calculator {
  // Методы класса
  public function add($a, $b) {
    return $a + $b;
  }

  public function subtract($a, $b) {
    return $a - $b;
  }

  public function multiply($a, $b) {
    return $a * $b;
  }

  public function divide($a, $b) {
    return $a / $b;
  }
}

// Создадим объект класса
$calculator = new Calculator();

echo "Сложение: " . $calculator->add(5, 3) . "<br>";
echo "Вычитание: " . $calculator->subtract(5, 3) . "<br>";
echo "Умножение: " . $calculator->multiply(5, 3) . "<br>";
echo "Деление: " . $calculator->divide(5, 3);

```

## Задача 3

Напишите класс BankAccount, который будет иметь свойства balance. /
Методы deposit(), который будет добавлять деньги на счет, и метод withdraw(), который будет снимать деньги со счета.

## Решение

```php
class BankAccount {
  // Свойства класса
  private $balance = 0;

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

  public function getBalance() {
    return $this->balance;
  }
}

// Создадим объект класса
$bankAccount = new BankAccount();

$bankAccount->deposit(100);
echo "Баланс: " . $bankAccount->getBalance() . "<br>";

$bankAccount->withdraw(50);
echo "Баланс: " . $bankAccount->getBalance() . "<br>";

$bankAccount->withdraw(100);
echo "Баланс: " . $bankAccount->getBalance();

```

## Задача 4

Напишите класс Book, который будет иметь свойства title (название), author (автор) и price (цена). \
Методы getInfo(), который будет возвращать информацию о книге, и метод setPrice(), который будет устанавливать цену на книгу.

## Решение

```php
class Book {
  // Свойства класса
  public $title;
  public $author;
  private $price;

  // Методы класса
  public function getInfo() {
    return "Название книги: " . $this->title . ", Автор: " . $this->author . ", Цена: " . $this->price;
  }

  public function setPrice($price) {
    $this->price = $price;
  }
}

// Создадим объект класса
$book = new Book();
$book->title = "Преступление и наказание";
$book->author = "Федор Достоевский";
$book->setPrice(500);

echo $book->getInfo();

```

## Задача 5

Напишите класс Circle, который будет иметь свойство radius./
Методы getArea(), который будет возвращать площадь круга, и  getCircumference(), который будет возвращать длину окружности.

## Решение

```php
class Circle {
  // Свойства класса
  public $radius;

  // Методы класса
  public function getArea() {
    return pi() * $this->radius * $this->radius;
  }

  public function getCircumference() {
    return 2 * pi() * $this->radius;
  }
}

// Создадим объект класса
$circle = new Circle();
$circle->radius = 5;

echo "Площадь круга: " . $circle->getArea() . "<br>";
echo "Длина окружности: " . $circle->getCircumference();

```
