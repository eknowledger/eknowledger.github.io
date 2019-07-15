---
layout: single
title: "XPress: Simple Truth Expression Language"
excerpt: "XPress is a simple yet powerful expression language for .net string literals. Using Xpress compiler you can create string truth expressions at compile time using binary, unary, relational, and conditional operators. XPress compiles expressions into an optimized cacheable predicates that can be evaluated at runtime by binding variable to runtime values. XPress supports numerical, text, boolean, null, and variable operands."
tags: [xpress,project, compiler, programming language, dsl, expression trees, parser]
share: true
comments: true
---

## Background
How many times you needed a quick, simple method to create expressions in a `Json` or `XML` element value. and you wished there were an easy wy to create dynamic expressions at compile time as a literal `string` to be compiled and evaluated at runtime using the same powerful `CLR`. Well, I have! 

The need for string expressions that can be simply expressed at compile time by engineers or non-engineering business or support team, has been a recurring theme through out my career. Whether its is business rules, business teams needs to modify it and change it frequently at runtime. or operation rules that devops team would like to control at runtime without the need to make a new deployment. 

[ <img src="https://raw.githubusercontent.com/eknowledger/XPress/master/XPress_logo.png">](https://github.com/eknowledger/XPress){: .align-center}

## Goals

So, I rolled up my sleeves and created `XPress`. It came handy in many situations and i used it in different product and solution. I had a few goals in mind when I designed `XPress`:


- Simple, yet powerful.
- Contained as possible, as little dependencies as possible.
- few to zero configurations.
- Purely written in C# and .net.
- Fast, and efficient.
- Generates an optimized cacheable .net expressions .
- Support all truth operators (`Binary`, `Unary`, `Relational`, and `Conditional`).
- Support basic data types `int32`, `string`, `boolean`, `float`.
- Support variable binding at runtime.
- Ability to check on `null`-ability.

## How it works?
[![NuGet](https://img.shields.io/nuget/dt/XPress.svg)](https://www.nuget.org/packages/XPress) [![NuGet](https://img.shields.io/nuget/v/XPress.svg?color=blue)](https://www.nuget.org/packages/XPress) [![License](https://img.shields.io/github/license/eknowledger/XPress.svg)](https://raw.githubusercontent.com/eknowledger/XPress/master/LICENSE)


{% highlight powershell %}
PM> Install-Package XPress
{% endhighlight %}

`XPress` is simple, all you have to do after installing [XPress package](https://www.nuget.org/packages/XPress/) using `nuget` manager, is instantiating `XpressCompiler`, author `XPress` expressions, compile it, and execute it. here is a simple `XPress` sample code:

{% highlight csharp %}

XpressCompiler _compiler = XpressCompiler.Default;

// Create and Compile Expression
var expression = "x gt y*2";
var compilationResult = _compiler.Compile(code);

// Create XpressRuntimeContext object with variable names and values
XpressRuntimeContext runtimeCtx = new XpressRuntimeContext() { { "x", "10" }, { "y", "9" } };

// Call compiled Func with runtime context
var result = compilationResult.Code(runtimeCtx);

{% endhighlight %}

As you can see, `XPress` language doesn't need much. very little configuration to start and you're good to go. If you notice I used `XpressCompiler.Default` a singleton compiler instance can be used quickly to compile expressions. But a compiler instance can be always instantiated through constructor.

{% highlight csharp %}

XpressCompiler _compiler = new XpressCompiler();

{% endhighlight %}

 ![class-diagram](/files/xpress_class_01.png){: .align-center}

The compiler class offers a single method `Compile(string)` taking an xpress expression and return a compilation result. The `XpressCompilationResult` object offers a boolean flag `Compiled` to indicate the success or failure of the compilation process, and a `Log` object of type `ILogReader` which can be used to get status on compilation process and debug the result. a particularly useful pattern after compilation process is to check the `HasErrors` fla, if true `GetErrorMessages()` and print it or log it.

{% highlight csharp %}
if (compilationResult.Log.HasErrors)
{
    var errors = compilationResult.Log.GetErrorMessages();
    foreach(var error in errors)
    {
        Console.WriteLine(error);
    }
}

{% endhighlight %}


Finally, the compilation result object, will have a `Code` predicate of type `Func<XpressRuntimeContext, bool>` that is the optimized compiled .net expression tree for your string expression. it accepts `XpressRuntimeContext` which is simply a strongly typed dictionary of `<string,string>` to bind expression's variables to runtime values. use the `XpressRuntimeContext` object to pass values to your variables. `Code` predicate jsut like any other .net `Func` can be cached and executed multiple time. the result of execution is a `boolean`.

## Language Features

### Variables
Variables literals can be used anywhere within an expression
The variable name follows same C# variable literals naming constraints. It Must start with a `letter`, or `_`, and it may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.

{% highlight csharp %}
var e = "y eq x+2*2-4/2";
{% endhighlight %}

### Operands
**XPress** supports boolean literals of `true` and `false` values, numerical operands of `int32` and `float` decimal values, and `string` operands. notice how the operand values are defined in the next sample code:

{% highlight csharp %}
var e1 = "true";
var e2 = "false";
var e3 = "9 gt 10";
var e4 = " 'Ahmed' eq 'ahmed'";

{% endhighlight %}

a `null` operands can also be expressed to compare a string with nothing

{% highlight csharp %}
var e = " 'Ahmed' ne null";
{% endhighlight %}

### Binary Expressions
`+`, `-`, `*`, `/`, `%` is supported on numerical operands

{% highlight csharp %}
var e = "x eq (1+2)";
{% endhighlight %}

If `+` or `-` operators applied to a `string` operands it will act as `String.concat()`

{% highlight csharp %}
var e = "x eq ('ahmed '+'elmalt')";
{% endhighlight %}

**Note**: Binary operators can't be applied to mixed types of operands.
{: .notice--warning}

### Unary Expressions

At the moment only unary logical operators are supported. `not` can onyl be applied to `boolean` operands or expressions.

{% highlight csharp %}
// boolean operands
var e1 = "not false";
        
// boolean variables, the value of x must be set to a boolean value at runtime or runtime error
var e2 = "not x";
        
// boolean expression
var e3 = "not ('a' eq 'b' and 9 gt 10)";

{% endhighlight %}
**Notice** i applied `not` to variable `x` in the previous example. which is acceptable by `XPress` compiler. it will assume that value of `x` will be boolean at runtime otherwise it will throw a runtime exception.

### Relational Expressions

The following relational expressions are supported:
- `eq` Equal
- `ne` Not Equal
- `gt` Greater Than
- `lt` Less Than
- `ge` Greater Than or Equal
- `le` Less Than or Equal

{% highlight csharp %}
var e = "1 eq 4";
{% endhighlight %}

### Conditional Expressions
The real power of `XPress` is composition, you can compose powerful expressions using conditional logical `and` and `or`
- `or` Logical OR
- `and` Logical AND

{% highlight csharp %}
var e = "false or x lt 2";

{% endhighlight %}

### Operator Precedence

- Parentheses: `()`
- Unary Logial Operators: `not`
- Binary Multiplicative Operators: `*`, `/` , `%`
- Binary Additive Operators: `+`, `-`
- Equality Operators: `eq`, `ne`
- Logical Operators: `gt`, `lt`, `ge`, `le`
- Conditional Operators: `and`, `or`


- `XPress` is very powerful and can be used to compose sophisticated boolean expressions as strings.

{% highlight csharp %}
var e = "(x ne null and x+1 gt 10) or (y ne null and (y*(5+1)-2) lt 5)";
{% endhighlight %}

## What about performance?
`XPress` is built to be fast and optimized to generated very efficient .net lambda expressions. the most expensive part of the process as you can expect is the compilation of expressions, but this phase needs to occur once, and the result can be cached for the lifetime of the application. on average `Xpress` compilation phase takes about ~120ms. 

Find more information about `XPress` on project [github repository](https://github.com/eknowledger/XPress). I will be blogging more in the future about the internals implementation of the language and its compiler.

**[XPress](https://github.com/eknowledger/XPress)** is distributed under [MIT license](https://raw.githubusercontent.com/eknowledger/XPress/master/LICENSE). What are you waiting, give it a try and let me know what you think!


_Happy Coding!_