# Rust Notes


* println! = macro
* std::io = how to import
* variables are immutable by default
	* initilize with "let" eg. let foo = bar;
* use "mut" to make it mutable: let mut foo = bar;
* String::new() is a static meth=od, signified by cons
* references are also immutable by default: use references to reference variables in memory
	* use & mut to make mutable reference

* Shadowing
	* use "let" and keyword again to reassign it even if it is immut, can change types with this
	* mut does not let you cnage type

* Type annotations: let f: bool = false;
* Arrays and tuples have fixed length
* arrs have to have same type for all elements
* index like tup.0, arr[0]
* pattern match to deconstruct
* eg. let a: [i32; 5] = [1, 2, 3, 4, 5]; let a = [3: 5];
* Types and function returning expression example:
	fn plus_one(x: i32) -> i32 {
	    x + 1
	}

* Ownership
	* helps manage garbage
	* .clone() = deep copy (copy all data into new object)
		* otherwise: shallow copy, the old variable is deleted (basically moved from old variable name to new variable name)
		* Doesn't hold for stack data or anything that extends copy
		* ownership gets passed into function, need to return to pass ownership back to main
* References
	* pass in param into function wihtout transferring ownership
	* calc(& string)
	* fn calc (mystr : &String) {}
	* references are immutable by default
	* use &mut to make it mutable
	* can have multiple immutable references but only one mutable reference (no imm + mut either)
* Struct
	* Entire thing must be mutable or immutable
	* Can also use tuple struct:
	```	 struct Color(i32, i32, i32);
    	 let black = Color(0, 0, 0);
			#[derive(Debug)]
				struct Rectangle {
    				width: u32,
    				height: u32,
				}

				fn main() {
    				let rect1 = Rectangle {
        				width: 30,
        				height: 50,
    				};

    				println!("rect1 is {:?}", rect1);
				} 
	```
* Methods:
	* Implemented to a struct
	* 
	``` 
		impl Rectangle {
    		fn area(&self) -> u32 {
        		self.width * self.height
    		}
		} 
	```
	* you can put any kind of data inside an enum variant: strings, numeric types, or structs, for example. You can even include another enum!
	* you can also define methods for enums
* Options
	* Enum, can be None or Some
	* used to signify there can be a null value for something
* Match
	* 
	```
			fn value_in_cents(coin: Coin) -> u8 {
    		match coin {
        		Coin::Penny => 1,
       		 	Coin::Nickel => 5,
     		   	Coin::Dime => 10,
        		Coin::Quarter => 25,
    		}
		}
	```
	* exhaustive
	* use _ as catch-all
* If let: syntactic sugar for when we want to match for one case and do nothing for other
* Modules
	* defined with mod
	* group definitions together
	* add pub to reference modules/definitions inside it
* Vectors
	* vectors only store values of same type
	* use enum in order to store more types
	* do this becuse of the storing on heap
	* infinite len tho
* String
	* Slicing
		* let hello = "Здравствуйте"; let s = &hello[0..4];
	* 
