# build.json\_partial\_compare

### Function Description

Recursively compares two json objects and returns `true` if all of the fields in the `expectedJson` **Exist** and **match** the fields in `actualJson`, otherwise returns `false`

### Function format

`build.json_partial_compare(expectedJson, actualJson)`

**Parameters:**

* `expectedJson` - JSON object that holds all keys and values to check in the `actualJson` object
* `actualJson` - JSON object that holds an object to check fields in values in.

### Function Usage Example

#### Example \#1

Evaluates to `false` since `"doctor" != "admin"`

```scala
actual := {
    "allow": true,
    "user": {
        "role": "doctor"
    }
}

expected := {
    "allow": true,
    "user": {
        "role": "admin"
    }
}

build.json_partial_compare(expected, actual)
```



#### Example \#2

Evaluates to `false` since `"4" != 4`

```scala
actual := {
    "allow": true,
    "output": {
        "input": {
            "foo": 4,
            "role": "admin"
        }
    }
}

expected := {
    "allow": true,
    "output": {
        "input": {
            "foo": "4",
        }
    }
}

build.json_partial_compare(expected, actual)
```

