# build.json\_partial\_compare

### Function Description

Recursively compares two json objects and returns `true` if all of the fields in the `expectedJson` **Exist** and **match** the fields in `actualJson`, otherwise returns `false`

### Function format

`build.json_partial_compare(expectedJson, actualJson)`

**Parameters:**

* `expectedJson` - JSON object that holds all keys and values to check in the `actualJson` object
* `actualJson` - JSON object that holds an object to check fields in values in.

### Function Usage Example

```scala
actual := {
    "a": {
        "b": "c"
    },
    "d": "e"
}

expected := {
    "a": {
        "b": "c"
    }
}

# Evaluates to true
build.json_partial_compare(expected, actual)
```

