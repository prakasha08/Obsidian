# Objects
object A collection of related properties and/or methods Can represent real world objects (people, products, places) object {key: value, function())
```java
const person1 = {
firstName: "Spongebob",
lastName: "Squarepants",
age: 30,
isEmployed: true,
sayHello: function()(console.log("Hi! I am Spongebob!")},
eat: function(){(console.log("I am eating a Krabby Patty")},
}
const person2 = {
firstName: "Patrick",
lastName: "Star",
age: 42,
isEmployed: false,
sayHello: () => console.log("Hey, I'm Patrick..."),
eat: () => console.log("I am eating roast beef, chicken, and pizza"),
}
personi.eat();
person2.eat();
```
## This
***this reference to the object where THIS is used (the object depends on the immediate context) person.name this.name
```js
const person1 = {
name: "Spongebob",
favFood: "hamburgers",
sayHello: function(){console.log(Hi! I am ${this.favFood})},
eat: function(){console.log(${this.name} is eating ${this.favFood}
}
const person2 = {
name: "Patrick",
favFood: "pizza",
sayHello: function(){console.log(Hi! I am ${person2 favFood})},
eat: function(){console.log(${this.name} is eating ${this.favFood})
}
person1.eat();
person2.eat();
```

## Constructor
***Constructor is special method for defining the properties and methods of objects
```js
function Car (make, model, year, color){
this.make make,
this.model = model,
this.year year,
this.color = color,
this.drive = function(){console.log(You drive the ${this.model})}
}
const car1= new Car ("Ford", "Mustang", 2024, "red");
const car2= new Car("Chevrolet", "Camaro", 2025, "blue");
const car3 new Car("Dodge", "Charger", 2026, "silver");
carl.drive();
car2.drive();
car3.drive();
```

## nested objects

nested objects Objects inside of other Objects.
Allows you to represent more complex data structures
Child Object is enclosed by a Parent Object
Person(Address{}, ContactInfo{}}
ShoppingCart{Keyboard(), Mouse(), Monitor{}}

```js
const person = {
fullName: "Spongebob Squarepants",
age: 30,
isStudent: true,
hobbies: ["karate", "jellyfishing", "cooking"],
address: {
street: "124 Conch St.",
city: "Bikini Bottom",
country: "Int. Water"
}
}
console.log(person.fullName);
console.log(person.age);
console.log(person.isStudent);
console.log(person.hobbies [2]);
console.log(person.address);
console.log(person.address.age);
			(or)
for(const property in person.address){
	console.log(person.address(property);
}
```

```js
class Person{
constructor (name, age, ...address) (
this.name name;
this.age age;
this.address new Address(...address);
}
}
class Address{
constructor(street, city, country) {
this.street = street;
this.city city;
this.country = country;
}
const person1 new Person("Spongebob", 30,"124 Conch St.","Bikini Bottom","Int. Waters");
const person2 = new Person("Patrick", 37,"128 Conch St.","Bikini Bottom","Int. Waters");
const person3 = new Person("Squidward", 45,"126 Conch St.", "Bikini Bottom","Int. Waters");
console.log(person3.address);
```
## Sorting Object
sort() method used to sort elements of an array in place. Sorts elements as strings in lexicographic order, not alphabetical lexicographic (alphabet + numbers + symbols) as strings
```js
const people = [{name: "Spongebob", age: 30, gpa: 3.0),
(name: "Patrick", age: 37, gpa: 1.5), (name: "Squidward", age: 51, gpa: 2.5),
(name: "Sandy", age: 27, gpa: 4.0)]
people.sort((a, b) => a.age - b.age);
people.sort((a, b) => b.age - a.age);
console.log(people);

people.sort((a, b) => a.name.localeCompare(b.name));//arrange them in lexographical order.
```

## Date object 
Date objects Objects that contain values that represent dates and times These date objects can be changed and formatted
// Date(year, month, day, hour, minute, second, ms)
```js
const date = new Date(2024, 0, 1, 2, 3, 4, 5);
console.log(date);
```

```js
const date = new Date("2024-01-02T12:00:00Z");
```

```js
const date = new Date();
const year date.getFullYear();
const month = date.getMonth();
const day date.getDate();
const hour date.getHours();
const minutes date.getMinutes();
const seconds date.getSeconds();
const dayOfWeek= date.getDay();
console.log(year);
console.log(month);
console.log(day);
console.log(hour);
console.log(minutes);
console.log(seconds);
console.log(dayOfWeek);
```

```js
const date = new Date();
date.setFullYear(2024);
date.setMonth(0);
date.setDate(1);
date.setHours(2);
date.setMinutes(3);
date.setSeconds(4);
console.log(date);
```

```js
const datel new Date("2023-12-31");
const date2 = new Date("2023-12-01");
if(date2 > datel) { console.log("HAPPY NEW YEAR!");
```

## Closure
// closure
A function defined inside of another function, the inner function has access to the variables and scope of the outer function.
Allow for private variables and state maintenance Used frequently in JS frameworks: React, Vue, Angular
```js
function createCounter(){
let count = 0;
function increment(){
count++;
console.log(Count increased to ${count});
function getCount(){
return count;
}
return (increment, getCount);
}
const counter createCounter();
counter.increment();
counter.increment();
counter.increment();
counter.increment();
console.log("The current count is ${counter.getCount()));
```

```js
function createGame(){
let score 0;
function increaseScore (points) {
score += points;
console.log(+${points}pts');
}
function decreaseScore (points) {
score - points;
console.log(${points}pts');
}
function getScore(){
return score;
}
return {increaseScore, decreaseScore, getScore);
}
const game = createGame();
game.increaseScore (5);
game.increaseScore(6);
game.decreaseScore (3);
console.log(The final score is ${game.getScore())pts');
```
# Array of Objects

```js
const fruits = [{name: "apple", color: "red", calories: 95},
{name: "orange", color: "orange", calories: 45},
{name: "banana", color: "yellow", calories: 105},
{name: "coconut", color: "white", calories: 159},
{name: "pineapple", color: "yellow", calories: 37}];
console.log(fruits [2].calories);

fruits.push((name: "grapes", color: "purple", calories: 62));//Add new abject at last

fruits.pop();// grapes object

fruits.splice(1, 2);
//forEach Loop
forEach()
fruits.forEach(fruit console.log(fruit.color));

//map()
const fruitNames fruits.map(fruit => fruit.name);
const fruitColors
fruits.map(fruit => fruit.color);
const fruitCalories fruits.map(fruit => fruit.calories);
console.log(fruitNames);
console.log(fruitColors);

// filter()
const yellowFruits = fruits.filter(fruit => fruit.color === "yellow");
const lowCalFruits = fruits.filter(fruit => fruit.calories < 100);
const highCalFruits = fruits.filter(fruit => fruit.calories >= 100);
console.log(highCalFruits);

// reduce()
const maxFruit = fruits.reduce((max, fruit) =>
fruit.calories > max.calories ?
fruit: max);
const minFruit = fruits.reduce( (min, fruit) =>
fruit.calories < min.calories ?
fruit: min);
console.log(maxFruit);
console.log(minFruit);
```
# Class
***class = (ESG feature) provides a more structured and cleaner way to work with objects compared to traditional constructor functions

```js
ex. static keyword, encapsulation, inheritance
class Product{
constructor (name, price){
this.name = name;
this.price price;
}
displayProduct(){
console.log(`Product: ${this.name}`);
console.log(`Price: $$(this.price.toFixed(2)}`);
calculateTotal (salesTax) (
return this.price (this.price salesTax);
}
}
const salesTax = 0.05;
const product1 = new Product("Shirt", 19.99);
const product2 = new Product("Pants", 22.50);
const product3 = new Product("Underwear", 100.00);
product3.displayProduct();
const total product3.calculateTotal (salesTax);
console.log(Total price (with tax): $5(total.toFixed(2)});
```
# Static Keyword
***static keyword that defines properties or methods that belong to a class itself rather than the objects created from that class (class owns anything static, not the objects)
```js
class User{
static userCount = 0;
constructor (username) { this.username username; User.userCount++;
}
static getUserCount(){
console.log("There are ${User.userCount) users online);
}
sayHello(){
console.log("Hello, my username is ${this.username}");
}
}
const user1 = new User("Spongebob");
const user2 = new User("Patrick");
const user3 = new User("Sandy");
user1.sayHello();
user2.sayHello();
user3.sayHello();
User.getUserCount();
```

# Destructuring(objects ,Arrays)

**destructuring = extract values from arrays and objects, then assign them to variables in a convenient way
[]= to perform array destructuring
()= to perform object destructuring
**

```js
EXAMPLE 4
//EXTRACT VALUES FROM OBJECTS
const person1 = {
firstName: "Spongebob",
lastName: "SquarePants",
age: 30,
job: "Fry Cook",
}
const person2 = {
firstName: "Patrick",
lastName: "Star",
age: 34,
}
const {firstName, lastName, age, job="Unemployed") person2;
console.log(firstName);
console.log(lastName);
console.log(age);
console.log(job);
```

```js
//
EXAMPLE 5
..
// DESTRUCTURE IN FUNCTION PARAMETERS
function displayPerson({firstName, lastName, age, job)){
console.log(name: ${firstName) $(lastName}');
console.log(age: ${age});
console.log(job: ${job));
}
const person1 = {
firstName: "Spongebob",
lastName: "SquarePants",
age: 30,
job: "Fry Cook",
}
const person2 = {
firstName: "Patrick",
lastName: "Star",
age: 34,
}
displayPerson(person2);
```

# Getter & setter
**/getter special method that makes a property readable
// setter special method that makes a property writeable
// validate and modify a value when reading/writing a property
```js
class Person{
constructor (firstName, lastName, age) {
this.firstName firstName;
this.lastName lastName;
this.age age;
}
set firstName (newFirstName) {
if(typeof newFirstName === "string" && newFirstName.length > 0){
this._firstName = newFirstName;
}
else{
console.error("First name must be a non-empty string");
}
}
set lastName (newLastName) {
if(typeof newLastName === "string" && newLastName.length > 0){
this._lastName = newLastName;
}
else{
console.error("Last name must be a non-empty string");
}
}
set age (newAge) {
if(typeof newAge === "number" && newAge.length > 0){
this._age = newLastName;
}
else{
console.error("Age name must be a number");
}
}
get firstName(){
return this._firstName;
}
get lastName(){
return this._lastName;
}
get fullName(){
return this._firstName+""+ this._lastName;
}
get age(){
return this._age;
}
const person new Person("Spongebob", "Squarepants", 30);
console.log(person.firstName);
console.log(person.lastName);
console.log(person.fullName);
console.log(person.age);
```

# Inheritance
```js
// inheritance allows a new class to inherit properties and methods from an existing class (parent -> child)
helps with code reusability
class Animal{ alive = true;
eat(){
console.log("This ${this.name} is eating");
}
sleep() {
console.log("This ${this.name} is sleeping");
}
}
class Rabbit extends Animal{ 
name "rabbit";
run(){ 
console.log("This ${this.name) is running");
}
}
class Fish extends Animal{ 
name = "fish";
swim(){
console.log("This ${this.name} is swimming");}
class Fish extends Animal{
name "fish";
swim(){
console.log("This $(this.name) is swimming");
}
class Hawk extends Animal {
name "hawk";
fly(){
console.log("This $(this.name) is flying");
}
const rabbit = new Rabbit();
const fish = new Fish();
const hawk = new Hawk();
console.log(hawk.alive);
hawk.eat();
hawk.sleep();

```
## Super Class
super keyword is used in classes to call the constructor or access the properties and methods of a parent (superclass)
this = this object
super = the parent
```js
class Animal(
constructor (name, age){
this.name = name; 
this.age age;
}
move (speed){
console.log(`The ${this.name} moves at a speed of ${speed}mph`);
}
}
class Rabbit extends Animal(
constructor (name, age, swimSpeed) {
super(name, age);
this.runSpeed = runSpeed;
run(){
console.log(`This $(this.name} can run`);
super.move(this.runSpeed);
}
}
class Fish extends Animal(
constructor (name, age, swimSpeed) {
super(name, age);
this.swimSpeed swimSpeed;
swim(){
console.log(`This $(this.name} can swim`);
super.move(this.swimSpeed);
}
}
class Hawk extends Animal{
constructor(name, age, flySpeed) (
super (name, age); 
this.flySpeed flySpeed;
fly(){
console.log(This ${this.name) can fly);
super.move(this.flySpeed);
}
}
const rabbit new Rabbit("rabbit", 1, 25);
const fish new Fish("fish", 2, 12);
const hawk пен Hawk ("hawk", 3, 50);
fish.swim();
```

