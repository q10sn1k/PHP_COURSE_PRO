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

Реализуйте класс BankAccount, у которого будет статическое свойство interestRate для хранения процентной ставки по счету, а также методы setInterestRate и getInterestRate для установки и получения значения процентной ставки соответственно.

## Решение

```php
class BankAccount {
  protected float $balance;
  protected string $ownerName;
  protected static float $interestRate = 0;

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

  public static function setInterestRate(float $rate): void {
    self::$interestRate = $rate;
  }

  public static function getInterestRate(): float {
    return self::$interestRate;
  }
}


$account1 = new BankAccount("Иван Сергеев", 1000);
$account2 = new BankAccount("Анна Петрова", 5000);

BankAccount::setInterestRate(3);

echo "Процентная ставка: " . BankAccount::getInterestRate() . "<br>";
echo "Баланс счета 1: " . $account1->getBalance() . "<br>";
echo "Баланс счета 2: " . $account2->getBalance() . "<br>";

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