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
-- This also applies to the following “operator-like” symbols:
-- The dot separator (.).
-- The two colons of a member reference (::).
- When a line is broken at an assignment operator the break comes after the symbol.
- A method or constructor name stays attached to the open parenthesis (() that follows it.
- A comma (,) stays attached to the token that precedes it.
- A lambda arrow (->) stays attached to the argument list that precedes it.

```
Note: The primary goal for line wrapping is to have clear code, not necessarily code that fits in the smallest number of lines.
```
