# Домашнее задание

## Задача 1

Создайте класс Calculator с защищенными свойствами num1 и num2, конструктором и четырьмя методами add(), subtract(), multiply() и divide(), которые будут выполнять соответствующие математические операции с защищенными свойствами.\
Каждый метод должен принимать два числовых аргумента и возвращать результат выполненной операции.

Затем создайте класс ScientificCalculator, наследующийся от класса Calculator и добавляющий защищенное свойство precision(точность) и методы setPrecision() и getPrecision() для установки и получения значения точности вычислений.

## Решение

```php
<?php

class Calculator {
  // Защищенные свойства класса
  protected $num1;
  protected $num2;

  // Конструктор класса
  public function __construct($num1, $num2) {
    $this->num1 = $num1;
    $this->num2 = $num2;
  }

  // Методы класса
  public function add() {
    return $this->num1 + $this->num2;
  }

  public function subtract() {
    return $this->num1 - $this->num2;
  }

  public function multiply() {
    return $this->num1 * $this->num2;
  }

  public function divide() {
    return $this->num1 / $this->num2;
  }
}

class ScientificCalculator extends Calculator {
  // Защищенное свойство класса
  protected $precision;

  // Методы класса
  public function setPrecision($precision) {
    $this->precision = $precision;
  }

  public function getPrecision() {
    return $this->precision;
  }
}

// Создадим объекты классов
$calculator = new Calculator(10, 5);
$scientificCalculator = new ScientificCalculator(10, 5);

// Выведем результаты операций с помощью методов базового класса
echo "Сложение: " . $calculator->add() . "<br>";
echo "Вычитание: " . $calculator->subtract() . "<br>";
echo "Умножение: " . $calculator->multiply() . "<br>";
echo "Деление: " . $calculator->divide() . "<br>";

// Установим точность вычислений и выведем ее на экран с помощью методов класса-наследника
$scientificCalculator->setPrecision(2);
echo "Точность вычислений: " . $scientificCalculator->getPrecision();

```

## Задача 2

Создайте класс BankAccount, который будет иметь свойство balance с модификатором доступа private.\
Реализуйте методы deposit() и withdraw() для добавления и снятия денег со счета.\
Создайте класс SavingAccount, который будет наследоваться от BankAccount и будет иметь дополнительное свойство interestRate, определяющее процентную ставку.\
Реализуйте метод addInterest(), который будет добавлять проценты на счет в соответствии со ставкой.

## Решение

```php
<?php

class BankAccount {
    private $balance;

    public function __construct($balance) {
        $this->balance = $balance;
    }

    public function deposit($amount) {
        $this->balance += $amount;
    }

    public function withdraw($amount) {
        if ($amount > $this->balance) {
            throw new Exception("Недостаточно средств на счете");
        }
        $this->balance -= $amount;
    }

    public function getBalance() {
        return $this->balance;
    }
}

class SavingAccount extends BankAccount {
    private $interestRate;

    public function __construct($balance, $interestRate) {
        parent::__construct($balance);
        $this->interestRate = $interestRate;
    }

    public function addInterest() {
        $interest = $this->getBalance() * ($this->interestRate / 100);
        parent::deposit($interest);
    }
}

// Пример использования классов
$bankAccount = new BankAccount(1000);
$bankAccount->deposit(500);
$bankAccount->withdraw(200);

$savingAccount = new SavingAccount(1000, 5);
$savingAccount->addInterest();

echo "Баланс обычного счета: " . $bankAccount->getBalance() . "<br>";
echo "Баланс сберегательного счета: " . $savingAccount->getBalance();

```