# Абстрактные классы и интерфейсы в PHP

Абстрактные классы и интерфейсы - это механизмы, которые позволяют определить общие свойства и методы для группы классов.\
Абстрактные классы предоставляют базовый функционал для наследования, в то время как интерфейсы определяют общий контракт, который должен быть реализован классами.

# Абстрактный класс

Абстрактный класс - это класс, который содержит абстрактные методы. \
Абстрактный метод - это метод без тела, то есть без реализации.\
Абстрактный класс может содержать и обычные методы, которые уже имеют реализацию.

От абстрактного класса нельзя создать объект.\

Класс, наследующий абстрактный класс, должен реализовать все абстрактные методы, иначе он также должен быть объявлен как абстрактный класс.

Абстрактный класс - это класс, который не может быть создан напрямую, а может использоваться только как базовый класс для других классов.\
Он может содержать как абстрактные, так и конкретные методы. \
Абстрактный метод - это метод, который не имеет реализации в абстрактном классе, но должен быть реализован в классе-наследнике.

Создание абстрактного класса осуществляется с помощью ключевого слова abstract перед определением класса.\
Абстрактный метод также определяется с помощью ключевого слова abstract.

```php
<?php

abstract class Animal {
  // Свойства класса
  public $name;

  // Абстрактный метод
  abstract public function makeSound();

  // Конкретный метод
  public function run() {
    echo "Бежит";
  }
}

// Наследуемся от абстрактного класса
class Cat extends Animal {
  public function makeSound() {
    echo "Мяу";
  }
}

// Создаем объект класса Cat и вызываем методы
$cat = new Cat();
$cat->name = "Барсик";
$cat->makeSound(); // Выведет "Мяу"
$cat->run(); // Выведет "Бежит"

```

# Интерфейсы в PHP 

Интерфейс - это набор методов без реализации, которые должны быть реализованы в классе-наследнике.\
Он определяет только сигнатуры методов и не содержит каких-либо реализаций.

Создание интерфейса осуществляется с помощью ключевого слова interface перед определением интерфейса.

В PHP отсутствует возможность множественного наследования классов, поэтому для реализации функционала, объединяющего методы из различных классов, используются интерфейсы.\
Интерфейс в PHP это абстрактный класс, который определяет набор методов без их реализации. \
Класс, который реализует интерфейс, обязан реализовать все его методы. \
Таким образом, интерфейсы позволяют организовать взаимодействие между классами, не требуя наследования от нескольких классов, что повышает гибкость и поддерживаемость кода.

```php
<?php

interface Vehicle {
  // Vehicle - транспортное средство
  // Методы интерфейса
  public function start();
  public function stop();
}

// Наследуемся от интерфейса и реализуем его методы
class Car implements Vehicle {
  public function start() {
    echo "Автомобиль завелся";
  }

  public function stop() {
    echo "Автомобиль заглушен";
  }
}

// Создаем объект класса Car и вызываем методы
$car = new Car();
$car->start(); // Выведет "Автомобиль завелся"
$car->stop(); // Выведет "Автомобиль заглушен"

```

Для наследования от абстрактного класса используется ключевое слово extends. \
При этом, дочерний класс должен реализовать все абстрактные методы родительского класса, иначе он также должен быть объявлен как абстрактный.


```php
<?php

abstract class Vehicle {
    protected $model;

    public function __construct($model) {
        $this->model = $model;
    }

    abstract public function drive();
}

class Car extends Vehicle {
    public function drive() {
        echo $this->model . " едет по дороге.";
    }
}

$car = new Car("BMW");
$car->drive();

```

В этом примере класс Vehicle является абстрактным и содержит конструктор и абстрактный метод drive().\
Класс Car наследуется от класса Vehicle и реализует абстрактный метод drive().

классы могут реализовывать несколько интерфейсов.\
Для этого используется ключевое слово implements.\
При этом, класс должен реализовать все методы, определенные в интерфейсах.

```php
<?php

interface Animal {
    public function makeSound();
}

interface Bird {
    public function fly();
}

class Eagle implements Animal, Bird {
    public function makeSound() {
        echo "Звук орла!";
    }

    public function fly() {
        echo "Орел летит.";
    }
}

$eagle = new Eagle();
$eagle->makeSound();
$eagle->fly();

```

Интерфейсы Animal и Bird содержат методы makeSound() и fly(), соответственно. \
Класс Eagle реализует оба интерфейса и определяет свои реализации для методов makeSound() и fly().

Класс может наследоваться от одного класса и реализовывать один или несколько интерфейсов.

```php
abstract class Animal {
  protected $name;

  public function __construct($name) {
    $this->name = $name;
  }

  abstract public function makeSound();
}

interface Flyable {
  public function fly();
}

class Eagle extends Animal implements Flyable {
  public function makeSound() {
    echo "Звук орла!";
  }

  public function fly() {
    echo "Орел летит.";
  }
}

$eagle = new Eagle("Орел");
$eagle->makeSound();
$eagle->fly();

```

_________________________________________
_________________________________________
_________________________________________

Мы имеем абстрактный класс Animal с двумя свойствами и двумя абстрактными методами, которые должны быть реализованы в дочерних классах:

```php
abstract class Animal {
  protected $name;
  protected $age;

  public function __construct($name, $age) {
    $this->name = $name;
    $this->age = $age;
  }

  abstract public function makeSound();
  abstract public function move();
}

```

Теперь мы создадим классы Cat и Dog, которые будут наследоваться от класса Animal и реализовывать его абстрактные методы:

```php
class Cat extends Animal {
  public function makeSound() {
    echo "Мяу!";
  }

  public function move() {
    echo "Кошка бежит";
  }
}

class Dog extends Animal {
  public function makeSound() {
    echo "Гав!";
  }

  public function move() {
    echo "Собака бежит";
  }
}

```

Мы также можем создать интерфейс Mammal(млекопетающее) с одним методом, который должен быть реализован в классах, которые реализуют этот интерфейс:

```php
interface Mammal {
  public function feed();
}

```

Теперь мы создадим классы Cat и Dog, которые будут наследоваться от класса Animal и реализовывать интерфейс Mammal:

```php
class Cat extends Animal implements Mammal {
  public function makeSound() {
    echo "Мяу!";
  }

  public function move() {
    echo "Кошка бежит";
  }

  public function feed() {
    echo "Кормлю кота";
  }
}

class Dog extends Animal implements Mammal {
  public function makeSound() {
    echo "Гав!";
  }

  public function move() {
    echo "Собака бежит";
  }

  public function feed() {
    echo "Кормлю собаку";
  }
}

```

Теперь мы можем создать объекты классов Cat и Dog и вызвать их методы:

```php
$cat = new Cat("Мурзик", 3);
$cat->makeSound(); // Выводит "Мяу!"
$cat->move(); // Выводит "Кошка бежит"
$cat->feed(); // Выводит "Кормлю кота"

$dog = new Dog("Барсик", 5);
$dog->makeSound(); // Выводит "Гав!"
$dog->move(); // Выводит "Собака бежит"
$dog->feed(); // Выводит "Кормлю собаку"

```

Обратите внимание, что классы Cat и Dog унаследовали свойства и методы класса Animal и реализовали абстрактные методы, а также реализовали метод feed() из интерфейса Mammal.

______________________________
______________________________
______________________________

# Домашнее задание

## Задача 1

Необходимо создать интерфейс PersonInterface с методом getInfo().\
Создать абстрактный класс Person, который будет реализовывать интерфейс PersonInterface и иметь свойства name и age.\
Создать класс Student, наследующий класс Person и реализующий метод getInfo().\
Класс Student должен иметь свойство major (специализация), которое устанавливается через конструктор.

## Задача 2

Реализуйте абстрактный класс Vehicle(транспортное средство) с защищенными свойствами brand и model, абстрактным методом getInfo() и общим методом startEngine().

Реализуйте интерфейс ElectricVehicle с методами setBatteryLife() и getBatteryLife().

Создайте класс Car, наследующийся от Vehicle и реализующий интерфейс ElectricVehicle. \
В классе Car реализуйте методы getInfo(), setBatteryLife() и getBatteryLife().

## Задача 3

Необходимо создать класс Calculator, который будет иметь методы для основных математических операций (сложение, вычитание, умножение, деление). \
Класс должен реализовывать интерфейс MathOperations, который определяет методы для математических операций, и абстрактный класс BaseCalculator, который содержит общие методы для всех калькуляторов.

## Задача 4

## Задача 4

Необходимо:

* Реализовать абстрактный класс BankAccount с защищенными свойствами баланса и имени владельца, конструктором и методами получения баланса и внесения денег на счет.\
* Определить абстрактный метод для снятия денег со счета.

* Создать два класса, наследующихся от абстрактного класса BankAccount - CheckingAccount и SavingsAccount.\
* Каждый класс должен иметь свои уникальные свойства и метод снятия денег.

* Создать интерфейс Transferable с методом для перевода денег с одного счета на другой.

* Создать класс Bank, в котором будут храниться объекты счетов. \
  Реализовать методы для добавления нового счета, перевода денег со счета на счет и получения всех счетов.

* Создать два объекта счетов - CheckingAccount и SavingsAccount. Вывести информацию о счетах до и после перевода денег со сберегательного счета на текущий.
