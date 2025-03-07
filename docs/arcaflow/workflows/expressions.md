# Arcaflow expressions

Arcaflow expressions are heavily inspired by JSONPath, but have diverged from the syntax. You can use expressions in a workflow YAML like this:

```yaml
some_value: !expr $.your.expresion.here
```

This page explains the language elements of expressions.

!!! warning
    Expressions in workflow definitions **must** be prefixed with `!expr`, otherwise their literal value will be taken as a string.

## Root reference

The `$` character always references the root of the data structure. Let's take this data structure:

```yaml
foo:
  bar: Hello world!
```

You can reference the text like this:

```
$.foo.bar
```

## Dot notation

The dot notation allows you to dive into a data structure. If the data structure is a map, it will look up the map keys. If it's a list, it will look up the list item. If it's an object, it will look up the object property.

For example, you can look up the list item from this data structure:


```yaml
foo:
  - Hello world!
```

You can use the following expression to access it:

```
$.foo.0
```

## Array accessor

Alternative to the dot notation, you can also use the array accessor:

```
$.foo[0]
```

In Arcaflow, the two are equivalent.