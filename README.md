# ssb-thread-schema

a module which provides you schemas and validators for messages involved in threads.

## Example Usage

```js
var { isRoot, isReply } = require('ssb-thread-schema')

const testMsg = {
  type: 'post',
  text: 'oh choice, finally a less janky way to check our stuff',
  root: '%+fBXl12aV1wpAdD62RMl1WRhwthDMuAuHH4iNWgB7jA=.sha256',
  branch: [
    '%PK5aWmXVYJLcmRQTc/6EQE1ht9T5Kb+wi6NgTReMKXI=.sha256'
  ]
}
// can be the content of a message or the whole thing

isRoot(testMsg)
// => false
isRoot.errors
// => helpful errors

isReply(testMsg)
// => true
```

## API

### `isRoot(Object) -> Boolean`

`Object` can be a full message from the log, or just the content from the message, the validator will take care of it.

If the test Object fails the validation, errors are attached to the function (i.e. `isRoot.errors`, see [Example Usage](#example-usage))

An optional second argument can be passed to the validator if you want to tell the validator to attach errors to the test Object (this mutates the test Object):

```js
isRoot(Object, { attachErrors: true })
```

### `isReply(Object) -> Boolean`
same pattern ^

### `isNestedReply(Object) -> Boolean`
same pattern ^

### `isFork(Object) -> Boolean`
same pattern ^



## See also

- the README in each folder with a little more about each message type
- the birth of forks / nested replies spec : `%+fBXl12aV1wpAdD62RMl1WRhwthDMuAuHH4iNWgB7jA=.sha256`

## TODO

- votes (a.k.a. likes)
- behaviour / flags

