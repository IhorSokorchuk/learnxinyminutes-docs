---
language: PHP
contributors:
    - ["Malcolm Fell", "http://emarref.net/"]
    - ["Trismegiste", "https://github.com/Trismegiste"]
    - ["Ihor Sokorchuk", "https://github.com/IhorSokorchuk/learnxinyminutes-docs/tree/master/uk-ua"]
filename: learnphp-ua.php
---

This document describes PHP 5+.
Цей документ описує PHP 5+.

```php
<?php // PHP code must be enclosed with <?php tags
      // Код PHP має міститися в тегах <?php

// If your php file only contains PHP code, it is best practice
// to omit the php closing tag to prevent accidental output.
// Якщо ваш php-файл містить лише PHP-код, то найкраще буде
// не вказувати тег закриття php, щоб запобігти випадковому виведенню.

// Two forward slashes start a one-line comment.
// Дві косі риски починають однорядковий коментар.

# So will a hash (aka pound symbol) but // is more common
# Те ж саме вказує символ #, але // є більш поширеним способом

/*
     Surrounding text in slash-asterisk and asterisk-slash
     makes it a multi-line comment.111
     Текст, який охоплений двознаками /* та */,
     робить цей текст багаторядковим коментарем.
*/

// Use "echo" or "print" to print output
// Використовуйте "echo" або "print", щоб надрукувати вивід
print('Hello '); // Prints "Hello " with no line break
                 // Видруковується "Hello " без розриву рядка

// () are optional for print and echo
// () є необов’язковими для print та echo
echo "World\n"; // Prints "World" with a line break
                // Видруковується "World" із розривом рядка
// (all statements must end with a semicolon)
// (усі оператори мають закінчуватися крапкою з комою)

// Anything outside <?php tags is echoed automatically
// Все, що знаходиться за межами тегів <?php, відтворюється автоматично
?>
Hello World Again!
<?php
// That is because historically PHP started as a Template engine
// Це тому, що історично PHP починався як механізм шаблонів


/************************************
 * Types & Variables
 * Типи та змінні
 */

// Variables begin with the $ symbol.
// A valid variable name starts with a letter or an underscore,
// followed by any number of letters, numbers, or underscores.
// Змінні починаються з символа $.
// Правильна назва змінної починається з літери або підкреслення,
// за яким слід будь-яка кількість літер, цифр або підкреслень.

// You don't have to (and cannot) declare variables.
// Once you assign a value, PHP will create the variable with the right type.
// Вам не потрібно (і не можна) оголошувати змінні.
// Коли ви присвоїте значення, PHP створить змінну з правильним типом.

// Boolean values are case-insensitive
// Логічні значення регістру не враховуються
$boolean = true;  // or TRUE or True
                  // або TRUE або True
$boolean = FALSE; // or false or False
                  // або false або False

// Integers
// Цілі числа
$int1 = 12;   // => 12
              // => 12
$int2 = -12;  // => -12
              // => -12
$int3 = 012;  // => 10 (a leading 0 denotes an octal number)
              // => 10 (початковий 0 позначає вісімкове число)
$int4 = 0x0F; // => 15 (a leading 0x denotes a hex literal)
              // => 15 (початковий 0x позначає шістнадцятковий літерал)
// Binary integer literals are available since PHP 5.4.0.
// Двійкові цілі літерали доступні починаючи з PHP 5.4.0.
$int5 = 0b11111111; // 255 (a leading 0b denotes a binary number)
                    // 255 (0b на початку позначає двійкове число)

// Floats (aka doubles)
// Із рухомою десятковою крапкою (також подвійні)
$float = 1.234;
$float = 1.2e3;
$float = 7E-10;

// Delete variable
// Видалити змінну
unset($int1);

// Arithmetic
// Аритметика
$sum        = 1 + 1; // 2
                     // 2
$difference = 2 - 1; // 1
                     // 1
$product    = 2 * 2; // 4
                     // 4
$quotient   = 2 / 1; // 2
                     // 2

// Shorthand arithmetic
// Скорочена аритметики
$number = 0;
$number += 1;      // Increment $number by 1
                   // Збільшити $number на 1
echo $number++;    // Prints 1 (increments after evaluation)
                   // Друкує 1 (збільшується після оцінки)
echo ++$number;    // Prints 3 (increments before evaluation)
                   // Друкує 3 (збільшується перед оцінкою)
$number /= $float; // Divide and assign the quotient to $number
                   // Ділимо і присвоюємо частку $number

// Strings should be enclosed in single quotes;
// Рядки повинні бути взяті в одинарні лапки;
$sgl_quotes = '$String'; // => '$String'
                         // => '$String'

// Avoid using double quotes except to embed other variables
// Уникайте використання подвійних лапок, за винятком вставлення інших змінних
$dbl_quotes = "This is a $sgl_quotes."; // => 'This is a $String.'
                                        // => 'Це $String.'

// Special characters are only escaped in double quotes
// Спеціальні символи екрануються лише в подвійних лапках
$escaped   = "This contains a \t tab character.";
$unescaped = 'This just contains a slash and a t: \t';

// Enclose a variable in curly braces if needed
// За потреби візьміть змінну у фігурні дужки
$apples = "I have {$number} apples to eat.";
$oranges = "I have ${number} oranges to eat.";
$money = "I have $${number} in the bank.";

// Since PHP 5.3, nowdocs can be used for uninterpolated multi-liners
// Починаючи з PHP 5.3, nowdocs можна використовувати для неінтерпольованих багаторядкових даних
$nowdoc = <<<'END'
Multi line
string
END;

// Heredocs will do string interpolation
// Heredocs виконає інтерполяцію (підстановку значень) рядка
$heredoc = <<<END
Multi line
$sgl_quotes
END;

// String concatenation is done with .
// Конкатенація (обʼєднання) рядків виконується за допомогою .
echo 'This string ' . 'is concatenated';

// Strings can be passed in as parameters to echo
// Рядки можна передати команді echo як параметри
echo 'Multiple', 'Parameters', 'Valid';  // Returns 'MultipleParametersValid'
                                         // Повертає 'MultipleParametersValid'


/********************************
 * Constants
 * Константи
 */

// A constant is defined by using define()
// and can never be changed during runtime!
// Константа визначається за допомогою define()
// і ніколи не може бути змінена під час виконання!

// a valid constant name starts with a letter or underscore,
// followed by any number of letters, numbers, or underscores.
// правильне ім'я константи починається з літери або підкреслення,
// за яким йде будь-яка кількість літер, цифр або підкреслень.
define("FOO", "something");

// access to a constant is possible by calling the chosen name without a $
// доступ до константи можливий шляхом виклику вибраного імені без $
echo FOO; // Returns 'something'
          // Повертає 'something' (щось)
echo 'This outputs ' . FOO;  // Returns 'This outputs something'
                             // Повертає 'This outputs something'



/********************************
 * Arrays
 * Масиви
 */

// All arrays in PHP are associative arrays (hashmaps in some languages)
// Усі масиви в PHP є асоціативними масивами (геш-карти у деяких мовах)

// Works with all PHP versions
// Працює з усіма версіями PHP
$associative = array('One' => 1, 'Two' => 2, 'Three' => 3);

// PHP 5.4 introduced a new syntax
// У PHP 5.4 введено новий синтаксис
$associative = ['One' => 1, 'Two' => 2, 'Three' => 3];

echo $associative['One']; // prints 1
                          // друкує 1

// Add an element to an associative array
// Додати елемент до асоціативного масиву
$associative['Four'] = 4;

// List literals implicitly assign integer keys
// Літерали списку неявно призначають ключі з цілочисельними значеннями
$array = ['One', 'Two', 'Three'];
echo $array[0]; // => "One"
                // => "Один"

// Add an element to the end of an array
// Додати елемент у кінець масиву
$array[] = 'Four';
// or
// або
array_push($array, 'Five');

// Remove element from array
// Видалення елемента з масиву
unset($array[3]);

/********************************
 * Output
 * Виведення
 */

echo('Hello World!');
// Prints Hello World! to stdout.
// Stdout is the web page if running in a browser.
// Друкує Hello World! до стандартного виводу.
// Стандартний вихід — це веб-сторінка, якщо вона працює у браузері.

print('Hello World!'); // The same as echo
                       // Те саме, що echo

// echo and print are language constructs too, so you can drop the parentheses
// echo та print також є мовними конструкціями, тому ви можете не вказувати дужки
echo 'Hello World!';
print 'Hello World!';

$paragraph = 'paragraph';

echo 100;        // Echo scalar variables directly
                 // Виводить вказані скалярні значення
echo $paragraph; // or variables
                 // або значення змінних

// If short open tags are configured, or your PHP version is
// 5.4.0 or greater, you can use the short echo syntax
// Якщо налаштовано скорочені відкриті теги або ваша версія PHP
// 5.4.0 або вище, ви можете використовувати короткий синтаксис для виведення
?>
<p><?= $paragraph ?></p>
<?php

$x = 1;
$y = 2;
$x = $y; // $x now contains the same value as $y
         // $x тепер містить те саме значення, що й $y
$z = &$y;
// $z now contains a reference to $y. Changing the value of
// $z will change the value of $y also, and vice-versa.
// $x will remain unchanged as the original value of $y
// $z тепер містить посилання на $y. Зміна значення
// $z також змінить значення $y і навпаки.
// $x залишиться незмінним як вихідне значення $y

echo $x; // => 2
         // => 2
echo $z; // => 2
         // => 2
$y = 0;
echo $x; // => 2
         // => 2
echo $z; // => 0
         // => 0

// Dumps type and value of variable to stdout
// Виводить тип і значення змінної на стандартний вивід
var_dump($z); // prints int(0)
              // друкує int(0)

// Prints variable to stdout in human-readable format
// Друкує змінну в stdout у зручному для читання форматі
print_r($array); // prints: Array ( [0] => One [1] => Two [2] => Three )
                 // друкує: масив ( [0] => один [1] => два [2] => три )

/********************************
 * Logic
 * Логіка
 */
$a = 0;
$b = '0';
$c = '1';
$d = '1';

// assert throws a warning if its argument is not true
// assert видає попередження, якщо його аргумент неправильний

// These comparisons will always be true, even if the types aren't the same.
// Ці порівняння завжди будуть правильними, навіть якщо типи не однакові.
assert($a == $b); // equality
                  // рівність
assert($c != $a); // inequality
                  // нерівність
assert($c <> $a); // alternative inequality
                  // альтернативна нерівність
assert($a < $c);
assert($c > $b);
assert($a <= $b);
assert($c >= $d);

// The following will only be true if the values match and are the same type.
// Наступне буде істинним, лише якщо значення збігаються та мають той самий тип.
assert($c === $d);
assert($a !== $d);
assert(1 === '1');
assert(1 !== '1');

// 'Spaceship' operator (since PHP 7)
// Returns 0 if values on either side are equal
// Returns 1 if value on the left is greater
// Returns -1 if the value on the right is greater
// Оператор 'Spaceship' (починаючи з PHP 7):
// повертає 0, якщо значення з обох боків рівні;
// повертає 1, якщо значення зліва більше;
// повертає -1, якщо значення праворуч більше.

$a = 100;
$b = 1000;

echo $a <=> $a; // 0 since they are equal
                // 0, оскільки вони рівні
echo $a <=> $b; // -1 since $a < $b
                // -1, оскільки $a < $b
echo $b <=> $a; // 1 since $b > $a
                // 1, оскільки $b > $a

// Variables can be converted between types, depending on their usage.
// Змінні можна перетворювати між типами залежно від їх використання.

$integer = 1;
echo $integer + $integer; // => 2
                          // => 2

$string = '1';
echo $string + $string; // => 2 (strings are coerced to integers)
                        // => 2 (рядки приведені до цілих чисел)

$string = 'one';
echo $string + $string; // => 0
                        // => 0
// Outputs 0 because the + operator cannot cast the string 'one' to a number
// Виводить 0, оскільки оператор + не може перетворити рядок «один» на число

// Type casting can be used to treat a variable as another type
// Приведення типів може використовуватися для обробки змінної як іншого типу

$boolean = (boolean) 1; // => true
                        // => правда

$zero = 0;
$boolean = (boolean) $zero; // => false
                            // => фальш

// There are also dedicated functions for casting most types
// Існують також спеціальні функції для приведення більшості типів
$integer = 5;
$string = strval($integer);

$var = null; // Null value
             // Нульове значення


/********************************
 * Control Structures
 * Оператори управління
 */

if (true) {
    print 'I get printed';
}

if (false) {
    print 'I don\'t';
} else {
    print 'I get printed';
}

if (false) {
    print 'Does not get printed';
} elseif (true) {
    print 'Does';
}

// ternary operator
// тернарний оператор
print (false ? 'Does not get printed' : 'Does');

// ternary shortcut operator since PHP 5.3
// equivalent of "$x ? $x : 'Does'"
// скорочений тернарний оператор, починаючи з PHP 5.3
// еквівалент "$x ? $x : 'Does'"
$x = false;
print($x ?: 'Does');

// null coalesce operator since php 7
// нульовий оператор об’єднання з php 7
$a = null;
$b = 'Does print';
echo $a ?? 'a is not set'; // prints 'a is not set'
                           // друкує 'a is not set' (не встановлено)
echo $b ?? 'b is not set'; // prints 'Does print'
                           // друкує 'Does print' (Друкує)


$x = 0;
if ($x === '0') {
    print 'Does not print';
} elseif ($x == '1') {
    print 'Does not print';
} else {
    print 'Does print';
}



// This alternative syntax is useful for templates:
// Цей альтернативний синтаксис корисний для шаблонів:
?>

<?php if ($x): ?>
This is displayed if the test is truthy.
<?php else: ?>
This is displayed otherwise.
<?php endif; ?>

<?php

// Use switch to save some logic.
// Використовуйте перемикач switch, щоб зберегти деяку логіку.
switch ($x) {
    case '0':
        print 'Switch does type coercion';
        break; // You must include a break, or you will fall through
               // to cases 'two' and 'three'
               // Ви повинні вказувати break (перервати), інакше ви перейдете
               // до випадків "два" і "три"
    case 'two':
    case 'three':
        // Do something if $variable is either 'two' or 'three'
        // Зробіть щось, якщо $variable дорівнює «два» або «три»
        break;
    default:
        // Do something by default
        // Робити щось за замовчуванням
}

// While, do...while and for loops are probably familiar
// Цикли while, do...while і for, мабуть, знайомі
$i = 0;
while ($i < 5) {
    echo $i++;
} // Prints "01234"
  // Друкує "01234"

echo "\n";

$i = 0;
do {
    echo $i++;
} while ($i < 5); // Prints "01234"
                  // Друкує "01234"

echo "\n";

for ($x = 0; $x < 10; $x++) {
    echo $x;
} // Prints "0123456789"
  // Друкує "0123456789"

echo "\n";

$wheels = ['bicycle' => 2, 'car' => 4];

// Foreach loops can iterate over arrays
// Цикли Foreach можуть перебирати масиви
foreach ($wheels as $wheel_count) {
    echo $wheel_count;
} // Prints "24"
  // Друкує "24"

echo "\n";

// You can iterate over the keys as well as the values
// Ви можете перебирати як ключі, так і значення
foreach ($wheels as $vehicle => $wheel_count) {
    echo "A $vehicle has $wheel_count wheels";
}

echo "\n";

$i = 0;
while ($i < 5) {
    if ($i === 3) {
        break; // Exit out of the while loop
               // Вихід із циклу while
    }
    echo $i++;
} // Prints "012"
  // Друкує "012"

for ($i = 0; $i < 5; $i++) {
    if ($i === 3) {
        continue; // Skip this iteration of the loop
                  // Пропустити цю ітерацію циклу
    }
    echo $i;
} // Prints "0124"
  // Друкує "0124"


/********************************
 * Functions
 * Функції
 */

// Define a function with "function":
// Визначити функцію за допомогою "function":
function my_function () {
    return 'Hello';
}

echo my_function(); // => "Hello"
                    // => "Hello" (Привіт)

// A valid function name starts with a letter or underscore, followed by any
// number of letters, numbers, or underscores.
// Правильне ім’я функції починається з літери або підкреслення, за якими йде будь-яка
// кількість літер, цифр або символів підкреслення.

function add ($x, $y = 1) { // $y is optional and defaults to 1
                            // $y є необов’язковим і за умовчанням дорівнює 1
    $result = $x + $y;
    return $result;
}

echo add(4); // => 5
             // => 5
echo add(4, 2); // => 6
                // => 6

// $result is not accessible outside the function
// print $result; // Gives a warning.
// $result недоступний поза функцією
// вивести $result; // Виводить попередження.

// Since PHP 5.3 you can declare anonymous functions;
// Починаючи з PHP 5.3, ви можете оголошувати анонімні функції;
$inc = function ($x) {
    return $x + 1;
};

echo $inc(2); // => 3
              // => 3

function foo ($x, $y, $z) {
    echo "$x - $y - $z";
}

// Functions can return functions
// Функції можуть повертати функції
function bar ($x, $y) {
    // Use 'use' to bring in outside variables
    // Використовуйте 'use' для введення зовнішніх змінних
    return function ($z) use ($x, $y) {
        foo($x, $y, $z);
    };
}

$bar = bar('A', 'B');
$bar('C'); // Prints "A - B - C"
           // Друкує "A - B - C"

// You can call named functions using strings
// Ви можете викликати іменовані функції за допомогою рядків
$function_name = 'add';
echo $function_name(1, 2); // => 3
                           // => 3
// Useful for programatically determining which function to run.
// Or, use call_user_func(callable $callback [, $parameter [, ... ]]);
// Корисно для програмного визначення, яку функцію запускати.
// Або використовуйте call_user_func(callable $callback [, $parameter [, ... ]]);


// You can get all the parameters passed to a function
// Ви можете отримати всі параметри, передані функції
function parameters() {
    $numargs = func_num_args();
    if ($numargs > 0) {
        echo func_get_arg(0) . ' | ';
    }
    $args_array = func_get_args();
    foreach ($args_array as $key => $arg) {
        echo $key . ' - ' . $arg . ' | ';
    }
}

parameters('Hello', 'World'); // Hello | 0 - Hello | 1 - World |
                              // Привіт | 0 - Привіт | 1 - Світ |

// Since PHP 5.6 you can get a variable number of arguments
// Починаючи з PHP 5.6, ви можете отримувати змінну кількість аргументів
function variable($word, ...$list) {
	echo $word . " || ";
	foreach ($list as $item) {
		echo $item . ' | ';
	}
}

variable("Separate", "Hello", "World"); // Separate || Hello | World |
                                        // Окремий || Привіт | Світ |

/********************************
 * Includes
 * Включення
 */

<?php
// PHP within included files must also begin with a PHP open tag.
// PHP у включених файлах також має починатися з тегу відкриття PHP.

include 'my-file.php';
// The code in my-file.php is now available in the current scope.
// If the file cannot be included (e.g. file not found), a warning is emitted.
// Код із my-file.php тепер доступний у поточному просторі.
// Якщо файл не можна включити (наприклад, файл не знайдено), видається попередження.

include_once 'my-file.php';
// If the code in my-file.php has been included elsewhere, it will
// not be included again. This prevents multiple class declaration errors
// Якщо код із my-file.php було вже включено раніше, він не буде
// включатися надалі. Це запобігає помилкам багаторазового оголошення класу

require 'my-file.php';
require_once 'my-file.php';
// Same as include(), except require() will cause a fatal error if the
// file cannot be included.
// Те ж саме, що й include(), за винятком того, що require() спричинить фатальну помилку,
// якщо файл не можна буде включити.

// Contents of my-include.php:
// Вміст my-include.php:
<?php

return 'Anything you like.';
// End file
// Кінець файла

// Includes and requires may also return a value.
// Прості включення та обовʼязкові включення можуть також повертати значення.
$value = include 'my-include.php';

// Files are included based on the file path given or, if none is given,
// the include_path configuration directive. If the file isn't found in
// the include_path, include will finally check in the calling script's
// own directory and the current working directory before failing.
// Файли включаються на основі вказаного шляху до файлу або, якщо не вказано,
// директиви конфігурації include_path. Якщо файл не знайдено в
// include_path, include далі перевірятиме у викликаному скрипті
// власний каталог і поточний робочий каталог аж до збою.
/* */

/********************************
 * Classes
 * Класи
 */

// Classes are defined with the class keyword
// Класи визначаються за допомогою ключового слова class

class MyClass
{
    const MY_CONST      = 'value'; // A constant
                                   // Константа

    static $staticVar   = 'static';

    // Static variables and their visibility
    // Статичні змінні та їх видимість
    public static $publicStaticVar = 'publicStatic';
    // Accessible within the class only
    // Доступно лише в межах класу
    private static $privateStaticVar = 'privateStatic';
    // Accessible from the class and subclasses
    // Доступно з класу та підкласів
    protected static $protectedStaticVar = 'protectedStatic';

    // Properties must declare their visibility
    // Властивості повинні оголошувати свою видимість
    public $property    = 'public';
    public $instanceProp;
    protected $prot = 'protected'; // Accessible from the class and subclasses
                                   // Доступно з класу та підкласів
    private $priv   = 'private';   // Accessible within the class only
                                   // Доступно лише в межах класу

    // Create a constructor with __construct
    // Створення конструктора за допомогою __construct
    public function __construct($instanceProp)
    {
        // Access instance variables with $this
        // Доступ до змінних екземпляра за допомогою $this
        $this->instanceProp = $instanceProp;
    }

    // Methods are declared as functions inside a class
    // Методи оголошуються як функції всередині класу
    public function myMethod()
    {
        print 'MyClass';
    }

    // final keyword would make a function unoverridable
    // ключове слово final зробить функцію незмінною
    final function youCannotOverrideMe()
    {
    }

    // Magic Methods
    // Магічні методи

    // what to do if Object is treated as a String
    // що робити, якщо Object розглядається як рядок
    public function __toString()
    {
        return $property;
    }

    // opposite to __construct()
    // called when object is no longer referenced
    // на противагу до __construct()
    // викликається, коли більше немає посилання на об’єкт
    public function __destruct()
    {
        print "Destroying";
    }

/*
 * Declaring class properties or methods as static makes them accessible without
 * needing an instantiation of the class. A property declared as static can not
 * be accessed with an instantiated class object (though a static method can).
 * Оголошення властивостей або методів класу як статичних робить їх доступними без
 * потреби в екземплярі класу. До властивості, яку оголошено як статичну, не можна
 * отримати доступ за допомогою створеного об’єкта класу (хоча статичний метод може).
 */

    public static function myStaticMethod()
    {
        print 'I am static';
    }
}

// Class constants can always be accessed statically
// До констант класу завжди можна отримати статичний доступ
echo MyClass::MY_CONST;    // Outputs 'value';
                           // Виводить 'value';

echo MyClass::$staticVar;  // Outputs 'static';
                           // Виводить 'static';
MyClass::myStaticMethod(); // Outputs 'I am static';
                           // Виводить 'I am static';

// Instantiate classes using new
// Створення екземплярів класів за допомогою new
$my_class = new MyClass('An instance property');
// The parentheses are optional if not passing in an argument.
// Дужки необов’язкові, якщо не передають аргумент.

// Access class members using ->
// Доступ до членів класу за допомогою ->
echo $my_class->property;     // => "public"
                              // => "публічний"
echo $my_class->instanceProp; // => "An instance property"
                              // => "Властивість екземпляра"
$my_class->myMethod();        // => "MyClass"
                              // => "MyClass"

// Nullsafe operators since PHP 8
// You can use this when you're unsure if the abstraction of $my_class contains has a property/method
// it can be used in conjunction with the nullish coalesce operator to ensure proper value
// Nullsafe оператори починаючи з PHP 8
// Ви можете використовувати це, якщо не впевнені, що абстракція $my_class містить властивість/метод
// це можна використовувати в поєднанні з нульовим оператором об’єднання для забезпечення правильного значення
echo $my_class->invalid_property // An error is thrown
                                 // Видається помилка
echo $my_class?->invalid_property // => NULL
                                  // => NULL
echo $my_class?->invalid_property ?? "public" // => "public"
                                              // => "public" (публічний)

// Extend classes using "extends"
// Розширюємо (спадкуємо) класи за допомогою "extends"
class MyOtherClass extends MyClass
{
    function printProtectedProperty()
    {
        echo $this->prot;
    }

    // Override a method
    // Перевизначити метод
    function myMethod()
    {
        parent::myMethod();
        print ' > MyOtherClass';
    }
}

$my_other_class = new MyOtherClass('Instance prop');
$my_other_class->printProtectedProperty(); // => Prints "protected"
                                           // => Друкує "protected" (захищений)
$my_other_class->myMethod();               // Prints "MyClass > MyOtherClass"
                                           // Друкує "MyClass > MyOtherClass"

final class YouCannotExtendMe
{
}

// You can use "magic methods" to create getters and setters
// Ви можете використовувати «магічні методи» для створення getters (ґетерів) та setters (сетерів)
class MyMapClass
{
    private $property;

    public function __get($key)
    {
        return $this->$key;
    }

    public function __set($key, $value)
    {
        $this->$key = $value;
    }
}

$x = new MyMapClass();
echo $x->property; // Will use the __get() method
                   // Буде використано метод __get().
$x->property = 'Something'; // Will use the __set() method
                            // Буде використано метод __set().

// Classes can be abstract (using the abstract keyword) or
// implement interfaces (using the implements keyword).
// An interface is declared with the interface keyword.
// Класи можуть бути абстрактними (за допомогою ключового слова abstract) або
// реалізувати інтерфейси (за допомогою ключового слова implements).
// Інтерфейс оголошується за допомогою ключового слова interface.

interface InterfaceOne
{
    public function doSomething();
}

interface InterfaceTwo
{
    public function doSomethingElse();
}

// interfaces can be extended
// інтерфейси можна розширити
interface InterfaceThree extends InterfaceTwo
{
    public function doAnotherContract();
}

abstract class MyAbstractClass implements InterfaceOne
{
    public $x = 'doSomething';
}

class MyConcreteClass extends MyAbstractClass implements InterfaceTwo
{
    public function doSomething()
    {
        echo $x;
    }

    public function doSomethingElse()
    {
        echo 'doSomethingElse';
    }
}


// Classes can implement more than one interface
// Класи можуть реалізувати більше одного інтерфейсу
class SomeOtherClass implements InterfaceOne, InterfaceTwo
{
    public function doSomething()
    {
        echo 'doSomething';
    }

    public function doSomethingElse()
    {
        echo 'doSomethingElse';
    }
}


/********************************
 * Traits
 * Трейти
 */

// Traits are available from PHP 5.4.0 and are declared using "trait"
// Трейти доступні починаючи з PHP 5.4.0 і оголошуються за допомогою "trait"

trait MyTrait
{
    public function myTraitMethod()
    {
        print 'I have MyTrait';
    }
}

class MyTraitfulClass
{
    use MyTrait;
}

$cls = new MyTraitfulClass();
$cls->myTraitMethod(); // Prints "I have MyTrait"
                       // Видруковується "I have MyTrait"


/********************************
 * Namespaces
 * Простори імен
 */

// This section is separate, because a namespace declaration
// must be the first statement in a file. Let's pretend that is not the case
// Цей розділ є окремим, оскільки це оголошення простору імен
// має бути першим оператором у файлі. Уявимо, що це не так

<?php

// By default, classes exist in the global namespace, and can
// be explicitly called with a backslash.
// За замовчуванням класи існують у глобальному просторі імен і можуть
// явно викликається зі зворотною косою рискою.

$cls = new \MyClass();



// Set the namespace for a file
// Встановити простір імен для файлу
namespace My\Namespace;

class MyClass
{
}

// (from another file)
// (з іншого файлу)
$cls = new My\Namespace\MyClass;

//Or from within another namespace.
//Або з іншого простору імен.
namespace My\Other\Namespace;

use My\Namespace\MyClass;

$cls = new MyClass();

// Or you can alias the namespace;
// Або ви можете створити псевдонім простору імен;

namespace My\Other\Namespace;

use My\Namespace as SomeOtherNamespace;

$cls = new SomeOtherNamespace\MyClass();


/**********************
* Late Static Binding
* Пізнє статичне зв'язування
*
*/

class ParentClass
{
    public static function who()
    {
        echo "I'm a " . __CLASS__ . "\n";
    }

    public static function test()
    {
        // self references the class the method is defined within
        // самостійно посилається на клас, у якому визначено метод
        self::who();
        // static references the class the method was invoked on
        // статичні посилання на клас, у якому було викликано метод
        static::who();
    }
}

ParentClass::test();
/*
I'm a ParentClass
I'm a ParentClass
*/

class ChildClass extends ParentClass
{
    public static function who()
    {
        echo "But I'm " . __CLASS__ . "\n";
    }
}

ChildClass::test();
/*
I'm a ParentClass
But I'm ChildClass
*/

/**********************
*  Magic constants
*  Магічні константи
*
*/

// Get current class name. Must be used inside a class declaration.
// Отримати назву поточного класу. Має використовуватися в декларації класу.
echo "Current class name is " . __CLASS__;

// Get full path directory of a file
// Отримати повний шлях до каталогу файлу
echo "Current directory is " . __DIR__;

    // Typical usage
    // Типове використання
    require __DIR__ . '/vendor/autoload.php';

// Get full path of a file
// Отримати повний шлях до файлу
echo "Current file path is " . __FILE__;

// Get current function name
// Отримати назву поточної функції
echo "Current function name is " . __FUNCTION__;

// Get current line number
// Отримати поточний номер рядка
echo "Current line number is " . __LINE__;

// Get the name of the current method. Only returns a value when used inside a trait or object declaration.
// Отримання назви поточного методу. Повертає значення лише тоді, коли використовується в декларації ознаки чи об’єкта.
echo "Current method is " . __METHOD__;

// Get the name of the current namespace
// Отримати назву поточного простору імен
echo "Current namespace is " . __NAMESPACE__;

// Get the name of the current trait. Only returns a value when used inside a trait or object declaration.
// Отримати назву поточного трейту. Повертає значення лише тоді, коли використовується всередині означення трейту або об’єкту.
echo "Current trait is " . __TRAIT__;

/**********************
*  Error Handling
*  Обробка помилок
*
*/

// Simple error handling can be done with try catch block
// Просту обробку помилок можна виконати за допомогою блоку try catch

try {
    // Do something
    // Зроби щось
} catch (Exception $e) {
    // Handle exception
    // Обробляти виняток
}

// When using try catch blocks in a namespaced environment it is important to
// escape to the global namespace, because Exceptions are classes, and the
// Exception class exists in the global namespace. This can be done using a
// leading backslash to catch the Exception.
// При використанні блоків try catch у середовищі простору імен важливо
// перейти до глобального простору імен, тому що винятками є класи та
// У глобальному просторі імен існує клас винятків. Це можна зробити за допомогою a
// початкова зворотна коса риска для виявлення винятку.

try {
    // Do something
    // Зроби щось
} catch (\Exception $e) {
    // Handle exception
    // Обробляти виняток
}

// Custom exceptions
// Спеціальні винятки

class MyException extends Exception {}

try {

    $condition = true;

    if ($condition) {
        throw new MyException('Something just happened');
    }

} catch (MyException $e) {
    // Handle my exception
    // Обробляти мій виняток
}

```

## More Information

Visit the [official PHP documentation](http://www.php.net/manual/) for reference
and community input.

If you're interested in up-to-date best practices, visit
[PHP The Right Way](http://www.phptherightway.com/).

A tutorial covering basics of language, setting up coding environment and making
few practical projects at [Codecourse - PHP Basics](https://www.youtube.com/playlist?list=PLfdtiltiRHWHjTPiFDRdTOPtSyYfz3iLW).

If you're coming from a language with good package management, check out
[Composer](http://getcomposer.org/).

For common standards, visit the PHP Framework Interoperability Group's
[PSR standards](https://github.com/php-fig/fig-standards).

## Більше інформації

Відвідайте [офіційну документацію PHP](http://www.php.net/manual/) для довідки
та внесок спільноти.

Якщо вас цікавлять найновіші найкращі практики, відвідайте
[PHP The Right Way](http://www.phptherightway.com/).

Посібник, який охоплює основи мови, налаштування середовища кодування та створення
кілька практичних проектів на [Codecourse - Основи PHP](https://www.youtube.com/playlist?list=PLfdtiltiRHWHjTPiFDRdTOPtSyYfz3iLW).

Якщо ви прийшли з мови з хорошим керуванням пакетами, перевірте
[Composer](http://getcomposer.org/).

Щоб дізнатися про загальні стандарти, відвідайте групу взаємодії PHP Framework
[Стандарти PSR](https://github.com/php-fig/fig-standards).
