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



#### Example \#3

Evaluates to `false` since `[1, 2] != [1]`\
Pay attention! Arrays are deeply compared and not partially compared.

```scala
actual := {
    "allow": true,
    "output": {
        "input": {
            "foo": [1],
            "role": "admin"
        }
    }
}

expected := {
    "allow": true,
    "output": {
        "input": {
            "foo": [1],
        }
    }
}

build.json_partial_compare(expected, actual)
```

{% hint style="info" %}


**Supported PDP version** 

This built-in function supported from version V0.3.5 and above 
{% endhint %}

