+++
title = 'Nullable reference types in C#'
date = 2023-10-27T13:40:43+02:00
+++

In C# 8.0 and later, the language introduced a feature called "nullable reference types." This feature was designed to help developers avoid null reference exceptions, which are a common source of runtime errors in C# programs.

When you enable nullable reference types, the C# compiler uses static flow analysis to determine where you might be accessing a reference type that could be null. It then provides warnings in those places, prompting you to handle the potential nulls appropriately.

Here's a brief overview of how it works:

**Non-nullable Reference Types:** By default, when you enable this feature, reference types are considered non-nullable. This means if you have a variable of type string, the compiler expects it never to be null.

```csharp
string name = null; // This will give a warning
```

**Nullable Reference Types:** If you want to indicate that a reference type can be null, you append a ? to its type.

```csharp
string? name = null; // This is fine
```

**Flow Analysis:** The compiler uses flow analysis to determine if a reference type variable can be null at the point of its usage.

```csharp
string? name = GetName();
int length = name.Length; // Warning: Dereference of a possibly null reference
```

**Null-forgiving Postfix:** If you're sure that a reference won't be null even if it's declared as nullable, you can use the ! operator to suppress the warning.

```csharp
string? name = GetName();
int length = name!.Length; // No warning
```

**Attributes:** There are also various attributes like [MaybeNull], [NotNull], etc., that can be used to provide more granular control over nullability behavior.

To enable nullable reference types, you can add the following directive at the top of your C# file:

```csharp
#nullable enable
```

Or, to enable it for the entire project, you can set the <Nullable> property to enable in your project file:

```xml
<PropertyGroup>
    <Nullable>enable</Nullable>
</PropertyGroup>
```

Remember, enabling nullable reference types doesn't change the runtime behavior of your program. It's a compile-time feature that provides warnings to help you catch potential null reference issues.
