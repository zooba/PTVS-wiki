# Code Formatting

**New in PTVS 2.0**

The code formatting feature enables you to quickly reformat either a document of Python code or just a selection to match your preconfigured formatting options. By default the code formatting options are set to match a superset of the [PEP 8 style guide](http://www.python.org/dev/peps/pep-0008/).

You can access the code formatting feature from Edit -> Advanced -> Format Document or Edit -> Advanced -> Format Selection. They are also typically bound to a keyboard shortcut - typically this is bound to Ctrl-K, Ctrl-D for reformat document and Ctrl-K, Ctrl-F for reformat selection.

You can configure formatting options under Tools -> Options-> Text Editor -> Python -> Formatting.

Currently there is one general options page and three high level categories of options for automatic reformatting. The general options page controls when formatting is applied, while the other pages control what formatting is performed.

The various formatting options are broken down into Spacing, Statements, and Wrapping. Spacing controls where spaces are inserted or removed around various language constructs, Statements controls automatic re-writing of various statements into more Pythonic forms, and Wrapping controls automatic wrapping of comments to limit text width.

## Spacing

Spacing options have 3 possible values: On, which ensures that spacing is present. Off, which removes any spacing, and Indeterminate, which leaves the original formatting in place.

## Class Definitions

### Insert space between a class declaration's name and bases list

If checked, a space is added between the name and opening parenthesis of the bases list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
class X (object): pass 
```

Example off:

```python
class X(object): pass 
```

### Insert space within bases list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of a bases list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
class X( object ): pass 
```

Example off:

```python
class X(object): pass
```

### Insert space within empty bases list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of an empty bases list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
class X( ): pass
```

Example off:

```python
class X(): pass
```

## Function Definitions

### Insert space between a function declaration's name and parameter list

If checked, a space is added between the name and opening parenthesis of the parameter list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
def X (): pass
```

Example off:

```python
def X(): pass
```

### Insert space within parameter list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of a parameter list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
def X( a, b ): pass
```

Example off:

```python
def X(a, b): pass
```

### Insert space within empty parameter list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of an empty parameter list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
def X( ): pass
```

Example off:

```python
def X(): pass
```

### Insert spaces around '=' in default parameter values

If checked, a space is added before and after '=' operators in function definitions. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
def X(a = 42): pass
```

Example off:

```python
def X(a=42): pass
```

### Insert space before and after return annotation operators

If checked, a space is added before and after '->' operators in function definitions. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
def X() -> 42: pass
```

Example off:

```python
def X()->42: pass
```

## Operators

### Insert spaces around binary operators

If checked, a space is added before and after binary operators. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
a + b
```

Example off:

```python
a+b
```

### Insert spaces around assignments

If checked, a space is added before and after '=' operators in assignments. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
a = b
```

Example off:

```python
a=b
```

## Expression Spacing

### Insert space between a function call's name and argument list

If checked, a space is added between the name and opening parenthesis of the argument list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
X ()
```

Example off:

```python
X()
```

### Insert space within empty argument list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of an empty argument list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
X( )
```

Example off:

```python
X()
```

### Insert space within argument list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of an argument list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
X( a, b )
```

Example off:

```python
X(a, b)
```

### Insert space within parentheses of expression

If checked, a space is added after the open parenthesis and before the close parenthesis of an expression. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
( a )
```

Example off:

```python
(a)
```

### Insert space within empty tuple parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of an empty tuple. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
( )
```

Example off:

```python
()
```

### Insert space within tuple parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of the tuple. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
( a, b )
```

Example off:

```python
(a, b)
```

### Insert space within empty square brackets

If checked, a space is added between the open square bracket and the close square bracket. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
[ ]
```

Example off:

```python
[]
```

### Insert spaces within square brackets of lists

If checked, a space is added after the open square bracket and before the close square bracket of the list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
[ a, b ]
```

Example off:

```python
[a, b]
```

### Insert space before open square bracket

If checked, a space is added before an open square bracket. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
x [i]
```

Example off:

```python
x[i]
```

### Insert space within square brackets

If checked, a space is added after the open square bracket and before the close square bracket. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

```python
x[ i ]
```

Example off:

```python
x[i]
```

## Statements

### Place imported modules on new line

If checked, import statements with multiple modules are separated onto individual lines. If unchecked, import statements with multiple modules are not modified.

Before:

```python
import sys, pickle
```

After:

```python
import sys
import pickle
```

### Remove unnecessary semicolons

If checked, semicolons at the end of lines will be removed. If unchecked, unnecessary semicolons are not modified.

Before:

```python
x = 42;
```

After:

```python
x = 42
```

### Place multiple statements on new lines

If checked, statements separated by semicolons are moved onto individual lines. If unchecked, lines with multiple statements are not modified.

Before:

```python
x = 42; y = 100
```

After:

```python
x = 42
y = 100
```

## Wrapping

### Wrap comments that are too wide

If checked, comments are wrapped to the specified width. If unchecked, comments are not modified.

Wrapped to 40 columns:

```python
# There should be one-- and preferably
# only one --obvious way to do it.
```

Not wrapped:

```python
# There should be one-- and preferably only one --obvious way to do it.
```

### Maximum comment width

The number of the last column that should include comment text. Words after this column are moved to the following line.

### Fill Comment paragraph 

This command will reflow comment text and format it:

```python
# foo 
# bar
# baz
```

changes to:

```python
# foo bar baz
```

and turns:

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

into:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```

 
