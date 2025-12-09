# Procedures and Keyword Arguments

## Defines Are Deprecated

Existing stdlib icon libraries use !define and !definelong to create
different macros.

> !function and !procedure should be used instead of !define and
> !definelong
>
> Per
> [MigrationNotes](https://plantuml.com/preprocessing#ajlk3nchu0zkka0ybjng):
>
> > *You should not use !define and !definelong anymore. Use !function,
> > !procedure or variable definition instead.*
> >
> > *!define should be replaced by return !function*
> >
> > *!definelong should be replaced by !procedure.*

## Default Values

Per
[DefaultArgumentValue](https://plantuml.com/preprocessing#ae1b47605326b65f),
"In both procedure and return functions, you can define default values
for arguments"

> The [default
> argument](https://plantuml.com/en/preprocessing#ajlk3nchu0zkka0ybjng)
> value can help to simplify definitions


![](/PlantUML%20features/procedures/defaultArgument.png)


```
@startuml
!function $inc($value, $step=1)
!return $value + $step
!endfunction

Alice -> Bob : Just one more $inc(3)
Alice -> Bob : Add two to three : $inc(3, 2)
@enduml

```


## Keyword Arguments

Current macros are polymorphic e.g. macros are defined twice with a
different number of arguments.

However, the ordering of the arguments is hardcoded e.g. first parameter
is "alias".

This has a number of issues:

1.  if the user wants to specify the 5th parameter only, they need to
    specify the first 4 also.
2.  if we want to add new parameters in the future, then we need to add
    them at the end - adding maybe more macros to do so.

Keyword Arguments allow the user to specify what they care about, and
the procedure uses defaults for other parameters. It also gives
extensibility.

See `Step-by-step Towards A Standard Macro` for the under-the-hood work
that led towards the following release.

<https://plantuml.com/news> *17 May, 2020: Use keyword arguments with
the preprocessor (V1.2020.10). (Thanks to Crashedmind for the suggestion
!)*
