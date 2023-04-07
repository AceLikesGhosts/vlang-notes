[VLang](vlang.io) is a.. "esolang", i guess? its fast, its simple. good enough for me to learn!
this is just some stuff i found interesting so like, cope? ratio? L + bozo?

key things:
**only allows lower_snake_case.**
**structs msut be uppercase first letter**
`:=` assigns
`=` reassigns
has structs
has types
- type cast using `T(val)`
strings
- contents of strings are immutable always (will panic)
- made up of runes

a simple "hello world" application looks like this
```v
// the name of the module
module main

// defines a new function named main, that gets called on program start
fn main() {
	// prints to the standard output and flushes it, same as
	// java's "System.out.println"
	println('hello world!')
}
```

unlike other langs vlang uses a different way of assign vars (atleast from what ive seen from mainly using TS)

to define a variable you use `:=`, for example
```v
// ...
fn main() {
	my_var := 'whatever'
}
```

in order to reassign that variable, you have to mark it as mutable using the `mut` keyword
```v
// ...
fn main() {
	// := assigns
	mut my_var := 'whatever'
	// while = reassigns
	my_var = 'new value'
}
```

although while you can mark a string as mutable, the actual contents of the string are immutable
ex: 
```v
// ...
fn main() {
	mut my_var := 'whatever'
	my_var[0] = 'a' // V panics, strings values arent mutable.
}
```

on the topic of strings, a string is really just an array of runes (chars)
```v
// ...
fn main() {
	mut my_var := 'whatever'
	println(my_var.runes()) // [`w`, `h`, `a`, `t`, `e`, `v`, `e`, `r`]
}
```


structs:
```v
// forced to start with a capital, idk why but it is.
struct My_Struct {
	my_field String
}

// defines a method on the struct
fn (mut struct My_Struct) print_field() {
	println(struct.my_field)
}
```

that roughly equates to this class in typescript
```ts
class My_Struct {
	private my_field: string;

	public print_field(): string {
		console.log(my_field);
	}
}
```

in order to create a new instance of the struct you have to do this
```v
// ... module and shit

fn main() {
	// creates a new instance of the struct, with "my_field" set as "string text"
	mut my_struct_thing := My_Struct{ my_field: 'string text' }
	// runs the method that prints the field
	my_struct_thing.print_field()
}
```

v has its own package manager (vpm) although its small there is some cool stuff on it, one cool package ive seen in the V community is pico.v, a fast asf (!!!)  http server (fastest for plaintext)

alongside vpm, there are builtin packages (ig, just modules builtin) that are vv cool, and typically for example there is `os`

```
module main

// imports the OS module
import os

fn main() {
	println(os.args) // the args passed to the program
}
```

you can compile this by using `v -keepc run .` or `v .` from there run the executeable with `./main.exe --my-very-cool-args lol` and the example there should print `['/path/to/main.exe', '--my-very-cool-args', 'lol']`

a for loop in this lang is also vv easy (for arrays)
this prints out each of the numbers in the array
```v
module main

fn main() {
	numbers := [1,2,3,4,5,6]

	for num in numbers {
		println(num) // prints each number
	}

	// or if you want the index
	// for i, num in numbers {...
}
```

looping over a map is also vv easy
```v
module main

fn main() {
	my_map := {
		'key': 'value'
		'thing': 'two'
	}

	for k, v in my_map {
		println('${key}: ${value}')
	} 
}
```

this lang actually has good enums too (unlike typescript)
```v
module main

enum My_Enum {
	thing
	thing_two
}

fn main() {
	My_Enum.thing // whatever
	// idk how to make this an example
}
```

