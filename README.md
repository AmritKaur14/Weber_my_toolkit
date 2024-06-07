# Weber_my_toolkit

In diesem Toolkit handelt es um meine Notizen während der Vorlesung. 
Falls ein Thema noch kompliziert war nach der Vorlesung habe ich mittels ChatGPT 
probiert nochmals mir ein Thema zu erklären lässen. Diese Beispiele habe ich dann direkt in die Notizen 
hineinkopiert, da es mehr Beispiele mir geholfen haben. 

## Woche 1 
### Funktionen
- Funktionien in JavaScript werden mit dem Schlüsselwort function definniert.
  - Syntax: 
    ```
    function functionName(parameters) {
      // function body
    }
  
### Lambda Expressions
- eine kurze Syntax für Funktionen in JavaScript
  - beispiel:
    ```
    const add = (a, b) => a + b;
    ```
    
## Woche 2
### IIFE: Immediately Invoked Function Expression
Eine Funktion wird direkt nach der Definition aufgerufen
- Beispiel:
  ```
  (function foo() {...}) ();
  ```

### Lambda Calculus

#### Alpha: 
Wird verwendet um die Lesbarkeit und Klarheit vom Code zu verbessern, indem ein parameter umbenennt wird. 
- Beispiel:
  ```
  const id1 = x => x; const id2 = y => y;
  ```

#### Beta: 
Wird verwendet um eine Sprache in Berechnungen mit Funktionen darzustellen.
- Beispiel:
```
( f => x => f (x)) (id) (1) //ersetzen f mit id()
( x => id (x)) (1)  //ersetze x mit 1
( id (1)) //1 in id einfügen
( x => x) (1) 
1
```

#### Eta:
Wird verwendet um redundanten Parameter in Lambda zu eleminieren
Wenn der Parameter in der Funktionsanwendung wie auch in der 
Argumentliste und Funktionskörper verwendet wird kannn die Eta reduktion verwendet werden.
- Beispiel:
```
const both = (x, y) => x + " " + y;
const foo = (x, y) => both(x, y);
const foo = both;
```

## Woche 3

#### Triple:
Eine erweiterung von Pair, wobei dieses aber drei werte enthält. 
- Beispiel:
```
const Triple = x => y => z => f => f(x)(y)(z);
const first = t => t(x => y => z => x);
const second = t => t(x => y => z => y);
const third = t => t(x => y => z => z);
const triple = Triple('a')('b')('c');
console.log(first(triple)); 
console.log(second(triple)); 
console.log(third(triple)); 
```
Hier bei wird zuerst in frist ('a')('b')('c') eingesetzt wobei a der output ist, da laut definition von first x also a berechnet wird.

#### Either 

Wird verwendet bei fehler fällen wenn was falsch oder richtig sein kann. 
- Beispiel:
```
const Left = x => f => g => f(x);
const Right = x => f => g => g(x);
const either = e => f => g => e(f)(g);

```

Left und Right nehmen jeweils den Parameter x, welches wieder entweder f oder g zurückgeben.
Either nimmt zwei Funktionen entgegen f und g. Diese ruft dann e mit entweder f oder g auf jenachdem welcher Parameter übergeben worden ist.
Hier ein Beispiel:
```
const success = Right('Success');

const handleResult = either(
    result => `Failure: ${result}`,
    result => `Success: ${result}`
);
console.log(handleResult(success)); 

```
success ist ein Right und enthält bei Aufruf den Wert 'Success'. handleResult nimmt sucess 
wobei mittels Right die zweite funktion ausgegeben wird also ist der Output 'Success: Success'

## Woche 4

#### Map 
Map wird verwendet um eine Funktion auf jedem Element eines Arrays anzuwenden und dann ein enues Array erstellt.

- Beispiel: 
```
const times = a => b => a * b;
[1, 2, 3].map(x => times(2)(x)); 
```
Hier wird nun jedes einzelne Element ausgewählt und in times aufgerufen und berechnet. Der Output ist somit 2,4,6
```
[1, 2, 3].map(times(2));
```
Hier wird die funktion nun direkt an map übergeben und erhält den output 2,4,6

#### Filter:
Filter gibt zurück wenn jeweils eine Bedingun erfüllt ist.
```
[1, 2, 3].filter(x => x % 2 === 1); 
```
Hier wäre nun der Filter x % 2, somit wird ist der output nur 1 und 3, da zwei herausgefiltert wurde.

#### Reduce
Reduce fürt dazu dass ein Ergenbis aus einem verarbeiteten Array erzeugt wird.
```
const plus = (accu, cur) => accu + cur;
```
Hier werden zwei Argumente genommen welche dann zu ein Ergebnis berechnet werden. 
Zum Beispeil kann ein Array [1,2,3] verwendet werden wobei zuerst 1 + 2 = 3 dann 3 + 3 = 6 berechnet wird und somit das resultat 6 ist. 

## Woche 5

#### Goodie:
```
console.log("hi")
[1,2,3].map( X => x*x)
[1,2,3] wird probiert auf einem objekt aufzurufen und wird als index gesehen deshalb gibt es einen fehler.
1,2,3 wäre aber richtig und gibt 3.
```
Deshalb ; nicht vergessen!

#### Scripting
JS ist passende Sprache für kleine Browser automatisierung. Ausserhalb nicht gut gebruachbar..
Scripting ist eine Methode zur Automatisierung von Befehlen. Es nutzt verschiedene Quellen wie Dateien, URLs oder 
Benutzereingaben, um Text zu bearbeiten.


## Woche 6


#### Object
Wie in Java bekannt als Klasse und ein Oject das erzeugt wird. 

#### this
Wichtig: Nicht wie in Java!
```
const meinObjekt = {
  name: "John",
  grüssen: function() {
    console.log("Hallo, " + this.name);
  }
};

meinObjekt.grüssen();
```
Hier wird this auf das Objekt welches es aufruft bezogen, also wäre hier mit name John gemeint.
Jedoch wenn es sich um Lambdas handelt, dann es nicht von meinObjekt referenziert, sondern ausserhalb also an einem globalen Objekt.


## Woche 7

#### extends
Hier ein Beispiel von ChatGpt welches eine Methode einer abgeleiteten Klasse erweitert.
```
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  introduce() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
  }
}

class Student extends Person {
  constructor(name, age, major) {
    super(name, age);
    this.major = major;
  }

  introduce() {
    super.introduce();
    console.log(`I am studying ${this.major}.`);
  }
}

const student = new Student('Alice', 20, 'Computer Science');
```
Ein Student ist eine Person wobei eine Person sich mit dem namen und alter vorstellt. Ein Student hat sich als Perosn 
vorgsetellt un noch hinzugefügt was er studiert.

## Woche 8
#### Datentypen
Boolean, Number, String, Object, BigInt, Symbol, Null und Undefined sind die Datentypen in JavaScript
Typeof wird verwendet, um den Typ einer Variablen oder eines Ausdrucks zurückzugeben.

#### Funktionen
@function, @constructor, @callback, @param und @return sind Annotationen, welche in klassischen 
Funktionen verwendet werden.

#### Schnittstelle:
@typedef wird verwendet um  benutzerdefinierten Typ oder eine Schnittstelle zu definieren.
## Woche 9

#### Async 
Asynchrone Programmierung ermöglicht Zeitaufwändige Operationen auszuführen ohne den 
Hauptthread zu blockieren. Verglichen zu Callback und Promises ist es eine einfachere Möglichkeit zu verwenden.
Ein async bei eine Funktion gibt immer ein promise zurück. 
Await wird innerhalb von async verwendet und pausiert eine Funktion bis das promise erfüllt ist.
- Beispiel:
```
const foo = async i => {
  const x = await processEven(i).catch(err => err); 
  console.log("foo: " + x);
}; 

foo(4);

```
Hier pausiert await processEven(i), bis Promise erfüllt ist, also die Ausgabe von processEvene(i) muss stimmen.

## Woche 10

#### Modules
Idee JavaScrip hätte nur ein paar zeilen lang sein sollte sein, um kleine automatirierungen zu machen.
Jedoch wurde viel mehr daraus, deshalb werden Modules gebarucht.
Warum Module?
Modulen ermöglichen es, Code zu organisieren und klare Abhängigkeiten zwischen verschiedenen 
Teilen des Codes herzustellen. Es werden Fehler vermieden, die durch globale Variablen, unzureichendes Scoping und
Namenskonflikte entstehen können.
Module helfen dabei, zu unterscheiden, wie der Code bearbeitet und wie er bereitgestellt werden soll.
Module sind keine Packages und haben keine Verisonen.

## Woche 11
#### Promise: 
- Beispiel mit Promise:
```
const processEven = i => new Promise((resolve, reject) => {
  if (i % 2 === 0) {
    resolve(i);
  } else {
    reject(i);
  }
});
processEven(4).then(num => console.log(num))
```
Hier wird die Funktion processEven definiert welche für die übergebene Zahl überprüft ob diese gerade oder ungerade ist 
und gibt ein Promise zurück ob die Bedingung erfüllt oder nicht erfüllt ist, also durch resolve und reject.
## Woche 13

#### Iterator 
Iterator hat eine Methode next() welches immer auf das nächste Object referenziert und zugegriffen werden kann.
Symbol.iterator() ist eine Methode welche ein Iterator Objekt zurückgibt welches Elemente aus einer Datenstruktur repräsentiert.




