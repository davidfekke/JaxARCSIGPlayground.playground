# JaxARCSIG Playground file for Swift 4

Here are the code examples from the presentation on Swift

```swift
//: Playground - noun: a place where people can play

import Cocoa

// # This is an playground with example from the JaxARCSIG presentation on Swift 4

let group = "JaxARCSIG"

var str = "Hello, \(group)"

print(str)

// Use var for mutable values
var name = "David"
var age = 29

// change values
name = "Dave"
age = 30

// Use let for immutable values
let myName = "Bob"
let myAge = 41

// trying to change the assignment
// myName = "Bobby" // will return an error

let str1 = "David"

var str2: String = "David"
str2 = "Dave"

// Use ! or ? to make type optional
var str3: String? = "David"
str3 = nil
str3 = "Dave"

// Basic Array
let myArray = ["Dog", "Cat", "Bird", "Snake"]

// Dictionary
let myDict = ["Bob": 42, "Joe": 40, "Karen": 39, "John": 35]

// Empty Array
var emptyArray: [String]
emptyArray = myArray

// emptyDictionary
var emptyDict: [String:Int]
emptyDict = myDict

let names = ["Anna", "Alex", "Brian", "Jack"]
for name in names {
    print("Hello, \(name)!")
}

let numberOfLegs = ["spider": 8, "ant": 6, "cat": 4]
for (animalName, legCount) in numberOfLegs {
    print("\(animalName)s have \(legCount) legs")
}

var elevator = 0
let topFloor = 11

while elevator < topFloor {
    print("Elevator is on the \(elevator) floor")
    elevator += 1
}

for i in 1...9 {
    print("Number \(i)")
}

// the same as

for i in 1..<10 {
    print("Number \(i)")
}

// Can also increment by more than 1 at a time

let hours = 12
let hourInterval = 3
for tickMark in stride(from: 3, through: hours, by: hourInterval) {
    print("render the \(tickMark) every 3 hours") // (3, 6, 9, 12)
}

let myNumber: Int = 32

if myNumber <= 33 {
    print("under or equal to 33")
} else {
    print("Older than 33")
}

let approximateCount = 62
let countedThings = "moons orbiting Saturn"
let naturalCount: String
switch approximateCount {
    case 0:
        naturalCount = "no"
    case 1..<5:
        naturalCount = "a few"
    case 5..<12:
        naturalCount = "several"
    case 12..<100:
        naturalCount = "dozens of"
    case 100..<1000:
        naturalCount = "hundreds of"
    default:
        naturalCount = "many"
}

class Starship {
    init (prefix: String?) {
        self.prefix = prefix
    }
    var prefix: String?
}
let ncc1701 = Starship(prefix: "USS")

// let prefix: String = ncc1701.prefix
// Will get a type error because prefix is an optional

let prefix2: String = ncc1701.prefix!
// force unwrap will work if there is a value, but considered a bad practice

if let prefix3 = ncc1701.prefix {
    print(prefix3) // USS
}

//guard let prefix4 = ncc1701.prefix else {
//   throw Error
//}

func someThrowingFunction() throws -> Int {
    // ...
    return 12
}
 
let x = try? someThrowingFunction()
 
let y: Int?
do {
    y = try someThrowingFunction()
} catch {
    y = nil
}

func printThisValue(_ param: String) {
    print("Printing value \(param)")
}

printThisValue("Gato")
// "Printing value Gato"

func say(this param: String) {
    print(param)
}

say(this: "Hello Jax ARCSIG")
// "Hello Jax ARCSIG"

func adder(_ first: Int, add second: Int) -> Int {
    return first + second
}

let addedValue = adder(32, add:49)
print("Added value \(addedValue)")

func swapTwoStrings(_ a: inout String, _ b: inout String) {
    let temporaryA = a
    a = b
    b = temporaryA
}
 
func swapTwoDoubles(_ a: inout Double, _ b: inout Double) {
    let temporaryA = a
    a = b
    b = temporaryA
}

// Be changed to one function
func swapTwoValues<T>(_ a: inout T, _ b: inout T) {
    let temporaryA = a
    a = b
    b = temporaryA
}

var bob = "Bob"
var doug = "Doug"

swapTwoValues(&bob, &doug)
print(bob) // Doug


let namesArr = ["Chris", "Alex", "Ewa", "Barry", "Daniella"]

func backward(_ s1: String, _ s2: String) -> Bool {
    return s1 > s2
}

var reversedNames = namesArr.sorted(by: backward)
// reversedNames is equal to ["Ewa", "Daniella", "Chris", "Barry", "Alex"]”

reversedNames = namesArr.sorted(by: { (string1: String, string2: String) -> Bool
    in return string1 > string2 })

reversedNames = namesArr.sorted(by: { (string1, string2) in return string1 > string2 })

reversedNames = namesArr.sorted(by: { (string1, string2) in string1 > string2 })

reversedNames = namesArr.sorted(by: { $0 > $1 })

reversedNames = namesArr.sorted(by:) { $0 > $1 }

reversedNames = namesArr.sorted(by:>)

struct Rectangle {
    let width: Float
    let height: Float
}

let myRect = Rectangle(width: 40.0, height: 30.0)

print("the width of the rect is \(myRect.width)")

struct RectangleWithArea {
    var width: Float
    var height: Float
    var area: Float {
        return width * height
    }
}

let myRect2 = RectangleWithArea(width: 40.0, height: 30.0)

print("the area of the rect is \(myRect2.area)")


struct Person {
    let name: String
    
    func sayName() {
        print("This person's name is \(name)")
    }
}

let debbie = Person(name: "Debbie")
debbie.sayName()

class PersonC {
    var firstName: String
    var lastName: String
    var age: Int
    
    init(first firstName: String, last lastName: String, age: Int) {
        self.firstName = firstName
        self.lastName = lastName
        self.age = age
    }
    
    func describePerson() -> String {
        return "\(self.firstName) \(self.lastName) is \(self.age) years old"
    }
}

let john = PersonC(first: "John", last: "Lyons", age: 42)
let personDesc = john.describePerson() // "John Lyons is 42 years old


class Employee : PersonC {
    var employeeId: Int?
    init(first firstName: String, last lastName: String, age: Int, id employeeId: Int?) {
        self.employeeId = employeeId
        super.init(first: firstName, last: lastName, age: age)
    }
    
    convenience init() {
        self.init(first: "firstName", last: "lastName", age: 0, id: nil)
    }
}

let rich = Employee(first: "Richard", last: "Dutton", age: 62, id: 8907890)
let empDesc = rich.describePerson()
print(empDesc)

enum CompassPoint {
    case north
    case south
    case east
    case west
}

var directionToHead = CompassPoint.west

switch directionToHead {
case .north:
    print("Lots of planets have a north")
case .south:
    print("Watch out for penguins")
case .east:
    print("Where the sun rises")
case .west:
    print("Where the skies are blue")
}
// Prints "Where the skies are blue"

extension Double {
    var km: Double { return self * 1_000.0 }
    var m: Double { return self }
    var cm: Double { return self / 100.0 }
    var mm: Double { return self / 1_000.0 }
    var ft: Double { return self / 3.28084 }
}
let oneInch = 25.4.mm
print("One inch is \(oneInch) meters")
// Prints "One inch is 0.0254 meters”

protocol FullyNamed {
    var fullName: String { get }
}

struct PersonP: FullyNamed {
    var name: String
    var fullName: String {
        return name
    }
}
let johnApple = PersonP(name: "John Appleseed")

class StarshipP: FullyNamed {
    var prefix: String?
    var name: String
    init(name: String, prefix: String? = nil) {
        self.name = name
        self.prefix = prefix
    }
    var fullName: String {
        return (prefix != nil ? prefix! + " " : "") + name
    }
}
var ncc1701a = StarshipP(name: "Enterprise", prefix: "USS")

struct Swifter: Decodable {
    let fullName: String
    let id: Int
    let twitter: URL
}

let json = """
{
 "fullName": "Federico Zanetello",
 "id": 123456,
 "twitter": "http://twitter.com/zntfdr"
}
""".data(using: .utf8)! // our data in native (JSON) format

let myStruct = try JSONDecoder().decode(Swifter.self, from: json)
// Decoding our data

print(myStruct.fullName) // decoded!!!!!


```