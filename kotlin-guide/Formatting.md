# Formatting
## Braces
Braces are not required for when branches and if statement bodies which have no else if/else branches and which fit on a single line.

```
if (string.isEmpty()) return

when (value) {
    0 -> return
    // …
}
```
Braces are otherwise required for any if, for, when branch, do, and while statements, even when the body is empty or contains only a single statement.

```
if (string.isEmpty())
    return  // WRONG!

if (string.isEmpty()) {
    return  // Okay
}
```
### Non-empty blocks
Braces follow the Kernighan and Ritchie style ("Egyptian brackets") for nonempty blocks and block-like constructs:

- No line break before the opening brace.
- Line break after the opening brace.
- Line break before the closing brace.
- Line break after the closing brace, only if that brace terminates a statement or terminates the body of a function, constructor, or named class. For example, there is no line break after the brace if it is followed by else or a comma.

```
return Runnable {
    while (condition()) {
        foo()
    }
}

return object : MyClass() {
    override fun foo() {
        if (condition()) {
            try {
                something()
            } catch (e: ProblemException) {
                recover()
            }
        } else if (otherCondition()) {
            somethingElse()
        } else {
            lastThing()
        }
    }
}
```
A few exceptions for (enum classes)[http://reference_below] are given below.

### Empty blocks
An empty block or block-like construct must be in K&R style.

```
try {
    doSomething()
} catch (e: Exception) {} // WRONG!
```
```
try {
    doSomething()
} catch (e: Exception) {
} // Okay
```

### Expressions
An if/else conditional that is used as an expression may omit braces only if the entire expression fits on one line.

```
val value = if (string.isEmpty()) 0 else 1  // Okay
val value = if (string.isEmpty())  // WRONG!
                0
            else
                1
```
```
val value = if (string.isEmpty()) { // Okay
    0
} else {
    1
}
```

### Indentation
Each time a new block or block-like construct is opened, the indent increases by four spaces. When the block ends, the indent returns to the previous indent level. The indent level applies to both code and comments throughout the block.

### One statement per line
Each statement is followed by a line break. Semicolons are not used.

### Line wrapping
Code has a column limit of 100 characters. Except as noted below, any line that would exceed this limit must be line-wrapped, as explained below.

Exceptions:
- Lines where obeying the column limit is not possible (for example, a long URL in KDoc)
- package and import statements
- Command lines in a comment that may be cut-and-pasted into a shell

### Where to break
The prime directive of line-wrapping is: prefer to break at a higher syntactic level. Also:

- When a line is broken at a non-assignment operator the break comes before the symbol.
- - This also applies to the following “operator-like” symbols:
- - The dot separator (`.`).
- - The two colons of a member reference (`::`).
- When a line is broken at an assignment operator the break comes after the symbol.
- A method or constructor name stays attached to the open parenthesis (`(`) that follows it.
- A comma (`,`) stays attached to the token that precedes it.
- A lambda arrow (`->`) stays attached to the argument list that precedes it.

> Note: The primary goal for line wrapping is to have clear code, not necessarily code that fits in the smallest number of lines.

### Continuation indent
When line-wrapping, each line after the first (each **continuation line**) is indented at least +8 from the original line.

When there are multiple continuation lines, indentation may be varied beyond +8 as desired. In general, two continuation lines use the same indentation level if and only if they begin with syntactically parallel elements.

### Functions
When a function signature does not fit on a single line, break each parameter declaration onto its own line. Parameters defined in this format should use a single indent (+4). The closing parenthesis ()) and return type are placed on their own line with no additional indent.

```
fun <T> Iterable<T>.joinToString(
    separator: CharSequence = ", ",
    prefix: CharSequence = "",
    postfix: CharSequence = ""
): String {
    // …
}
```

#### Expression functions
When a function contains only a single expression it can be represented as an expression function.

```
override fun toString(): String {
    return "Hey"
}
```
```
override fun toString(): String = "Hey"
```
Expression functions should not wrap to two lines. If an expression function grows to require wrapping, use a normal function body, a return declaration, and normal expression wrapping rules instead.

#### Properties
When a property initializer does not fit on a single line, break after the equals sign (=) and use a continuation indent.

```
private val defaultCharset: Charset? =
        EncodingRegistry.getInstance().getDefaultCharsetForPropertiesFiles(file)
```
Properties declaring a get and/or set function should place each on their own line with a normal indent (+4). Format them using the same rules as functions.

```
var directory: File? = null
    set(value) {
        // …
    }
```
Read-only properties can use a shorter syntax which fits on a single line.
```
val defaultExtension: String get() = "kt"
```

## Whitespace
### Vertical
A single blank line appears:

- Between consecutive members of a class: properties, constructors, functions, nested classes, etc.
- - Exception: A blank line between two consecutive properties (having no other code between them) is optional. Such blank lines are used as needed to create logical groupings of properties and associate properties with their backing property, if present.
- - Exception: Blank lines between enum constants are covered below.
- Between statements, as needed to organize the code into logical subsections.
- Optionally before the first statement in a function, before the first member of a class, or after the last member of a class (neither encouraged nor discouraged).
- As required by other sections of this document (such as the Structure section).
Multiple consecutive blank lines are permitted, but not encouraged or ever required.

### Horizontal
Beyond where required by the language or other style rules, and apart from literals, comments, and KDoc, a single ASCII space also appears in the following places only:

- Separating any reserved word, such as if, for, or catch from an open parenthesis (() that follows it on that line.
```
// WRONG!
for(i in 0..1) {
}
```
```
// Okay
for (i in 0..1) {
}
```
- Separating any reserved word, such as else or catch, from a closing curly brace (}) that precedes it on that line.
```
// WRONG!
}else {
}
```
```
// Okay
} else {
}
```
- Before any open curly brace ({).
```
// WRONG!
if (list.isEmpty()){
}
```
```
// Okay
if (list.isEmpty()) {
}
```
- On both sides of any binary operator.
```
// WRONG!
val two = 1+1
```
```
// Okay
val two = 1 + 1
```
This also applies to the following “operator-like” symbols:
- - the arrow in a lambda expression (`->`).
```
// WRONG!
ints.map { value->value.toString() }
```
```
// Okay
ints.map { value -> value.toString() }
```
But not:
- - the two colons (::) of a member reference.
```
// WRONG!
val toString = Any :: toString
```
```// Okay
val toString = Any::toString
```
- - the dot separator (.).
```
// WRONG
it . toString()
```
```
// Okay
it.toString()
```
- - the range operator (`..`).
```
// WRONG
 for (i in 1 .. 4) print(i)
 ```
 ```
 // Okay
 for (i in 1..4) print(i)
 ```
- Before a colon (:) only if used in a class declaration for specifying a base class or interfaces, or when used in a where clause for generic constraints.
```
// WRONG!
class Foo: Runnable
```
```
// Okay
class Foo : Runnable
```
```
// WRONG
fun <T: Comparable> max(a: T, b: T)
```
```
// Okay
fun <T : Comparable> max(a: T, b: T)
```
```
// WRONG
fun <T> max(a: T, b: T) where T: Comparable<T>
```
```
// Okay
fun <T> max(a: T, b: T) where T : Comparable<T>
```
- After a comma (,) or colon (:).
```
// WRONG!
val oneAndTwo = listOf(1,2)
```
```
// Okay
val oneAndTwo = listOf(1, 2)
```
```
// WRONG!
class Foo :Runnable
```
```
// Okay
class Foo : Runnable
```
- On both sides of the double slash (`//`) that begins an end-of-line comment. Here, multiple spaces are allowed, but not required.
```
// WRONG!
var debugging = false//disabled by default
```
```
// Okay
var debugging = false // disabled by default
```
This rule is never interpreted as requiring or forbidding additional space at the start or end of a line; it addresses only interior space.


