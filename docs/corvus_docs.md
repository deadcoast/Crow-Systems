# DICTIONARY #

## PROJECT NOTES ##

---

**TODO:DICTIONARY REQUIRES DEVELOPMENT BASED ON:**
    - The Logic provided in the `corvus` syntax under the [[## EXAMPLE ##]] HEADING
    - Ignore current configuration files for Placeholders:
        - `.markdownlint.jsonc` and `.markdownlintignore`

- The document and logic below for `corvus` must be complete, and fully filled out
- There is some logic that may need to be created to complete methods

---

`corvus` Documentation is a 'no weight' natural language documentation format
    - Designed to be easy to read and understand, while still being machine readable and writable
    - Prefers and prioritizes brackets over spaces for:
        - Separation, Isolation, and Organization of its data and requests
    - Bracket assigns a more rigid framework providing:
    - Less complications and confusion
    - Straightforward and requires no initial training

The Design Philosophy has three pillars:

1. Separation, Modulation through the use of an opinionated bracket system
2. Simple, Direct, Specific WITHOUT UNNECESSARY COMPLEXITY
3. Understood without needing Explanation or Training

## BASIC FORMAT BREAKDOWN ##

Syntax: `Directive -> Command -> Variable -> Options`
Format: `Principal -> Teacher -> Parent -> Child`

- `corvus` is the designed format used in the document suite
- `[nl]` is used to indicate a natural language taskstring
- `A` is used to indicate an Alias, usually used in the context of the syntax
- `corvus_design` correlates to the specifics in the syntax design

## OPERATORS (A:`oper`) ##

   1. `.` is used to access properties.
   2. `:` is used to set properties.
   3. `+` is used to concatenate.
   4. `=` is used to assign.
   5. `"` is used to encase natural language taskstrings.
   6. `|` is used to pipe or chain operations.
   7. `&` is used to combine conditions.
   8. `!` is used to negate conditions.
   9. `?` is used to make conditions optional.
   10. `*` is used to repeat or multiply operations.
   11. `#` is used to reference or link elements.
   12. `@` is used to reference external resources.

## DIRECTIVES A:`direc`) ##

The Principal Command is the directive, it must be in ALL CAPITAL LETTERS.

- Directives Utilize `<!--` and `-->` brackets.

RULES:
    - Directives must be in ALL CAPITAL LETTERS
    - Directives must be enclosed in `<!--` and `-->` brackets
    - Only one directive per bracket pair
    - Directives can contain commands, variables, and options

### DEVELOP (A:`DEV`) ##

- Directive to develop or complete logic for the Directive.

### `ASSIGN` (A:`ASGN`) Assign a value to a variable ###

- Directive to assign a value to a variable.

### `SET` (A:`SET`) Set a property to a value ###

- Directive to set a property to a value.

### `TASK` (A:`TASK`) Set a task to be completed ###

- Directive to set a task to be completed.

### `ENFORCE` (A:`ENFR`) Enforce a rule ###

- Directive to enforce a rule.

### `CREATE` (A:`CRT`) Create a new element ###

- Directive to create a new element or resource.

### `UPDATE` (A:`UPD`) Update an existing element ###

- Directive to update an existing element or resource.

### `DELETE` (A:`DEL`) Delete an element ###

- Directive to delete an element or resource.

### `VALIDATE` (A:`VAL`) Validate a condition ###

- Directive to validate a condition or requirement.

## VARIABLES (A:`var`) ##

- VARIABLES UTILIZE `{ }` brackets.

RULES:
    - Variables must be enclosed in `{` and `}` brackets
    - Variable names are case-sensitive
    - Variables can contain values separated by `:`
    - Variables can be nested within other variables

### System (A:`sys`) ###

- Variable for system-level configurations and settings.

### Output (A:`output`) ###

- Variable for output formats and destinations.

### Input (A:`input`) ###

- Variable for input sources and formats.

### Format (A:`format`) ###

- Variable for formatting specifications.

### Style (A:`style`) ###

- Variable for styling and presentation options.

### Dependency (A:`dep`) ###

- Variable for dependency management and relationships.

### Require (A:`req`) ###

- Variable for requirement specifications.

### Execute (A:`exec`) ###

- Variable for execution parameters and settings.

### Configure (A:`config`) ###

- Variable for configuration values and settings.

### Process (A:`proc`) ###

- Variable for processing parameters and data.

### Generate (A:`gen`) ###

- Variable for generation settings and options.

### Transform (A:`trans`) ###

- Variable for transformation parameters and rules.

## COMMANDS (A:`cmd`) ##

- COMMANDS UTILIZE `<< >>` brackets.

RULES:
    - Commands must be enclosed in `<<` and `>>` brackets
    - Commands can contain variables and options
    - Commands are case-sensitive
    - Commands can be chained with `+` operator

### SET (A:`set`) ###

- Command to set a property or value.

### GET (A:`get`) ###

- Command to retrieve a property or value.

### CALL (A:`call`) ###

- Command to call a function or method.

### RUN (A:`run`) ###

- Command to run a process or script.

### BUILD (A:`build`) ###

- Command to build or compile resources.

### TEST (A:`test`) ###

- Command to test or validate functionality.

### DEPLOY (A:`deploy`) ###

- Command to deploy or publish resources.

## OPTIONS (A:`opt`) ##

RARE USES CASES WHEN VARIABLES REQUIRE OPTIONS.

- OPTIONS UTILIZE `( )` brackets.

RULES:
    - Options must be enclosed in `(` and `)` brackets
    - Options are used to provide additional parameters
    - Options are optional and can be omitted
    - Multiple options can be separated by commas

## CORVUS BRACKETS ##

### PRINCIPAL BRACKETS ###

   1. `<!--` is used to start a directive.
   2. `-->` is used to end a directive.

RULES:
    - There must always be a space to isolate the closing directive
    - Principal brackets must be properly nested
    - Each opening `<!--` must have a corresponding closing `-->`
    - Content within principal brackets follows the directive syntax

### CONTENT BRACKETS ###

   1. `<< >>` is used to start commands
   2. `< >` is used to set properties
   3. `{ }` is used to assign variables

RULES:
    - Content brackets must be properly paired
    - Nested brackets are allowed but must be balanced
    - Each opening bracket must have a corresponding closing bracket
    - Brackets can contain other bracket types

## EXAMPLE ##

```crow
>1| <!-- <ASGN:{sys:admin}><{sys_output:corvus}>>
>2|   <<SET:{formatting_style:professional_document}><format:corvus>>
>3|   <<TASK:[nl]"Design a Professional Format for the corvus syntax">+
>4|   <<DEV:req={type:adherence}><syntax:opinion={strict:dep=(design_format)}>+
>5|     <completion:str[oper, var, opt, dirv, cmd, nl]:(dep:corvus_design)>+
>6|   <<ENFR:corvus{.markdownlint.jsonc}> -->
```

- LINE 1: Opening Principal bracket `<!--` circumvents the requirement/rule for:
  - `<` Parent bracket opens a new sequence
    - Dependency: Principal Bracket
  - `ASGN` directive is used to assign a value to a variable`{sys}`

    > `<<` Teacher opening bracket NOT used here because:
    >
    > The Principal bracket(`<!--`) inherently contains an open Parent Bracket(`<`)

  - `{ }` variable brackets are used to isolate and assign a value to a variable`{sys_output}`
    - `:` is used to set a property
    - `admin` is used to set the property to the value of the variable`{sys}`
  - `+` is not used here because the next line calls
      a Principal Bracket to set a new Directive

LINE 2: Opening Teacher bracket `<<` opens a sequence of parent and child commands.
    - `SET` command is used to set a property to a value.
    - `format` is the property.
    - `corvus` is the value.
  
LINE 3: Opening Principal bracket `<!--` circumvents the requirement/rule for:
    - `<<` Teacher bracket opening a sequence of parent and child commands.
    - `<>` Parent brackets open a new sequence.
    - `+` is used to concatenate.

LINE 4: `<<DEV:req={type:adherence}><syntax:opinion={strict:dep=(design_format)}>+`

>`<<DEV:req={type:adherence}>`
    - `<<` Teacher Bracket Opens a sequence of parent and child commands.
    - `DEV` directive is used to develop or complete logic for the Directive.
        - `:` is used to set a Directive(`DEV`) to a Property(`syntax`).
    - `req` is the property.
        - `type` is the property.
        - `adherence` is the value.
    - `syntax` is the property.
        - `opinion` is the property.
        - `strict` is the value.
        - `dep` is the property.
        - `design_format` is the value.
    - `=` is used to connect the Directive Property to the value.
    - `{ }` is used to assign the value(`consistency`) to a variable(`config`).
        - `{config:consistency}` is the variable value.
    - `>` Parent closing bracket assigns the directive to the property variable value

**NOTE**:
    - `><` Opposite bracket pairs of parent values touching identifying
    an open and closed sequence of Principal, Teacher,Parent and child commands.

> `syntax:opinion={strict:dep=(design_format)}>+`
    - `<` Parent Bracket is opened to assign the second property to a variable value.
        - Dependency: Teacher Bracket
    - `syntax` is the property.
    - `opinion` is the value.
    - `strict` is the value.
    - `dep` is the value.
    - `design_format` is the value.
    - `=` is used to connect the Directive Property to the value.
    - `{ }` is used to assign the Option(`design_format`) to the Variable(`syntax`).
        - `{syntax:design_format}` is the variable value.

LINE 5: `<completion:str[oper, var, opt, dirv, cmd, nl]:(design_format)><dep:corvus={corvus_design}>+`

> `<completion:str[oper, var, opt, dirv, cmd, nl]:(design_format)>`
    - `<` begins, indented with two spaces from the above LINE 4
    - `completion` is the property.
    - `str` is the property.
    - `oper` is the property.
    - `var` is the property.
    - `opt` is the property.
    - `dirv` is the property.
    - `cmd` is the property.
    - `nl` is the property.
    - `(design_format)` is the Option.
    - `>` is used to connect the Property to the Option.
>
> `<dep:corvus={corvus_design}>`
    - `dependency` is the property.
    - `corvus` is the property.
    - `{corvus_design}` is the value.
    - `=` is used to connect the Property to the value.
    - `{ }` is used to assign the Option(`corvus_design`) to the Variable(`dependency`).
        - `{corvus:corvus_design}` is the variable value.
>
> `+` is used to concatenate the completion and dependency.

LINE 6: `<<ENFR:corvus{.markdownlint.jsonc}> -->`

> `<<ENFR:corvus{.markdownlint.jsonc}>`
    - `<<` Teacher Bracket Opens a sequence of parent and child commands.
    - `ENFR` directive is used to enforce a rule.
    - `corvus` is the property.
    - `{markdownlint.jsonc}` is the value.
    - `>` is used to connect the Property to the value.
    - `{ }` is used to assign the Option(`markdownlint.jsonc`) to the Variable(`corvus`).
        - `{corvus:markdownlint.jsonc}` is the variable value.
>
> `<dep:corvus={corvus_design}>+`
    - `dep` is the property.
    - `corvus` is the property.
    - `{corvus_design}` is the value.
    - `=` is used to connect the Property to the value.
    - `{ }` is used to assign the Option(`corvus_design`) to the Variable(`dependency`).
        - `{corvus:corvus_design}` is the variable value.
>
> `+` is used to concatenate the enforcement and dependency.
>
> `-->` is used to close the directive.

 Closing Principal bracket `-->` closes the directive.

## SYNTAX REFERENCE ##

### Quick Reference Table ###

| Element | Bracket | Purpose | Example |
|---------|---------|---------|---------|
| Directive | `<!-- -->` | Principal command | `<!-- <ASGN:{var:value}> -->` |
| Command | `<< >>` | Action execution | `<<SET:{param:value}>>` |
| Variable | `{ }` | Data storage | `{name:value}` |
| Option | `( )` | Parameters | `(option1, option2)` |
| Property | `< >` | Value assignment | `<key:value>` |

### Bracket Hierarchy ###

```
<!-- DIRECTIVE -->
  << COMMAND >>
    < PROPERTY >
      { VARIABLE }
        ( OPTION )
```

## USAGE GUIDE ##

### Basic Syntax Structure ###

The corvus format follows a hierarchical structure:

```
<!-- DIRECTIVE:command{variable:value}(option) -->
```

### Common Patterns ###

1. **Simple Assignment:**
   ```crow
   <!-- <ASGN:{variable:value}> -->
   ```

2. **Command Execution:**
   ```crow
   <<COMMAND:{parameter:value}>>
   ```

3. **Task Definition:**
   ```crow
   <<TASK:[nl]"Natural language description">>
   ```

4. **Dependency Management:**
   ```crow
   <<DEP:{dependency:version}><req:{requirement:specification}>>
   ```

### Best Practices ###

1. **Consistency:** Always use the same bracket types for the same purposes
2. **Clarity:** Use descriptive variable names and clear directives
3. **Structure:** Follow the Principal -> Teacher -> Parent -> Child hierarchy
4. **Validation:** Ensure all brackets are properly paired and nested

### Error Prevention ###

- Always close brackets in the reverse order they were opened
- Use consistent spacing around operators
- Validate syntax before committing changes
- Test examples to ensure they follow the defined rules
