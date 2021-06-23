# log

#### Function Description

`log` is a build.security built-in function that adds log statement\(s\) to the decision log upon evaluation.

It's important to note that the log statements appear _only_ in the decision log when HTTP authz requests are made to the PDP server, and not, for example, in the Rego playground.

#### Function format

`log(statement)`

**Parameters:**

* `statement` - the string to add to the decision log.

#### Function Usage Example

```text
log("A simple log statement")

# Log Rego values by converting them to string
log(sprintf("Logging some values: %v %v", [x, y]))
```

**Usage in production**

Most Rego rules are cached upon evaluation, but adding certain functions such as `log` inside rules prevents them from getting cached.

This not only affects performance, it also means that if there is a evaluation containing `log` inside a Rego loop, the decision log will end up being large.

As such, using `log` is encouraged only for development and debugging.

The recommended way to record useful information in production is by restructuring policy: move statements out from inside rules to new rules in the global scope. This way, their evaluation will be recorded in the result.

Example, change the following rule:

```text
rule_with_multiple_checks {
    ...check_1...
    ...check_2...
    ...check_3...
}
```

by making new rules in the global scope:

```text
check_1 {
    ...
}

check_2 {
    ...
}

check_3 {
    ...
}

final_rule {
    check_1
    check_2
    check_3
}
```

The evaluation output of `check_1`, `check_2` and `check_3` will now be accessible on your build.security console.

