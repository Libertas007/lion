# Libertas Object Notation (lion)

Libertas Object Notation is a new way of structuring data. It is similar to JSON, but it is made better.

## Document structure

Each document consists of one or two parts.

The first part is a `@schema`. For now, only embedded schema is supported.

To specify a schema, start with `@schema` modifier followed by a schema in braces.

```lion
@schema {
    @definition {
        example: String,
        version: Integer,
    }
}
```

The schema part is optional.

The next and **compulsory** part is the document itself. Start using `@doc` modifier and then a document.

```lion
@doc {
    example: "This is an example document",
    version: 1,
}
```

## `@doc` syntax

The document itself is made up of pairs of keys and values. Keys are defined using an identifier, which consists of letters. A value can be a string, number (integer or float), boolean, array or an object. Commas after values are not optional, but highly recommended!

```lion
@doc {
    example: "This is an example document",
    version: 1,
    users: [
        {
            name: "John",
            age: 32,
        },
        {
            name: "Lucy",
            age: 25,
        }
    ]
}
```

## `@schema` syntax

The schema syntax is very similar to the document syntax. However, there are some differences.

The base schema is defined using a `@definition` modifier followed by a schema definition. This definition also consists of pairs, but the key difference is that the values are type names.

The following types are present:

-   `String`
-   `Number`
-   `Integer`
-   `Float`
-   `Boolean`
-   `Array<T>`

(`T` in `Array<T>` means that the array is made of some other type `T`.)

```lios
@definition {
    example: String,
    version: Number
}
```

As more complex data cannot be specified in only one object, you can create custom types in schemas. Start with `@subschema` modifier, followed by an identifier for the name and the schema as it was done previously.

Type names should follow the PascalCase naming convention.

```lios
@definition {
    example: String,
    version: Number,
    users: Array<User>,
}

@subschema User {
    name: String,
    age: Integer,
}
```
