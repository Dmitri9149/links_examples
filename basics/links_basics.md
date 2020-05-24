#### Lists
#### Lists.......Polymorphic variants
********************************************
```console
dmitri@dmitri-Lenovo-H50-00:~/links$ linx --config='/home/dmitri/info/linx_config_v1.config'
 _     _ __   _ _  __  ___
/ |   | |  \ | | |/ / / ._\
| |   | | , \| |   /  \  \
| |___| | |\ \ | |\ \ _\  \
|_____|_|_| \__|_| \_|____/
Welcome to Links version 0.9.1 (Burghmuirhead)
links> 1::4::9::[];
[1, 4, 9] : [Int]
links> [1,2,3,4];
[1, 2, 3, 4] : [Int]
links> [];
[] : [_::Any]
links> var x ="apple";
x = "apple" : String
links> ["banana", x];
["banana", "apple"] : [String]
links> [1,2]++[2,3,4,6];
[1, 2, 2, 3, 4, 6] : [Int]
links> hd([1,2,3,4,5]);
1 : Int
links> tl([1,2,3,4,5]);
[2, 3, 4, 5] : [Int]
links> take(3,[1,2,3,4]);
[1, 2, 3] : [Int]
links> drop([1,2,3,4,5]);
<stdin>:1: Type error: The function
    `drop'
has type
    `(Int, [a]) ~b~> [a]'
while the arguments passed to it have types
    `[Int]'
and the currently allowed effects are
    `wild'
In expression: drop([1,2,3,4,5]).
 
links> drop(2,[1,2,3,4]);
[3, 4] : [Int]
links> var s = [1,2,3,4];
s = [1, 2, 3, 4] : [Int]
links> switch (s) {
...... case []-> Empty
...... case x::xs -> NonEmpty
...... };
NonEmpty : [|NonEmpty|Empty|_::Any|]
links> [1....10];
***: Parse error: <stdin>:1

  [1....10];
        ^ 
links> [1..10);
***: Parse error: <stdin>:1

  [1..10);
         ^ 
links> [1..10];
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10] : [Int]
links> ##########
...... ;
links> ############# Tuples;
...... ;
links> var a = 1;
a = 1 : Int
links> (a,"OK");
(1, "OK") : (Int, String)
links> ############ Records;
...... ;
links> (listname="Bond", firstname="James", license="To kill");
(firstname = "James", license = "To kill", listname = "Bond") : (firstname:String,license:String,listname:String)
links> var item = (drinkname="latte", price = 2.0 + 0.5);
<stdin>:1: Type error: The infix operator
    `+'
has type
    `(Int, Int) -a-> Int'
while the arguments passed to it have types
    `Float'
and
    `Float'
and the currently allowed effects are
    `wild'
In expression: 2.0 + 0.5.
 
links> var item = (drinkname="latte", price = 2.0 + .0.5);
***: Parse error: <stdin>:1

  var item = (drinkname="latte", price = 2.0 + .0.5);
                                                ^ 
links> var item = (drinkname="latte", price = 2.0 +. 0.5);
item = (drinkname = "latte", price = 2.5) : (drinkname:String,price:Float)
links> var item = ("drink" + "name" = "latte", price = 2.0 +. 0.5) ## NOT OK ;
***: Parse error: <stdin>:1

  var item = ("drink" + "name" = "latte", price = 2.0 +. 0.5) ## NOT OK ;
                                ^ 
links> item.drinkname == "latte";
true : Bool
links> (lastname="Bond", firstname="James").lastname == "Bond";
true : Bool
links> ############## Record Modifications ;
...... ;
links> (caffeineContent = 60| item);
(caffeineContent = 60, drinkname = "latte", price = 2.5) : (caffeineContent:Int,drinkname:String,price:Float)
links> (item with drinkname = "cappuccino");
(drinkname = "cappuccino", price = 2.5) : (drinkname:String,price:Float)
links> ####### Polymorphic variants
...... ;
links> Automobile(Diesel);
Automobile(Diesel) : [|Automobile:[|Diesel|_::Any|]|_::Any|]
links> Automobile(Unleaded);
Automobile(Unleaded) : [|Automobile:[|Unleaded|_::Any|]|_::Any|]
links> Camel(2);
Camel(2) : [|Camel:Int|_::Any|]
links> Camel(4);
Camel(4) : [|Camel:Int|_::Any|]
links> [|Automobile: [|Diesel:() | Unleaded:() | Biodiesel:()|] |
***: Parse error: <stdin>:1

  [|Automobile: [|Diesel:() | Unleaded:() | Biodiesel:()|] |
    ^ 
links> [|Automobile: [|Diesel:() | Unleaded:() | Biodiesel:()|] |Camel:Int|];
***: Parse error: <stdin>:1

  [|Automobile: [|Diesel:() | Unleaded:() | Biodiesel:()|] |Camel:Int|];
    ^ 
links> [|Automobile: [|Diesel | Unleaded | Biodiesel|] |Camel:Int|];
***: Parse error: <stdin>:1

  [|Automobile: [|Diesel | Unleaded | Biodiesel|] |Camel:Int|];
    ^ 
links> var target = Camel;
target = Camel : [|Camel|_::Any|]
links> switch (target) {
...... case Camel (humpCount) -> humpCount
...... case Automobile(fuelType)-> 0
...... }
...... ;
<stdin>:1: Type error: The type of an input to a switch should match the type of its patterns, but the expression
    `target'
has type
    `[|Camel|a::Any|]'
while the patterns have type
    `[|Automobile:b|Camel:Int|]'
In expression: switch (target) {
case Camel (humpCount) -> humpCount
case Automobile(fuelType)-> 0
}.
 
links> var target = Camel(2);
target = Camel(2) : [|Camel:Int|_::Any|]
links> switch (target) {
...... case Camel (humpCount) -> humpCount
...... case Automobile(fuelType)-> 0
...... };
2 : Int
links> @quit;
dmitri@dmitri-Lenovo-H50-00:~/links$ 
```
**************************************************