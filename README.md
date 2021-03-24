<h1 align="center"> Android Kotlin Style Guide </h1>


# Inspiration

This style-guide is somewhat of a mash-up between the existing Kotlin language style guides. The language guidance is drawn from: 

- [Android Kotlin style guide](https://android.github.io/kotlin-guides/style.html)
- [Kotlin Coding Conventions](https://kotlinlang.org/docs/reference/coding-conventions.html)
- [Google Java Style Guide](https://google-styleguide.googlecode.com/svn/trunk/javaguide.html).
- [Ribot's Android Guidelines](https://github.com/ribot/android-guidelines)
- [Ray Wenderlich's Kotlin Style Guide](https://github.com/raywenderlich/kotlin-style-guide)
- [Adam Bennett's Kotlin Style Guide](https://github.com/ditn/KotlinStyleGuide)


# Android Studio Coding Style

It is possible to get Android Studio to adhere to these style guidelines, via a rather complex sequence of menus. To make it easier, we've provided a coding style that can be imported into Android Studio.

The file can be found [here](settings.zip).

To use these settings:
 - If you have a project opened, go to **File > Manage IDE Settings > Import Settings** and then select this zip file.
 - If you are on the select project dialogue, go to **Configue > Import Settings** and then select this zip file.


# Recommended Plugins for Android Studio

| Plugins                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------- |
| [Android Parcelable Code Generator](https://plugins.jetbrains.com/plugin/16132-android-parcelable-code-generator) |
| [Atom Material Icons](https://plugins.jetbrains.com/plugin/10044-atom-material-icons)                             |
| [CodeGlance](https://plugins.jetbrains.com/plugin/7275-codeglance)                                                |
| [.ignore](https://plugins.jetbrains.com/plugin/7495--ignore)                                                      |
| [Markdown](https://plugins.jetbrains.com/plugin/7793-markdown)                                                    |
| [Material Color Palette](https://plugins.jetbrains.com/plugin/8590-material-color-palette)                        |
| [One Dark Theme](https://plugins.jetbrains.com/plugin/11938-one-dark-theme)                                       |
| [Rainbow Brackets](https://plugins.jetbrains.com/plugin/10080-rainbow-brackets)                                   |
| [String Manipulation](https://plugins.jetbrains.com/plugin/2162-string-manipulation)                              |


# Table of Contents

- [Inspiration](#inspiration)
- [Android Studio Coding Style](#android-studio-coding-style)
- [Recommended Plugins for Android Studio](#recommended-plugins-for-android-studio)
- [Table of Contents](#table-of-contents)
- [File Naming](#file-naming)
  - [Packages](#packages)
  - [Classes & Interfaces](#classes--interfaces)
  - [Methods](#methods)
  - [Fields](#fields)
  - [Variables & Parameters](#variables--parameters)
  - [Resources Files](#resources-files)
    - [Drawable Files](#drawable-files)
    - [Layout Files](#layout-files)
    - [Menu Files](#menu-files)
    - [Values Files](#values-files)
- [Code Guidelines](#code-guidelines)
  - [Language](#language)
  - [Kotlin Language Rules](#kotlin-language-rules)
    - [Declaration](#declaration)
      - [Fields Definition and Naming](#fields-definition-and-naming)
      - [Classes](#classes)
      - [Constructors](#constructors)
      - [Data Type Objects](#data-type-objects)
      - [Getters & Setters](#getters--setters)
      - [Enum Classes](#enum-classes)
    - [Treat Acronyms as Words](#treat-acronyms-as-words)
    - [Comments](#comments)
    - [Semicolons](#semicolons)
    - [Indentation](#indentation)
      - [Blocks](#blocks)
      - [Vertical Spacing](#vertical-spacing)
      - [Line Length](#line-length)
      - [Line Wraps](#line-wraps)
      - [Line-Wrapping Strategies](#line-wrapping-strategies)
      - [Brace Style](#brace-style)
    - [Don't Ignore Exceptions](#dont-ignore-exceptions)
    - [Don't Catch Generic Exception](#dont-catch-generic-exception)
    - [Don't Use Finalizers](#dont-use-finalizers)
    - [Fully Qualify Imports](#fully-qualify-imports)
    - [When Statements](#when-statements)
    - [Type Inference](#type-inference)
    - [Companion Objects](#companion-objects)
    - [Constants vs. Variables](#constants-vs-variables)
    - [Nullable Types](#nullable-types)
    - [Limit Variable Scope](#limit-variable-scope)
    - [Visibility Modifiers](#visibility-modifiers)
    - [Access Level Modifiers](#access-level-modifiers)
    - [Logging guidelines](#logging-guidelines)
    - [Class Member Ordering](#class-member-ordering)
    - [Parameter Ordering in Methods](#parameter-ordering-in-methods)
    - [String Constants, Naming, and Values](#string-constants-naming-and-values)
    - [Arguments in Fragments and Activities](#arguments-in-fragments-and-activities)
  - [XML Style Rules](#xml-style-rules)
    - [Use Self Closing Tags](#use-self-closing-tags)
    - [Resources Naming](#resources-naming)
      - [ID naming](#id-naming)
      - [Strings](#strings)
      - [Styles and Themes](#styles-and-themes)
    - [Attributes Ordering](#attributes-ordering)


# File Naming

On the whole, naming should follow Java standards, as Kotlin is a JVM-compatible language.


## Packages

Package names are similar to Java: all __lower-case__, multiple words concatenated together, without hypens or underscores:

__BAD__:

```kotlin
com.Krayong.funky_widget
```

__GOOD__:

```kotlin
com.krayong.funkywidget
```


## Classes & Interfaces

Class names are written in __UpperCamelCase__.

For classes that extend an Android component, the name of the class should end with the name of the component.

Examples: `SignInActivity`, `SignInFragment`, `ImageUploaderService`, `ChangePasswordDialog`. 


## Methods

Methods are written in __lowerCamelCase__. 

Examples: `setValue`, `assignUser`.


## Fields

Generally, written in __lowerCamelCase__. Fields should **not** be named with Hungarian notation, as Hungarian notation is [erroneously thought](http://jakewharton.com/just-say-no-to-hungarian-notation/) to be recommended by Google.

Example field names:

```kotlin
class MyClass {
  var publicField: Int = 0
  val person = Person()
  private var privateField: Int?
}
```

Constant values in the companion object should be written in __uppercase__, with an underscore separating words:

```kotlin
companion object {
  const val THE_ANSWER = 42
}
```


## Variables & Parameters

Written in __lowerCamelCase__.

Single character values must be avoided, except for temporary looping variables.


## Resources Files

Resources file names are written in __lowercase_underscore__.


### Drawable Files

Naming conventions for drawables:


| Asset Type   | Prefix          | Example                    |
| ------------ | --------------- | -------------------------- |
| Action bar   | `ab_`           | `ab_stacked.9.png`         |
| Button       | `btn_`          | `btn_send_pressed.9.png`   |
| Dialog       | `dialog_`       | `dialog_top.9.png`         |
| Divider      | `divider_`      | `divider_horizontal.9.png` |
| Icon         | `ic_`           | `ic_star.png`              |
| Menu         | `menu_	`        | `menu_submenu_bg.9.png`    |
| Notification | `notification_` | `notification_bg.9.png`    |
| Tabs         | `tab_`          | `tab_pressed.9.png`        |

Naming conventions for icons (taken from [Android iconography guidelines](http://developer.android.com/design/style/iconography.html)):

| Asset Type                      | Prefix           | Example                    |
| ------------------------------- | ---------------- | -------------------------- |
| Icons                           | `ic_`            | `ic_star.png`              |
| Launcher icons                  | `ic_launcher`    | `ic_launcher_calendar.png` |
| Menu icons and Action Bar icons | `ic_menu`        | `ic_menu_archive.png`      |
| Status bar icons                | `ic_stat_notify` | `ic_stat_notify_msg.png`   |
| Tab icons                       | `ic_tab`         | `ic_tab_recent.png`        |
| Dialog icons                    | `ic_dialog`      | `ic_dialog_info.png`       |

Naming conventions for selector states:

| State    | Suffix      | Example                    |
| -------- | ----------- | -------------------------- |
| Normal   | `_normal`   | `btn_order_normal.9.png`   |
| Pressed  | `_pressed`  | `btn_order_pressed.9.png`  |
| Focused  | `_focused`  | `btn_order_focused.9.png`  |
| Disabled | `_disabled` | `btn_order_disabled.9.png` |
| Selected | `_selected` | `btn_order_selected.9.png` |


### Layout Files

Layout files should match the name of the Android components that they are intended for but moving the top level component name to the beginning. For example, if we are creating a layout for the `SignInActivity`, the name of the layout file should be `activity_sign_in.xml`.

| Component        | Class Name             | Layout Name                  |
| ---------------- | ---------------------- | ---------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`  |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`       |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml` |
| AdapterView item | ---                    | `item_person.xml`            |
| Partial layout   | ---                    | `partial_stats_bar.xml`      |

A slightly different case is when we are creating a layout that is going to be inflated by an `Adapter`, e.g to populate a `ListView`. In this case, the name of the layout should start with `item_`.

Note that there are cases where these rules will not be possible to apply. For example, when creating layout files that are intended to be part of other layouts. In this case you should use the prefix `partial_`.


### Menu Files

Similar to layout files, menu files should match the name of the component. For example, if we are defining a menu file that is going to be used in the `UserActivity`, then the name of the file should be `activity_user.xml`

A good practice is to not include the word `menu` as part of the name because these files are already located in the `menu` directory.


### Values Files

Resource files in the values folder should be __plural__, e.g. `strings.xml`, `styles.xml`, `colors.xml`, `dimens.xml`, `attrs.xml`


# Code Guidelines


## Language

Use `en-US` English spelling.

__BAD:__

```kotlin
val colourName = "red"
```

__GOOD:__

```kotlin
val colorName = "red"
```


## Kotlin Language Rules


### Declaration


#### Fields Definition and Naming

Fields should be defined at the __top of the file__.

Example:

```kotlin
class MyClass {
    public var publicVariable: Int?			    // same as public int variable in java
    var packagePrivate: Int?					// same as int variable in java
    private var privateVariable: Int?    	    // same as private int variable in java
    protected var protectedVariable: Int?	    // same as protected int variable in java
    
    companion object {
    	public const val SOME_CONSTANT = 42 	// same as public static final int variable in java
    }
}
```

Prefer single declaration per line.

__BAD:__
```kotlin
var username:String?; var twitterHandle: String?
```

__GOOD:__

```kotlin
var username: String?
var twitterHandle: String?
```


#### Classes

Exactly one class per source file, although inner classes are encouraged where scoping appropriate.


#### Constructors

Initialize the properties of a class via primary constructor parameters instead of using an init block.

__BAD:__

```kotlin
class Person(firstName: String, lastName: String, age: Int) {
    val firstName: String
    val lastName: String
    var age: Int

    init {
        this.firstName = firstName
        this.lastName = lastName
        this.age = age
    }

    // ...
}
```

__GOOD:__

```kotlin
class Person(val firstName: String, val lastName: String, var age: Int) {
    // ...
}
```

For formatting these primary constructors, follow the Kotlin coding conventions:

>Classes with longer headers should be formatted so that each primary constructor argument is in a separate line with indentation. Also, the closing parenthesis should be on a new line. If we use inheritance, then the superclass constructor call or list of implemented interfaces should be located on the same line as the parenthesis.
>
>For multiple interfaces, the superclass constructor call should be located first and then each interface should be located in a different line:

```kotlin
class Person(
    id: Int,
    name: String,
    surname: String
) : Human(id, name),
    KotlinMaker {
    // ...
}
```


#### Data Type Objects

Prefer data classes for simple data holding objects.

__BAD:__

```kotlin
class Person(val name: String) {
    override fun toString() : String {
        return "Person(name=$name)"
    }
}
```

__GOOD:__

```kotlin
data class Person(val name: String)
```


#### Getters & Setters

Unlike Java, direct access to fields in Kotlin is preferred. 

If custom getters and setters are required, they should be declared [following Kotlin conventions](https://kotlinlang.org/docs/reference/properties.html) rather than as separate methods.


#### Enum Classes

Enum classes without methods may be formatted without line-breaks, as follows:

```kotlin
private enum CompassDirection { EAST, NORTH, WEST, SOUTH }
```


### Treat Acronyms as Words

| Good             | Bad              |
| ---------------- | ---------------- |
| `XmlHttpRequest` | `XMLHTTPRequest` |
| `getCustomerId`  | `getCustomerID`  |
| `url: String?`   | `URL: String?`   |
| `findPostById`   | `findPostByID`   |


### Comments

When they are needed, use comments to explain **why** a particular piece of code does something. Comments must be kept up-to-date or deleted.

Avoid block comments inline with code, as the code should be as self-documenting as possible. *Exception: This does not apply to those comments used to generate documentation.*


### Semicolons

Semicolons ~~are dead to us~~ should be avoided wherever possible in Kotlin. 

__BAD__:

```kotlin
val horseGiftedByTrojans = true;
if (horseGiftedByTrojans) {
  bringHorseIntoWalledCity();
}
```

__GOOD__:

```kotlin
val horseGiftedByTrojans = true
if (horseGiftedByTrojans) {
    bringHorseIntoWalledCity()
}
```


### Indentation

Indentation is always using tabs - never spaces (__NEVER__). [We are with Richard on this](https://www.youtube.com/watch?v=SsoOG6ZeyUI&ab_channel=freakpants).


#### Blocks

Indentation for blocks uses 1 tab:

__BAD:__

```kotlin
for (i in 0..9) {
  Log.i(TAG, "index=" + i) // 2 spaces
}
```

```kotlin
for (i in 0..9) {
    Log.i(TAG, "index=" + i) // 4 spaces
}
```

__GOOD:__

```kotlin
for (i in 0..9) {
    Log.i(TAG, "index=" + i) // 1 tab 😃
}
```


#### Vertical Spacing

There should be exactly two blank lines between methods to aid in visual clarity and organization. Whitespace within methods should separate functionality, but having too many sections in a method often means you should refactor into several methods.


#### Line Length

Code lines should not exceed __100 characters__. If the line is longer than this limit there are usually two options to reduce its length:

* Extract a local variable or method (preferable).
* Apply line-wrapping to divide a single line into multiple ones.

There are two __exceptions__ where it is possible to have lines longer than 100:

* Lines that are not possible to split, e.g. long URLs in comments.
* `package` and `import` statements.


#### Line Wraps

Indentation for line wraps should use 2 tabs (not the default 1):

__BAD:__

```kotlin
val widget: CoolUiWidget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line)
```

__GOOD:__

```kotlin
val widget: CoolUiWidget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line)
```


#### Line-Wrapping Strategies

There isn't an exact formula that explains how to line-wrap and quite often different solutions are valid. However there are a few rules that can be applied to common cases.

__Break at operators__

When the line is broken at an operator, the break comes __before__ the operator. For example:

```kotlin
longName: Int = anotherVeryLongVariable + anEvenLongerOne - thisRidiculousLongOne
        + theFinalOne;
```

__Assignment Operator Exception__

An exception to the `break at operators` rule is the assignment operator `=`, where the line break should happen __after__ the operator.

```kotlin
longName: Int =
        anotherVeryLongVariable + anEvenLongerOne - thisRidiculousLongOne + theFinalOne;
```

__Method chain case__

When multiple methods are chained in the same line - for example when using Builders - every call to a method should go in its own line, breaking the line before the `.`

```kotlin
Picasso.with(context).load("https://avatars.githubusercontent.com/u/42269590?s=400&u=88c4366ebb380a6b1069281b14cbce486948d269&v=4").into(imageView)
```

```kotlin
Picasso.with(context)
        .load("https://avatars.githubusercontent.com/u/42269590?s=400&u=88c4366ebb380a6b1069281b14cbce486948d269&v=4")
        .into(imageView)
```

__Long parameters case__

When a method has many parameters or its parameters are very long, we should break the line after every comma `,`

```kotlin
loadPicture(context, "https://avatars.githubusercontent.com/u/42269590?s=400&u=88c4366ebb380a6b1069281b14cbce486948d269&v=4", mImageViewProfilePicture, clickListener, "Title of the picture")
```

```kotlin
loadPicture(context,
        "https://avatars.githubusercontent.com/u/42269590?s=400&u=88c4366ebb380a6b1069281b14cbce486948d269&v=4",
        mImageViewProfilePicture,
        clickListener,
        "Title of the picture")
```


#### Brace Style

Only trailing closing-braces are awarded their own line. All others appear the same line as preceding code:

__BAD:__

```kotlin
class MyClass
{
  fun doSomething()
  {
    if (someTest)
    {
      // ...
    }
    else
    {
      // ...
    }
  }
}
```

__GOOD:__

```kotlin
class MyClass {
    fun doSomething() {
        if (someTest) {
            // ...
        } else {
            // ...
        }
    }
}
```

Conditional statements are always required to be enclosed with braces, irrespective of the number of lines required.

__BAD:__

```kotlin
if (someTest)
  doSomething()
if (someTest) doSomethingElse()
```

__GOOD:__

```kotlin
if (someTest) {
    doSomething()
}

if (someTest) { doSomethingElse() }
```


### Don't Ignore Exceptions

You must never do the following:

```kotlin
fun setServerPort(value: String) {
    try {
        serverPort = value.toInt()
    } catch (e: NumberFormatException) {}
}
```

_While you may think that your code will never encounter this error condition or that it is not important to handle it, ignoring exceptions like above creates mines in your code for someone else to trip over some day. You must handle every Exception in your code in some principled way. The specific handling varies depending on the case._ - ([Android code style guidelines](https://source.android.com/source/code-style.html))

See alternatives [here](https://source.android.com/source/code-style.html#dont-ignore-exceptions).


### Don't Catch Generic Exception

You should not do this:

```kotlin
try {
    someComplicatedIOFunction()         // may throw IOException
    someComplicatedParsingFunction()    // may throw ParsingException
    someComplicatedSecurityFunction()   // may throw SecurityException
    // phew, made it all the way
} catch (e: Exception) {                // I'll just catch all exceptions
    handleError()                       // with one generic handler!
}
```

See the reason why and some alternatives [here](https://source.android.com/source/code-style.html#dont-catch-generic-exception)


### Don't Use Finalizers

_We don't use finalizers. There are no guarantees as to when a finalizer will be called, or even that it will be called at all. In most cases, you can do what you need from a finalizer with good exception handling. If you absolutely need it, define a `close()` method (or the like) and document exactly when that method needs to be called. See `InputStream` for an example. In this case it is appropriate but not required to print a short log message from the finalizer, as long as it is not expected to flood the logs._ - ([Android code style guidelines](https://source.android.com/source/code-style.html#dont-use-finalizers))


### Fully Qualify Imports

This is bad: `import foo.*;`

This is good: `import foo.Bar;`

See more info [here](https://source.android.com/source/code-style.html#fully-qualify-imports)


### When Statements

To keep `when` statements clean, do not call more than one function from a condition. Prefer to move these functions into a single enclosing function:

__BAD:__

```kotlin
when (aValue) {
    1 -> doSomethingForCaseOne()
    2 -> {
        foo()
        bar()
    }
    3 -> doSomethingForCaseThree()
}
```

__GOOD:__

```kotlin
when (aValue) {
    1 -> doSomethingForCaseOne()
    2 -> doSomethingForCaseTwo()
    3 -> doSomethingForCaseThree()
}

fun doSomethingForCaseTwo() {
    foo()
    bar()
}
```

Unlike `switch` statements in Java, `when` statements do not fall through. Separate cases using commas if they should be handled the same way. Always include the else case.

__BAD:__

```kotlin
when (anInput) {
  1 -> doSomethingForCaseOneOrTwo()
  2 -> doSomethingForCaseOneOrTwo()
  3 -> doSomethingForCaseThree()
}
```

__GOOD:__

```kotlin
when (anInput) {
    1, 2 -> { doSomethingForCaseOneOrTwo() }
    3 -> { doSomethingForCaseThree() }
    else -> { println("No case satisfied") }
}
```


### Type Inference

Type inference should be preferred where possible to explicitly declared types. 

__BAD:__

```kotlin
val something: MyType = MyType()
val meaningOfLife: Int = 42
```

__GOOD:__

```kotlin
val something = MyType()
val meaningOfLife = 42
```


### Companion Objects
Companion objects, such as those for `Fragment` `newInstance` methods, should be defined at the bottom of a class declaration;

```kotlin
class MyFragment : Fragment() {

    init {
        Injector.INSTANCE.inject(this)
    }

    @Inject
    lateinit var dataManager: DataManager

    fun doSomething() {
        // ...
    }

    companion object {
        const val BUNDLE_VALUE_ONE = "bundle_value_one"

        fun newInstance(value1: String, value2: String): MyFragment {
            // ...
        }
    }
}
```
As a sidenote regarding `val` properties in companion objects; accessing them from Java requires accessing the companion object too, which is ugly and not idiomatic:

```java
String key = MyFragment.Companion.BUNDLE_VALUE_ONE;
```

Delcaring the property as a `const val` allows you to access a property as if it was static from Java code:

```java
String key = MyFragment.BUNDLE_VALUE_ONE;
```
This also inlines any access to the `val`. There is a caveat though: this only works with primitives and Strings. For more information, check out [this](https://blog.egorand.me/where-do-i-put-my-constants-in-kotlin/) excellent article regarding constants in Kotlin.


### Constants vs. Variables 

Constants are defined using the `val` keyword, and variables with the `var` keyword. Always use `val` instead of `var` if the value of the variable will not change.

*Tip*: A good technique is to define everything using `val` and only change it to `var` if the compiler complains!


### Nullable Types

Declare variables and function return types as nullable with `?` where a `null` value is acceptable.

Use implicitly unwrapped types declared with `!!` only for instance variables that you know will be initialized before use, such as subviews that will be set up in `onCreate` for an Activity or `onCreateView` for a Fragment.

When naming nullable variables and parameters, avoid naming them like `nullableString` or `maybeView` since their nullability is already in the type declaration.

When accessing a nullable value, use the safe call operator if the value is only accessed once or if there are many nullables in the chain:

```kotlin
editText?.setText("foo")
```


### Limit Variable Scope

_The scope of local variables should be kept to a minimum. By doing so, you increase the readability and maintainability of your code and reduce the likelihood of error. Each variable should be declared in the innermost block that encloses all uses of the variable._

_Local variables should be declared at the point they are first used. Nearly every local variable declaration should contain an initializer. If you don't yet have enough information to initialize a variable sensibly, you should postpone the declaration until you do._ - ([Android code style guidelines](https://source.android.com/source/code-style.html#limit-variable-scope))


### Visibility Modifiers

Always include visibility modifiers.

**BAD:**

```kotlin
val wideOpenProperty = 1
private val myOwnPrivateProperty = "private"
```

**GOOD:**

```kotlin
public val wideOpenProperty = 1
private val myOwnPrivateProperty = "private"
```


### Access Level Modifiers

Access level modifiers should be explicitly defined for classes, methods and member variables.


### Logging guidelines

Use the logging methods provided by the `Log` class to print out error messages or other information that may be useful for developers to identify issues:

* `Log.v(String tag, String msg)` (verbose)
* `Log.d(String tag, String msg)` (debug)
* `Log.i(String tag, String msg)` (information)
* `Log.w(String tag, String msg)` (warning)
* `Log.e(String tag, String msg)` (error)

As a general rule, we use the class name as tag and we define it at the top of the file. For example:

```kotlin
public class MyClass {
    private val TAG = MyClass::class.qualifiedName

    private fun myMethod() {
        Log.e(TAG, "My error message")
    }
}
```

VERBOSE and DEBUG logs __must__ be disabled on release builds. It is also recommended to disable INFORMATION, WARNING and ERROR logs but you may want to keep them enabled if you think they may be useful to identify issues on release builds. If you decide to leave them enabled, you have to make sure that they are not leaking private information such as email addresses, user ids, etc.

To only show logs on debug builds:

```kotlin
if (BuildConfig.DEBUG) Log.d(TAG, "The value of x is " + x)
```


### Class Member Ordering

There is no single correct solution for this but using a __logical__ and __consistent__ order will improve code learnability and readability. It is recommendable to use the following order:

1. Constants
2. Fields
3. Constructors
4. Override methods and callbacks (public or private)
5. Public methods
6. Private methods
7. Inner classes or interfaces

Example:

```kotlin
public class MainActivity: Activity {
    private val TAG = MainActivity::class.qualifiedName

    private var title: String?
    private var textViewTitle: TextView?

    override fun onCreate() {
        ...
    }

    public fun setTitle(title: String) {
    	this.title = title
    }

    private fun setUpView() {
        ...
    }

    inner class AnInnerClass {

    }
}
```

If your class is extending an __Android component__ such as an Activity or a Fragment, it is a good practice to order the override methods so that they __match the component's lifecycle__. For example, if you have an Activity that implements `onCreate()`, `onDestroy()`, `onPause()` and `onResume()`, then the correct order is:

```kotlin
public class MainActivity: Activity {

	//Order matches Activity lifecycle
    override fun onCreate() {}

    override fun onResume() {}

    override fun onPause() {}

    override fun onDestroy() {}
}
```


### Parameter Ordering in Methods

When programming for Android, it is quite common to define methods that take a `Context`. If you are writing a method like this, then the __Context__ must be the __first__ parameter.

The opposite case are __callback__ interfaces that should always be the __last__ parameter.

Examples:

```kotlin
// Context always goes first
public fun loadUser(context: Context, userId: Int): User { };

// Callbacks always go last
public fun loadUserAsync(context: Context, userId: Int, userCallback: UserCallback) { };
```


### String Constants, Naming, and Values

Many elements of the Android SDK such as `SharedPreferences`, `Bundle`, or `Intent` use a key-value pair approach so it's very likely that even for a small app you end up having to write a lot of String constants.

When using one of these components, you __must__ define the keys as a `const val` fields in `companion object` and they should be prefixed as indicated below.

| Element            | Field Name Prefix |
| ------------------ | ----------------- |
| SharedPreferences  | `PREF_`           |
| Bundle             | `BUNDLE_`         |
| Fragment Arguments | `ARGUMENT_`       |
| Intent Extra       | `EXTRA_`          |
| Intent Action      | `ACTION_`         |

Note that the arguments of a Fragment - `Fragment.getArguments()` - are also a Bundle. However, because this is a quite common use of Bundles, we define a different prefix for them.

Example:

```kotlin
companion object {
    // Note the value of the field is the same as the name to avoid duplication issues
    const val PREF_EMAIL = "PREF_EMAIL"
    const val BUNDLE_AGE = "BUNDLE_AGE"
    const val ARGUMENT_USER_ID = "ARGUMENT_USER_ID"

    // Intent-related items use full package name as value
    const val EXTRA_SURNAME = "com.myapp.extras.EXTRA_SURNAME"
    const val ACTION_OPEN_USER = "com.myapp.action.ACTION_OPEN_USER"
}
```

Prefer using string template to concatenate string for cleaner code.

__BAD:__

```kotlin
val language = "Android"
val sentence = "I love to code in " + language "."
```

__GOOD:__

```kotlin
val language = "Android"
val sentence = "I love to code in ${language}."
```


### Arguments in Fragments and Activities

When data is passed into an `Activity` or `Fragment` via an `Intent` or a `Bundle`, the keys for the different values __must__ follow the rules described in the section above.

When an `Activity` or `Fragment` expects arguments, it should provide a method that facilitates the creation of the relevant `Intent` or `Fragment`.

In the case of Activities the method is usually called `getStartIntent()`:

```kotlin

companion object {
    @JvmStatic
    fun getStartIntent(context: Context, user: User): Intent {
        val intent = Intent(context, ThisActivity::class.java)
        intent.putParcelableExtra(EXTRA_USER, user)
        return intent
    }
}
```

For Fragments it is named `newInstance()` and handles the creation of the Fragment with the right arguments:

```kotlin
companion object {
    @JvmStatic
    fun newInstance(user: User): UserFragment {
        val fragment = UserFragment()
        val args = Bundle()
        args.putParcelable(ARGUMENT_USER, user)
        fragment.setArguments(args)
        return fragment
    }
}
```

__Note 1__: These methods should go at the top of the class before `onCreate()`.

__Note 2__: If we provide the methods described above, the keys for extras and arguments should be `private` because there is not need for them to be exposed outside the class.


## XML Style Rules


### Use Self Closing Tags

When an XML element doesn't have any contents, you __must__ use self closing tags.

This is good:

```xml
<TextView
	android:id="@+id/text_view_profile"
	android:layout_width="wrap_content"
	android:layout_height="wrap_content" />
```

This is __bad__ :

```xml
<!-- Don't do this! -->
<TextView
    android:id="@+id/text_view_profile"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" >
</TextView>
```


### Resources Naming

Resource IDs and names are written in __lowerCamelCase__.


#### ID naming

IDs should be prefixed with the name of the element in lower camel case. For example:


| Element       | Prefix   |
| ------------- | -------- |
| `TextView`    | `text`   |
| `ImageView`   | `img`    |
| `Button`      | `btn`    |
| `Menu`        | `menu`   |
| `ImageButton` | `imgBtn` |

Image view example:

```xml
<ImageView
    android:id="@+id/imgProfile"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" />
```

Menu example:

```xml
<menu>
	<item
        android:id="@+id/menuDone"
        android:title="Done" />
</menu>
```


#### Strings

String names start with a prefix that identifies the section they belong to. For example `registration_email_hint` or `registration_name_hint`. If a string __doesn't belong__ to any section, then you should follow the rules below:


| Prefix    | Description                          |
| --------- | ------------------------------------ |
| `error_`  | An error message                     |
| `msg_`    | A regular information message        |
| `title_`  | A title, i.e. a dialog title         |
| `action_` | An action such as "Save" or "Create" |

Exceptions are strings like `yes`, `no`, `cancel` which have the same use case everywhere and are used a lot.


#### Styles and Themes

Unlike the rest of resources, style names are written in __UpperCamelCase__ as they are specifies in the `themes.xml`/`styles.xml`.


### Attributes Ordering

As a general rule you should try to group similar attributes together. A good way of ordering the most common attributes is:

1. View ID
2. Style
3. Layout Width and Layout Height
4. Other layout attributes, sorted alphabetically
5. Style attributes such as `gravity` or `textColor`
6. Value attributes such as `text` or `src`
7. Remaining attributes, sorted alphabetically
