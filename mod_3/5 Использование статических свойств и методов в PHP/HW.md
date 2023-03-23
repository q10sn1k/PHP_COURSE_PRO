# Домашнее задание

## Задача 1

Реализуйте класс Calculator, у которого будут статические методы для выполнения основных математических операций: add, subtract, multiply и divide. \
Каждый метод должен принимать два аргумента и возвращать результат вычисления.

## Решение

```php
<?php

// Класс калькулятора
class Calculator {
  
  // Статические методы для выполнения математических операций
  public static function add(float $a, float $b): float {
    return $a + $b;
  }
  
  public static function subtract(float $a, float $b): float {
    return $a - $b;
  }
  
  public static function multiply(float $a, float $b): float {
    return $a * $b;
  }
  
  public static function divide(float $a, float $b): float {
    if ($b == 0) {
      throw new Exception('Деление на ноль');
    }
    return $a / $b;
  }
}

// Примеры использования
echo Calculator::add(2, 3); // выводит 5
echo Calculator::subtract(10, 5); // выводит 5
echo Calculator::multiply(2.5, 3); // выводит 7.5
echo Calculator::divide(10, 2); // выводит 5
echo Calculator::divide(10, 0); // генерирует исключение

```

## Задача 2

Написать класс CheckingAccount, который наследует абстрактный класс BankAccount и расширяет его функциональность добавлением комиссии за снятие денег с чекового счета.\
Класс должен иметь методы для установки/изменения значения комиссии и получения информации о счете, включая текущий баланс и размер комиссии.\
Также требуется написать примеры использования методов класса.

## Решение

```php
<?php

// Абстрактный класс банковского счета
abstract class BankAccount {
    protected float $balance;
    protected string $ownerName;

    public function __construct(string $ownerName, float $balance = 0) {
        $this->balance = $balance;
        $this->ownerName = $ownerName;
    }

    public function getBalance(): float {
        return $this->balance;
    }

    public function deposit(float $amount): void {
        $this->balance += $amount;
    }

    abstract public function withdraw(float $amount): void;
}

// Класс для чекового счета
class CheckingAccount extends BankAccount {
    private float $fee;

    public function __construct(string $ownerName, float $balance = 0, float $fee = 0) {
        parent::__construct($ownerName, $balance);
        $this->fee = $fee;
    }

    public function withdraw(float $amount): void {
        $this->balance -= $amount + $this->fee;
    }

    public function getFee(): float {
        return $this->fee;
    }

    public function setFee(float $fee): void {
        $this->fee = $fee;
    }

    public function getInfo(): string {
        return "Счет № {$this->ownerName}<br>" .
            "Баланс: {$this->balance} руб.<br>" .
            "Комиссия: {$this->fee} руб.";
    }
}

$checking = new CheckingAccount("Иван Сергеев", 1000, 10);
echo $checking->getInfo() . "<br>"; // Счет № Иван Сергеев<br>Баланс: 1000 руб.<br>Комиссия: 10 руб.

$checking->withdraw(100);
echo $checking->getInfo() . "<br>"; // Счет № Иван Сергеев<br>Баланс: 890 руб.<br>Комиссия: 10 руб.

$checking->setFee(15);
echo $checking->getInfo() . "<br>"; // Счет № Иван Сергеев<br>Баланс: 890 руб.<br>Комиссия: 15 руб.

```

## Задача 3

Реализуйте класс Book,  у которого будет статическое свойство count для подсчета количества созданных объектов этого класса, а также метод getInfo для получения информации о книге.

## Решение

```php
<?php

abstract class Book {
    protected string $title;
    protected string $author;
    protected int $pages;
    protected int $year;

    protected static int $count = 0;

    public function __construct(string $title, string $author, int $pages, int $year) {
        $this->title = $title;
        $this->author = $author;
        $this->pages = $pages;
        $this->year = $year;
        self::$count++;
    }

    public static function getCount(): int {
        return self::$count;
    }

    public function getInfo(): string {
        return "Название: {$this->title}, Автор: {$this->author}, Кол-во страниц: {$this->pages}, Год издания: {$this->year}";
    }

}

class Novel extends Book {
    protected string $genre;

    public function __construct(string $title, string $author, int $pages, int $year, string $genre) {
        parent::__construct($title, $author, $pages, $year);
        $this->genre = $genre;
    }

    public function getInfo(): string {
        return parent::getInfo() . ", Жанр: {$this->genre}";
    }
}

class Textbook extends Book {
    protected string $subject;

    public function __construct(string $title, string $author, int $pages, int $year, string $subject) {
        parent::__construct($title, $author, $pages, $year);
        $this->subject = $subject;
    }

    public function getInfo(): string {
        return parent::getInfo() . ", Предмет: {$this->subject}";
    }
}

// Создаем объекты книг
$novel = new Novel("Мастер и Маргарита", "Михаил Булгаков", 480, 1967, "Роман");
$textbook = new Textbook("Основы программирования на PHP", "Дмитрий Руденко", 240, 2022, "Программирование");

// Выводим информацию о книгах
echo $novel->getInfo() . "<br>";
echo $textbook->getInfo() . "<br>";

// Выводим количество созданных книг
echo "Количество книг: " . Book::getCount() . "<br>";

```