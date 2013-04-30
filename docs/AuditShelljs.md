Audit directory properties/content with ShellJS

_Source: [lib/audit-shelljs/index.js](../lib/audit-shelljs/index.js)_

- [exports.create](#exportscreate)
- [exports.extendAuditShelljs](#exportsextendauditshelljsext)
- [exports.extendRules](#exportsextendrulesext)
- [AuditShelljs](#auditshelljs)
- [AuditShelljs.prototype.last](#auditshelljsprototypelast)
- [AuditShelljs.prototype.pass](#auditshelljsprototypepass)
- [rules._](#rules)
- [rules.__](#rulesmethod)
- [rules.assert](#rulesassertlabel-cb)
- [rules.refute](#rulesrefutelabel-cb)
- [rules.grep](#rulesgrep)
- [rules.grepv](#rulesgrepv)
- [rules.hasDir](#ruleshasdirdir)
- [rules.hasFile](#ruleshasfilefile)

# exports.create()

Create a new AuditShelljs.

**Return:**

`{object}`

# exports.extendAuditShelljs(ext)

Extend AuditShelljs.prototype.

**Parameters:**

- `{object} ext`

**Return:**

`{object}`: Merge result.

# exports.extendRules(ext)

Extend audit rule set.

**Parameters:**

- `{object} ext`

**Return:**

`{object}`: Merge result.

# AuditShelljs()

AuditShelljs constructor.

**Usage:**

```js
var dox = require('audit-shelljs').create();
```

**Configuration:**

- `{string} [input]` Source file to read
- `{string} [output]` Markdown file to write

**Properties:**

- `{object} shelljs` OuterShelljs instance
- `{array} tests` One object per executed test
  - `{string} name` Ex. 'hasFile'
  - `{function} cb` Name-specific test function from `createTester()`
  - `{mixed} res` Ex. ShellJS `test()` boolean result
- `{array} result` One object per executed test
  - `{string} name` Ex. 'hasFile'
  - `{array} args` Ex. arguments passed to `hasFile()`
  - `{mixed} res` Ex. ShellJS `test()` boolean result
- `{boolean} match` True if 0 executed tests failed
- `{function} <rule>` Generated rule testing method
- `{function} refute.<rule>` Negated variants of above rule testing methods

# AuditShelljs.prototype.last()

Return the result of the last executed test.

**Return:**

`{mixed}`: Result object, or undefined if none were executed.

# AuditShelljs.prototype.pass()

Run queued tests and return the result. Stop at first failure.

**Return:**

`{boolean}`: True if all tests passed.

# rules._()

Truthy-test a custom ShellJS invocation.

**Return:**

`{boolean}`

# rules.__(method)

Truthy-test a custom OuterShelljs invocation.

**Parameters:**

- `{string} method`: Ex. 'findByRegex', 'grep'

**Return:**

`{boolean}`

# rules.assert(label, cb)

Truthy-test a custom function invocation.

**Parameters:**

- `{string} label`: Ex. 'contain debug logging'
- `{function} cb`

**Return:**

`{boolean}`

# rules.refute(label, cb)

Falsey-test a custom function invocation.

**Parameters:**

- `{string} label`: Ex. 'contain debug logging'
- `{function} cb`

**Return:**

`{boolean}`

# rules.grep()

Verify that a file has a line with the given string.

Thin wrapper around `OuterShelljs#grep`.

**Return:**

`{boolean}`

**See:**

- [OuterShelljs#grep](https://github.com/codeactual/outer-shelljs/docs/OuterShelljs.md)

# rules.grepv()

Verify that a file has a line with the given string.

Thin wrapper around `OuterShelljs#grep`.

**Return:**

`{boolean}`

**See:**

- [OuterShelljs#grep](https://github.com/codeactual/outer-shelljs/docs/OuterShelljs.md)

# rules.hasDir(dir)

Verify that a sub-dir exists.

**Parameters:**

- `{string} dir`

**Return:**

`{boolean}`

# rules.hasFile(file)

Verify that a descendant file exists.

**Parameters:**

- `{string} file`

**Return:**

`{boolean}`