# Contents
## Source Files
All source files must be encoded as UTF-8.

## Naming
If a source file contains only a single top-level class, the file name should reflect the case-sensitive name plus the .kt extension. Otherwise, if a source file contains multiple top-level declarations, choose a name that describes the contents of the file, apply PascalCase, and append the .kt extension.

```kotlin 
// MyClass.kt
class MyClass { }
```

```kotlin
// Bar.kt
class Bar { }
fun Runnable.toBar(): Bar = // …
```

```kotlin
// Map.kt
fun <T, O> Set<T>.map(func: (T) -> O): List<O> = // …
fun <T, O> List<T>.map(func: (T) -> O): List<O> = // …
```

## Special Characters
### Whitespace characters
Aside from the line terminator sequence, the ASCII horizontal space character (0x20) is the only whitespace character that appears anywhere in a source file. This implies that:

- All other whitespace characters in string and character literals are escaped.
- Tab characters are not used for indentation.

### Special escape sequences
For any character that has a special escape sequence (\b, \n, \r, \t, \', \", \\, and \$), that sequence is used rather than the corresponding Unicode (e.g., \u000a) escape.

### Non-ASCII characters
For the remaining non-ASCII characters, either the actual Unicode character (e.g., ∞) or the equivalent Unicode escape (e.g., \u221e) is used. The choice depends only on which makes the code easier to read and understand. Unicode escapes are discouraged for printable characters at any location and are strongly discouraged outside of string literals and comments.

```
Example	Discussion
val unitAbbrev = "μs"	            Best: perfectly clear even without a comment.
val unitAbbrev = "\u03bcs" // μs	Poor: there’s no reason to use an escape with a printable character.
val unitAbbrev = "\u03bcs"`	      Poor: the reader has no idea what this is.
return "\ufeff" + content	        Good: use escapes for non-printable characters, and comment if necessary.
```

## Structure
A .kt file comprises the following, in order:

- Copyright and/or license header (optional)
- File-level annotations
- Package statement
- Import statements
- Top-level declarations

Exactly one blank line separates each of these sections.

### Copyright / License
If a copyright or license header belongs in the file it should be placed at the immediate top in a multi-line comment.
```kotlin
/*
 * Copyright 2017 Google, Inc.
 *
 * ...
 */
```
Do not use a KDoc-style or single-line-style comment.
```kotlin
/**
 * Copyright 2017 Google, Inc.
 *
 * ...
 */
```

```kotlin
// Copyright 2017 Google, Inc.
//
// ...
```
### File-level annotations
Annotations with the "file" use-site target are placed between any header comment and the package declaration.

### Package statement
The package statement is not subject to any column limit and is never line-wrapped.

### Import statements
Import statements for classes, functions, and properties are grouped together in a single list and ASCII sorted.

Wildcard imports (of any type) are not allowed.

Similar to the package statement, import statements are not subject to a column limit and they are never line-wrapped.

### Top-level declarations
A .kt file can declare one or more types, functions, properties, or type aliases at the top-level.

The contents of a file should be focused on a single theme. Examples of this would be a single public type or a set of extension functions performing the same operation on multiple receiver types. Unrelated declarations should be separated into their own files and public declarations within a single file should be minimized.

No explicit restriction is placed on the number nor order of the contents of a file.

Source files are usually read from top-to-bottom meaning that the order, in general, should reflect that the declarations higher up will inform understanding of those farther down. Different files may choose to order their contents differently. Similarly, one file may contain 100 properties, another 10 functions, and yet another a single class.

What is important is that each class uses some logical order, which its maintainer could explain if asked. For example, new functions are not just habitually added to the end of the class, as that would yield “chronological by date added” ordering, which is not a logical ordering.

### Class member ordering
The order of members within a class follow the same rules as the top-level declarations.
