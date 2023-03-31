# Домашнее задание

## Задача 1

Необходимо создать интерфейс PersonInterface с методом getInfo().\
Создать абстрактный класс Person, который будет реализовывать интерфейс PersonInterface и иметь свойства name и age.\
Создать класс Student, наследующий класс Person и реализующий метод getInfo().\
Класс Student должен иметь свойство major (специализация), которое устанавливается через конструктор.

## Решение

```php
interface PersonInterface {
  public function getInfo();
}

abstract class Person implements PersonInterface {
  // Свойства класса
  protected $name;
  protected $age;

  // Конструктор класса
  public function __construct($name, $age) {
    $this->name = $name;
    $this->age = $age;
  }

  // Методы класса
  public function getInfo() {
    return "Имя: " . $this->name . ", Возраст: " . $this->age;
  }
}

class Student extends Person {
  // Свойства класса
  private $major;

  // Конструктор класса
  public function __construct($name, $age, $major) {
    parent::__construct($name, $age);
    $this->major = $major;
  }

  // Методы класса
  public function getInfo() {
    return parent::getInfo() . ", Специализация: " . $this->major;
  }
}

// Создадим объект класса Student и выведем его информацию
$student = new Student("Иван", 20, "Программирование");
echo $student->getInfo();

```

## Задача 2

Реализуйте абстрактный класс Vehicle(транспортное средство) с защищенными свойствами brand и model, абстрактным методом getInfo() и общим методом startEngine().

Реализуйте интерфейс ElectricVehicle с методами setBatteryLife() и getBatteryLife().

Создайте класс Car, наследующийся от Vehicle и реализующий интерфейс ElectricVehicle. \
В классе Car реализуйте методы getInfo(), setBatteryLife() и getBatteryLife().

## Решение

```php
<?php
// Абстрактный класс Vehicle
abstract class Vehicle {
    protected $brand;
    protected $model;

    // Абстрактный метод getInfo()
    abstract public function getInfo();

    // Общий метод startEngine()
    public function startEngine() {
        echo "Запуск двигателя";
    }
}

// Интерфейс ElectricVehicle
interface ElectricVehicle {
    public function setBatteryLife($life);
    public function getBatteryLife();
}

// Класс Car, наследующийся от Vehicle и реализующий ElectricVehicle
class Car extends Vehicle implements ElectricVehicle {
    private $batteryLife;

    public function setBrand($brand) {
        $this->brand = $brand;
    }

    public function getBrand() {
        return $this->brand;
    }

    public function setModel($model) {
        $this->model = $model;
    }

    public function getModel() {
        return $this->model;
    }

    // Реализация метода getInfo()
    public function getInfo() {
        return "Марка: " . $this->getBrand() . ", Модель: " . $this->getModel();
    }

    // Реализация метода setBatteryLife()
    public function setBatteryLife($life) {
        $this->batteryLife = $life;
    }

    // Реализация метода getBatteryLife()
    public function getBatteryLife() {
        return $this->batteryLife;
    }
}

// Создаем объект класса Car
$electricCar = new Car();
$electricCar->setBrand("Tesla");
$electricCar->setModel("Model S");

// Устанавливаем значение заряда батареи и выводим его на экран
$electricCar->setBatteryLife(80);
echo "Заряд батареи: " . $electricCar->getBatteryLife() . "%<br>";

// Выводим информацию о машине
echo $electricCar->getInfo() . "<br>";

// Запускаем двигатель
$electricCar->startEngine();

```


## Задача 3

Необходимо создать класс Calculator, который будет иметь методы для основных математических операций (сложение, вычитание, умножение, деление). \
Класс должен реализовывать интерфейс MathOperations, который определяет методы для математических операций, и абстрактный класс BaseCalculator, который содержит общие методы для всех калькуляторов.

## Решение

```php
<?php

// Определяем интерфейс MathOperations
interface MathOperations {
  public function add($a, $b);
  public function subtract($a, $b);
  public function multiply($a, $b);
  public function divide($a, $b);
}

// Определяем абстрактный класс BaseCalculator
abstract class BaseCalculator {
  protected $lastResult;

  public function getLastResult() {
    return $this->lastResult;
  }
}

// Создаем класс Calculator, который реализует интерфейс MathOperations и наследует абстрактный класс BaseCalculator
class Calculator extends BaseCalculator implements MathOperations {
  public function add($a, $b) {
    $this->lastResult = $a + $b;
    return $this->lastResult;
  }

  public function subtract($a, $b) {
    $this->lastResult = $a - $b;
    return $this->lastResult;
  }

  public function multiply($a, $b) {
    $this->lastResult = $a * $b;
    return $this->lastResult;
  }

  public function divide($a, $b) {
    if ($b == 0) {
      throw new Exception('Division by zero');
    }
    $this->lastResult = $a / $b;
    return $this->lastResult;
  }
}

// Используем класс Calculator для выполнения математических операций
$calculator = new Calculator();
$calculator->add(5, 10);
echo "Результат сложения: " . $calculator->getLastResult() . "<br>";
$calculator->subtract(10, 5);
echo "Результат вычитания: " . $calculator->getLastResult() . "<br>";
$calculator->multiply(5, 10);
echo "Результат умножения: " . $calculator->getLastResult() . "<br>";
$calculator->divide(10, 2);
echo "Результат деления: " . $calculator->getLastResult() . "<br>";

```

## Задача 4

______________________________
void - это тип возвращаемого значения метода, который означает, что метод не возвращает никакого значения.

Если метод объявлен как void, это означает, что он не возвращает какое-либо значение в вызывающий код.

______________________________

Необходимо:

* Реализовать абстрактный класс BankAccount с защищенными свойствами баланса и имени владельца, конструктором и методами получения баланса и внесения денег на счет.\
* Определить абстрактный метод для снятия денег со счета.

* Создать два класса, наследующихся от абстрактного класса BankAccount - CheckingAccount и SavingsAccount.\
* Каждый класс должен иметь свои уникальные свойства и метод снятия денег.

* Создать интерфейс Transferable с методом для перевода денег с одного счета на другой.

* Создать класс Bank, в котором будут храниться объекты счетов. \
Реализовать методы для добавления нового счета, перевода денег со счета на счет и получения всех счетов.

* Создать два объекта счетов - CheckingAccount и SavingsAccount. Вывести информацию о счетах до и после перевода денег со сберегательного счета на текущий.

## Решение

```php
<?php
interface BankAccountInterface {
    public function getBalance(): float; // метод для получения баланса счета
    public function deposit(float $amount): void; // метод для пополнения счета
    public function withdraw(float $amount): void; // метод для снятия денег со счета
    public function transferTo(float $amount, BankAccount $account): void; // метод для перевода денег на другой счет
    public function getInfo(): string; //  метод для получения информации о счете, возвращает строку
}


// Абстрактный класс банковского счета
abstract class BankAccount implements BankAccountInterface {
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

    public function transferTo(float $amount, BankAccount $account): void {
        if ($this->balance - $amount >= 0) {
            $this->balance -= $amount;
            $account->deposit($amount);
        } else {
            throw new Exception("Недостаточно средств");
        }
    }

    /*
      BankAccount $account в методе transferTo класса CheckingAccount означает,
    что в качестве второго аргумента метода можно передать объект класса BankAccount или любого его наследника,
    потому что CheckingAccount является наследником BankAccount.
     */

    public function getInfo(): string {
        return "Счет {$this->ownerName}<br>" .
            "Баланс: {$this->balance} руб.";
    }
}

interface CheckingAccountInterface {
    // public function getBalance(): float;
    // public function deposit(float $amount): void;
    public function withdraw(float $amount): void; // Снятие со счета заданной суммы и комиссии за операцию
    // public function transferTo(float $amount, BankAccount $account): void;
    // public function getInfo(): string;
    public function getFee(): float;  // Получение текущей комиссии за операции со счетом
    public function setFee(float $fee): void; // Изменение текущей комиссии за операции со счетом
}


// Класс для расчетного (чекового) счета
class CheckingAccount extends BankAccount implements CheckingAccountInterface {
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
        return parent::getInfo() . "<br>" .
            "Комиссия: {$this->fee} руб.";
    }
}

interface SavingsAccountInterface {
    // public function getBalance(): float;
    //public function deposit(float $amount): void;
    public function withdraw(float $amount): void; // Снятие со счета заданной суммы
    public function addInterest(): void; // Добавление процентов на остаток счета в соответствии с текущей процентной ставкой
    public function getInfo(): string; // Получение информации о счете
}


// Класс для сберегательного счета
class SavingsAccount extends BankAccount implements SavingsAccountInterface {
    private float $interestRate;

    public function __construct(string $ownerName, float $balance = 0, float $interestRate = 0) {
        parent::__construct($ownerName, $balance);
        $this->interestRate = $interestRate;
    }

    public function withdraw(float $amount): void {
        if ($this->balance - $amount >= 0) {
            $this->balance -= $amount;
        } else {
            throw new Exception("Недостаточно средств");
        }
    }

        public function addInterest(): void {
        $this->balance += $this->balance * ($this->interestRate / 100);
    }

    public function getInfo(): string {
        return parent::getInfo() . "<br>" .
            "Процентная ставка: {$this->interestRate}%";
    }
}

/*
interface BankInterface {
    public function addAccount(BankAccount $account): void; // Добавление нового банковского счета в банк
    public function transfer(float $amount, BankAccount $account1, BankAccount $account2): void; // Перевод денежных средств между банковскими счетами
}


// Класс для банка
class Bank implements BankInterface{
    private array $accounts;

    public function __construct() {
        $this->accounts = [];
    }

    public function addAccount(BankAccount $account): void {
        $this->accounts[] = $account;
    }

    public function transfer(float $amount, BankAccount $account1, BankAccount $account2): void {
        $account1->transferTo($amount, $account2);
    }
}

// Класс Bank предоставляет функционал для управления счетами.

*/

// Создаем объекты счетов
$checking = new CheckingAccount("Иван Сергеев", 1000, 10);
$savings = new SavingsAccount("Анна Петрова", 5000, 5);

// Выводим информацию о счетах до операций
if ($checking instanceof CheckingAccount) {
    echo $checking->getInfo() . "<br>";
}

if ($savings instanceof SavingsAccount) {
    echo $savings->getInfo() . "<br>";
}

// Переводим деньги со сберегательного счета на текущий
$savings->transferTo(2000, $checking);

// Выводим информацию о счетах до операций
if ($checking instanceof CheckingAccount) {
    echo $checking->getInfo() . "<br>";
}

if ($savings instanceof SavingsAccount) {
    echo $savings->getInfo() . "<br>";
}

// Переводим деньги со сберегательного счета на текущий
$savings->transferTo(2000, $checking);

// Выводим информацию о счетах после операций
if ($checking instanceof CheckingAccount) {
    echo $checking->getInfo() . "<br>";
}

if ($savings instanceof SavingsAccount) {
    echo $savings->getInfo() . "<br>";
}



```
