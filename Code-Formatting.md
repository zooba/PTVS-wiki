# Code Formatting

**New in PTVS 2.0**

The code formatting feature enables you to quickly reformat either a document of Python code or just a selection to match your preconfigured formatting options. By default the code formatting options are set to match a superset of the [PEP 8 style guide](http://www.python.org/dev/peps/pep-0008/).

You can access the code formatting feature from Edit->Advanced->Format Document or Edit->Advanced->Format Selection. They are also typically bound to a keyboard shortcut – typically this is bound to Ctrl-K Ctrl-D for reformat document and Ctrl-K Ctrl-F for reformat selection.

You can configure the formatting options in Tools->Options->Text Editor->Python->Formatting.

Currently there is one general options page and 3 high level buckets of options related to automatic reformatting. The general options page has options as to when formatting is applied. The other pages have options related to what formatting is performed when formatting is applied.

The various formatting options are broken down into spacing, statements, and wrapping. The spacing page covers where spaces are inserted around various language constructs. The statements page covers automatic re-writing of various statements into more Pythonic forms. And finally the Wrapping page configures how automatic wrapping of comments occurs to enforce a limited width.

## Spacing

The spacing options have 3 possible values: On, which ensures that spacing is present. Off, which removes the extra spaces, and indeterminate which leaves the original formatting in place.

 

## Class Definitions

### Insert space between a class declaration's name and bases list

If checked, a space is added between the name and opening parenthesis of the bases list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	class X (object): pass 

Example off:

	class X(object): pass 

### Insert space within bases list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of a bases list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	class X( object ): pass 

Example off:

	class X(object): pass

### Insert space within empty bases list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of an empty bases list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	class X( ): pass

Example off:

	class X(): pass

## Function Definitions

### Insert space between a function declaration's name and parameter list

If checked, a space is added between the name and opening parenthesis of the parameter list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	def X (): pass

Example off:

	def X(): pass

### Insert space within parameter list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of a parameter list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	def X( a, b ): pass

Example off:

	def X(a, b): pass

### Insert space within empty parameter list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of an empty parameter list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	def X( ): pass

Example off:

	def X(): pass

### Insert spaces around '=' in default parameter values

If checked, a space is added before and after '=' operators in function definitions. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	def X(a = 42): pass

Example off:

	def X(a=42): pass

### Insert space before and after return annotation operators

If checked, a space is added before and after '->' operators in function definitions. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	def X() -> 42: pass

Example off:

	def X()->42: pass

## Operators

### Insert spaces around binary operators

If checked, a space is added before and after binary operators. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	a + b

Example off:

	a+b

### Insert spaces around assignments

If checked, a space is added before and after '=' operators in assignments. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	a = b

Example off:

	a=b

## Expression Spacing

### Insert space between a function call's name and argument list

If checked, a space is added between the name and opening parenthesis of the argument list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	X ()

Example off:

	X()

### Insert space within empty argument list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of an empty argument list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	X( )	

Example off:

	X()

### Insert space within argument list parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of an argument list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	X( a, b )

Example off:

	X(a, b)

### Insert space within parentheses of expression

If checked, a space is added after the open parenthesis and before the close parenthesis of an expression. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	( a )

Example off:

	(a)

### Insert space within empty tuple parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of an empty tuple. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	( )

Example off:

	()

### Insert space within tuple parentheses

If checked, a space is added after the open parenthesis and before the close parenthesis of the tuple. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	( a, b )

Example off:

	(a, b)

### Insert space within empty square brackets

If checked, a space is added between the open square bracket and the close square bracket. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	[ ]

Example off:

	[]

### Insert spaces within square brackets of lists

If checked, a space is added after the open square bracket and before the close square bracket of the list. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	[ a, b ]

Example off:

	[a, b]

### Insert space before open square bracket

If checked, a space is added before an open square bracket. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	x [i]

Example off:

	x[i]

### Insert space within square brackets

If checked, a space is added after the open square bracket and before the close square bracket. If unchecked, spaces are removed. Otherwise, spaces are not modified.

Example on:

	x[ i ]

Example off:

	x[i]

## Statements

### Place imported modules on new line

If checked, import statements with multiple modules are separated onto individual lines. If unchecked, import statements with multiple modules are not modified.

Before:

	import sys, pickle

After:

	import sys

	import pickle

### Remove unnecessary semicolons

If checked, semicolons at the end of lines will be removed. If unchecked, unnecessary semicolons are not modified.

Before:

	x = 42;

After:

	x = 42

### Place multiple statements on new lines

If checked, statements separated by semicolons are moved onto individual lines. If unchecked, lines with multiple statements are not modified.

Before:

	x = 42; y = 100

After:

	x = 42
	
	y = 100

## Wrapping

### Wrap comments that are too wide

If checked, comments are wrapped to the specified width. If unchecked, comments are not modified.

Wrapped to 40 columns:

	# There should be one-- and preferably
	# only one --obvious way to do it.

Not wrapped:

	# There should be one-- and preferably only one --obvious way to do it.

### Maximum comment width

The number of the last column that should include comment text. Words after this column are moved to the following line.

### Fill Comment paragraph 

This command will reflow comment text and format it:

	# foo 
	 # bar
	 # baz

changes to:

	# foo bar baz

and turns:

	# This is a very long long long long long long long long long long long long long long long long long long long comment

into:

	# This is a very long long long long long long long long long long long long
 	# long long long long long long long comment

 
