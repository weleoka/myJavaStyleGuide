[[toc]]

# Introduction
This is a style guide for collaboratory projects. A style guide provides a map so that the code written by a group of programmers will be consistent and, therefore, easier to read and maintain. Many people do not like working according to the style guide offered by Sun. This document is one alternative. This style guide is derived with the guidance of the following [JavaRanch Style guide](https://www.javaranch.com/styleLong.jsp) however it has been updated following discussion about some of its rules.

The rules requirements have changed, and in part due to the default formatting options of the most prevailent IDE's for Java. The in column vertically arranged braces is phased out in favour of more compact code but arguably with even better redability. The setback is slightly more difficult cut and paste operations, but that is mitigated by the better auto-formatting of the modern IDE's.

If changes should be made to this guide or if the reader is in dissagreement with any of this point, or find them lacking then appriciation is to share your thoughts!

#### Some points to discuss, and style details that are not covered here:

* Docstring/javadoc standards could be included
* Singleton methods decleration point in class.
* Exceptions to camelCasingNames. lowerCamelCase UpperCamelCase.
    - userID // OK!!
    - CSVWriter or cSVWriter // ??
    - All capital letters for constants.
* Multiline method calls and method chaining rules.
* Labels on iterative control statements. 
    - Should the label be on its own line?
    - When to label?




## 1 - Formatting

### 1.1 - Indentation
All indenting is done with spaces, not tabs. All indents are four spaces.

Reasoning: All programs work well with spaces. Most programs will mix tabs and spaces so that some lines are indented with spaces and some with tabs. If your tabbing is set to 4 and you share a file with someone that has tabbing set to 8, everything comes out goofy.

The braces do not have to line up vertically in the same column as it makes the code too spaced out and is difficult for redability. Especially iterative statements and selective statements can be exempt from the rule, but also method declarations can have a trailing brace on the same line.

Old rule: (Matching braces always line up vertically in the same column as their construct.)

Example:

```java
void foo() {
    
    while (bar > 0) {
        System.out.println();
        bar--;
    }

    if (oatmeal == tasty) {
        System.out.println("Oatmeal is good and good for you");
    }

    else if (oatmeal == yak) {
        System.out.println("Oatmeal tastes like sawdust");
    }

    else {
        System.out.println("tell me pleeze what iz dis 'oatmeal'");
    }

    switch (suckFactor) {
        case 1:
            System.out.println("This sucks");
            break;
        case 2:
            System.out.println("This really sucks");
            break;
        case 3:
            System.out.println("This seriously sucks");
            break;
        default:
            System.out.println("whatever");
            break;
    }
}
```
All if, while and for statements must use braces even if they control just one statement. This still stands.

Reasoning: Consistency is easier to read. Plus, less editing is involved if lines of code are added or removed.

```java
if (superHero == theTick) System.out.println("Spoon!");  // NO!

if (superHero == theTick)
    System.out.println("Spoon!");  // NO!

if (superHero == theTick)                   
{
    System.out.println("Spoon!");
}                                            // NO! (changed from YES!)

if (superHero == theTick) {
    System.out.println("Spoon!");
}                                            // YES! ( changed from NO!)
```
In the case of multiline assignments it follows the same rule. Example:

```java
String[] tmpArr = {
    this.name,
    this.id,
    this.status.toString()
};
```

### 1.2 - Spacing
All method names should be immediately followed by a left parenthesis.

```java
foo (i, j); // NO!
foo(i, j);  // YES!
```

All array dereferences should be immediately followed by a left square bracket.

```java
args [0];  // NO!
args[0];   // YES!
```

Binary operators should have a space on either side.

```java
a=b+c;          // NO!
a = b+c;        // NO!
a=b + c;        // NO!
a = b + c;      // YES!

z = 2*x + 3*y;         // NO!
z = 2 * x + 3 * y;     // YES!
z = (2 * x) + (3 * y); // YES!'
```

Unary operators should be immediately preceded or followed by their operand.

```java
count ++; // NO!
count++;  // YES!
 
i --;     // NO!
i--;      // YES!
```
 
Commas and semicolons are always followed by whitespace.

```java
 for (int i = 0;i < 10;i++)   // NO!
 for (int i = 0; i < 10; i++) // YES!

 getPancakes(syrupQuantity,butterQuantity);  // NO!
 getPancakes(syrupQuantity, butterQuantity); // YES!
```

All casts should be written with no spaces.

```java
(MyClass) v.get(3);  // NO!
( MyClass )v.get(3); // NO!
(MyClass)v.get(3);   // YES!
```

The keywords if, while, for, switch, and catch must be followed by a space.

```java
if(hungry)  // NO!
if (hungry) // YES!

while(pancakes < 7)  // NO!
while (pancakes < 7) // YES!

for(int i = 0; i < 10; i++)  // NO!
for (int i = 0; i < 10; i++) // YES!

catch(TooManyPancakesException e)  // NO!
catch (TooManyPancakesException e) // YES!
```

Method/function arguments lists or parameters lists have now leading or trailing whitespace.

```java
public myMethod( int myInt, int theirInt ) {...}  // NO!
public myMethod(int myInt, int theirInt) {...}  // YES!
```

### 1.3 - Class Member Ordering

```java
class Order
{
    // fields (attributes)

    // constructors

    // methods
}
```
### 1.4 - Maximum Line Length
Avoid making lines longer than 120 characters. If your code starts to get indented way to the right, consider breaking your code into more methods.

Reasoning: Editors and printing facilities used by most programmers can easily handle 120 characters. Longer lines can be frustrating to work with.

### 1.5 - Parentheses
Parentheses should be used in expressions not only to specify order of precedence, but also to help simplify the expression. When in doubt, parenthesize. 

### 1.6 - Blank line preceeding
Statements for, if, while, case, else, else if, try, catch should ideally be preceeded by a blank line. This is not essentially required of this style guide but is recommended for redability.

The continue, break and return statements are less requiring of a blank line preceeding.


### 1.7- Newline before closing brace

* No line break before the opening brace.
* Line break after the opening brace.
* Line break before the closing brace.
* Line break after the closing brace, only if that brace terminates a statement or terminates the body of a method, constructor, or named class. For example, there is no line break after the brace if it is followed by else or a comma. 

Example:

```java
return new MyClass() {
  @Override public void method() {
    if (condition()) {
      try {
        something();
      } catch (ProblemException e) {
        recover();
      }
    } else if (otherCondition()) {
      somethingElse();
    } else {
      lastThing();
    }
  }
};
```


## 2 - Identifiers
All identifiers use letters ('A' through 'Z' and 'a' through 'z') and numbers ('0' through '9') only. No underscores, dollar signs or non-ascii characters.

### 2.1 - Classes and Interfaces
All class and interface identifiers will use mixed case. The first letter of each word in the name will be uppercase, including the first letter of the name. All other letters will be in lowercase, except in the case of an acronym, which will be all upper case.

Examples:

    Customer
    SalesOrder
    TargetURL
    URLTarget

### 2.2 - Packages
Package names will use lower case characters only. Try to keep the length under eight (8) characters. Multi-word package names should be avoided.

Examples:

    common
    core
    lang

### 2.3 - All Other Identifiers
All other identifiers, including (but not limited to) fields, local variables, methods and parameters, will use the following naming convention. This includes identifiers for constants.

Reasoning: Using all upper case, as traditionally done in C, is a violation of OO abstraction. For example, a variable which starts out as a constant may be refactored later to not be a constant.
The first letter of each word in the name will be uppercase, except for the first letter of the name. All other letters will be in lowercase, except in the case of an embedded acronym, which will be all uppercase. Leading acronyms are all lower case.

Examples:

    customer
    salesOrder
    addToTotal()
    targetURL
    urlTarget


#### 2.3.1 Hungarian Notation and Scope Identification
Hungarian notation and scope identification are not allowed.

Reasoning: Hungarian Notation, which specifies type as part of the identifier, violates OO abstraction. Scope identification specifies scope as part of the identifier, which also violates OO abstraction.

```java
public class Person 
{
    private String sFirstName; // NO! (Hungarian notation: s for String)
    private String firstName;  // YES!

    private String mLastName;  // NO! (Scope identification: m for member variable)
    private String _lastName;  // NO! (Scope identification: _ for member variable)
    private String lastName;   // YES!

    // ...
}
```

#### 2.3.2 Test Code
Test code is permitted to use underscores in identifiers for methods and fields.

Code for testing other code often needs to be able to refer to existing identifiers, but also be able to append other qualifiers to the name. This is easier to read if an additional delimiter is allowed.

Example:
Code to test a method double eatSomePie(double amount) may use variables such as:

```java
eatSomePie_count
eatSomePie_amount
eatSomePie_return
eatSomePie_exception
```



## 3 - Coding

### 3.1 - Constructs to Avoid
  

#### 3.1.1 - Never use do..while
Do not use do..while loops.

Reasoning: Consider that the programmer looking at your code is probably examining each method starting at the top and working down. When encountering a loop, the first thing the programmer wants to know is what terminates the loop. If you have that logic at the bottom, it is harder to read. Further, many less experienced programmers are not familiar with do..while, but may be required to modify your code.
So rather than:

```java
boolean done = false;
do
{
    ...
} while (!done)
```
use:

```java
boolean done = false;
while (!done)
{
   ...
}
```

#### 3.1.2 - Never use return in the middle of a method (changed)
This rule has ben discussed and currently some exceptions are thought to excist, where in fact it would be highly meritable for code readability and to have multiple return statements and higher up in the method than at the end. 

Old rule:

    return is to be used at the end of a method only.
    Reasoning: Using return in the middle of a method makes it difficult to later break the method into smaller methods. It also forces the developer to consider more than one exit point to a method.


#### 3.1.3 - Never use continue (changed)
This rule has been discussed and it has been decided that if the construct is very small (for example a for loop spanning up to 10 SLOC) then to use continue can be an acceptable way of advancing to the next iteration with the intention of not having to perform remaining logic in the construct and waste time doing that. Efforts should be made to avoid continue when possible.

Old rule:

    Reasoning: Using continue makes it difficult to later break the construct into smaller constructs or methods. It also forces the developer to consider more than one end point for a construct.


#### 3.1.4 - Never use break other than in a switch statement (changed)
This rule has been discussed and it has been decided that if the construct is very small (for example a for loop spanning up to 10 SLOC) then to use continue can be an acceptable way of advancing to the next iteration with the intention of not having to perform remaining logic in the construct and waste time doing that. Efforts should be made to avoid continue when possible.

Old rule:

    Reasoning: Using break, other than for switch statement control, makes it difficult to later break a construct into smaller constructs or methods. It also forces the developer to consider more than one end point for a construct.


### 3.2 - Do Not Compound Increment or Decrement Operators
Use a separate line for an increment or decrement.

Reasoning: Compounding increment or decrement operators into method calls or math is not clear to less experienced programmers who may be required to modify your code.

Examples:

```java
foo(x++); // NO!
foo(x);   // YES!
x++;


y += 100 * x++;  // NO!
y += 100 * x;    // YES!
x++;
```

Note: `i++` and `++i` are equally fast, and `i++` seems more consistent with the rest of the language. Since the above prevents any use of a case where `++i` could make a difference, never use pre- increment/decrement.

### 3.3 - Initialization
Declare variables as close as possible to where they are used.

Examples:

```java
int totalWide;
int firstWide = 20;
int secondWide = 12;
firstWide = doFoo(firstWide, secondWide);
doBar(firstWide, secondWide);
totalWide = firstWide + secondWide;         //  wrong!

int firstWide = 20;
int secondWide = 12;
firstWide = doFoo(firstWide, secondWide);
doBar(firstWide, secondWide);
int totalWide = firstWide + secondWide;     //  right!

int secondWide = 12;
int firstWide = doFoo(20, secondWide);
doBar(firstWide, secondWide);
int totalWide = firstWide + secondWide;     //  even better!
```

### 3.4 - Access
All fields must be private, except for some constants. 




## 4 - Self-Documenting Code

"Any fool can write code that a computer can understand.
Good programmers write code that humans can understand."  
-- Martin Fowler, Refactoring: Improving the Design of Existing Code

Rather than trying to document how you perform a complex algorithm, try to make the algorithm easier to read by introducing more identifiers. This helps in the future in case the algorithm changes but someone forgets to change the documentation.

So for example instead of:

```java
if ( (hero == theTick) && ( (sidekick == arthur) || (sidekick == speak) ) )
```
Use:

```java
boolean isTickSidekick = ( (sidekick == arthur) || (sidekick == speak) );
if ( (hero == theTick) && isTickSidekick )
```
Or, instead of:

```java
public static void happyBirthday(int age)
{
    // If you're in the US, some birthdays are special:
    // 16 (sweet sixteen)
    // 21 (age of majority)
    // 25, 50, 75 (quarter centuries)
    // 30, 40, 50, ... etc (decades)
    if ((age == 16) || (age == 21) || ((age > 21) && (((age % 10) == 0) || ((age % 25) == 0))))
    {
        System.out.println("Super special party, this year!");
    }
    else
    {
        System.out.println("One year older. Again.");
    }
}
```

Use:

```java
public static void happyBirthday(int age)
{
    boolean sweet_sixteen = (age == 16);
    boolean majority = (age == 21);
    boolean adult = (age > 21);
    boolean decade = (age % 10) == 0;
    boolean quarter = (age % 25) == 0;

    if (sweet_sixteen || majority || (adult && (decade || quarter)))
    {
        System.out.println("Super special party, this year!");
    }
    else
    {
        System.out.println("One year older. Again.");
    }
}
```




## 5 - Commenting and docstrings

### 5.1 - Inline comments

Inline comment specifications:

- Finish with full stop. 
- Begin with uppercase letter.
- One to 4 spaces before commencing comment. Unless many comments in which case they should all line up on the same column for better redability.
- Before subject codeline or inline subject codeline.
