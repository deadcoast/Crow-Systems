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

### Primary Operators ###

1. **`.` (Property Access)** - Used to access properties within variables
   - Example: `{user.name}` accesses the `name` property of the `user` variable

2. **`:` (Property Setter)** - Used to set properties (FIRST PRIORITY)
   - Example: `{sys:admin}` sets the `sys` variable to `admin` value`
   - **ORDER OF USE**: `:` is used FIRST to establish the property-value relationship

3. **`=` (Assignment Connector)** - Used to connect properties to values (SECOND PRIORITY)
   - Example: `syntax:opinion={strict:dep=(design_format)}`
   - **ORDER OF USE**: `=` is used SECOND, after `:` has already been used
   - **PURPOSE**: Connects a third function when `:` has already established the primary relationship

4. **`+` (Concatenation)** - Used to concatenate sequences and properties
   - **WHEN TO USE**: Use `+` to chain multiple properties, commands, or sequences
   - Example: `<completion:str[oper, var, opt]:(dep:corvus_design)>+<dep:corvus={corvus_design}>`
   - **LOGIC**: Each `+` creates a new sequence that builds upon the previous one

5. **`"` (Natural Language)** - Used to encase natural language taskstrings
   - Example: `[nl]"Design a Professional Format for the corvus syntax"`
   - **PURPOSE**: Allows human-readable descriptions within the structured syntax

6. **`><` (Bridge/Connector)** - Used to pipe or chain sequences (BYPRODUCT of proper Parent Bracket pairing)
   - **LOGIC**: `><` Opposite bracket pairs of parent values touching identify an open and closed sequence
   - **PURPOSE**: Bridges two sequences together
   - **RULE**: Only the closing Parent bracket meeting the opening Parent Bracket has this effect
   - Example: `syntax:opinion={strict:dep=(design_format)}>+` - the `><` bridges the property assignment to the concatenation

## DIRECTIVES (A:`direc`) ##

The Principal Command is the directive, it must be in ALL CAPITAL LETTERS.

- Directives Utilize `<!--` and `-->` brackets.

RULES:
    - Directives must be in ALL CAPITAL LETTERS
    - Directives must be enclosed in `<!--` and `-->` brackets
    - Only one directive per bracket pair
    - Directives can contain commands, variables, and options

### DEVELOP (A:`DEV`) ###

USAGE:
    - Directive to develop or complete logic for a system component
    - Other Language Example:
      - `def` function definition in Python
    - `corvus` Syntax Examples:

     ```crow
     <!-- <<DEV:req={type:adherence}><syntax:opinion={strict:dep=(design_format)}>+
       <completion:str[oper, var, opt, dirv, cmd, nl]:(dep:corvus_design)> -->
     ```

     ```crow
     <!-- <<DEV:{api:endpoint}><method:{type:post}><schema:{fields:name,email,password}>+
       <validation:{required:true}> -->
     ```

     ```crow
     <!-- <<DEV:{module:auth}><req:{security:oauth2}><validation:{input:email}>+
       <output:{format:json}> -->
     ```

### ASSIGN (A:`ASGN`) ###

USAGE:
    - Directive to assign a value to a variable or property
    - Other Language Example:
      - `=` assignment operator in Python
    - `corvus` Syntax Examples:

     ```crow
     <!-- <ASGN:{sys:admin}><{sys_output:corvus}> -->
     ```

     ```crow
     <!-- <ASGN:{config:database}><{url:postgresql://prod/db}><{env:production}>+
       <{timeout:30}> -->
     ```

     ```crow
     <!-- <ASGN:{user:permissions}><{role:editor}><{access:admin}>+
       <{scope:global}> -->
     ```

### SET (A:`SET`) ###

USAGE:
    - Directive to set a property or configuration value
    - Other Language Example:
      - `set()` function in Python
    - `corvus` Syntax Examples:

     ```crow
     <!-- <<SET:{formatting_style:professional_document}><format:corvus>> -->
     ```

     ```crow
     <!-- <<SET:{debug:mode}><level:{type:verbose}><output:{destination:console}>+
       <{file:debug.log}> -->
     ```

     ```crow
     <!-- <<SET:{api:config}><timeout:{value:30}><unit:{type:seconds}>+
       <retries:{count:3}> -->
     ```

### TASK (A:`TASK`) ###

USAGE:
    - Directive to define a task or objective to be completed
    - Other Language Example:
      - `import` statement in Python
    - `corvus` Syntax Examples:

    ```crow
    <!-- <<TASK:[nl]"Design a Professional Format for the corvus syntax">+
      <priority:{level:critical}><deadline:{date:2024-01-15}> -->
    ```

    ```crow
    <!-- <<TASK:[nl]"Implement user authentication system">+
      <req:{security:oauth2}><validation:{input:email}>+
      <output:{format:jwt}> -->
    ```

    ```crow
    <!-- <<TASK:[nl]"Create API documentation">+
      <format:{type:openapi}><version:{spec:3.0}>+
      <style:{theme:professional}> -->
    ```

### ENFORCE (A:`ENFR`) ###

USAGE:
    - Directive to enforce a rule or standard
    - Other Language Example:
      - `assert` statement in Python
    - `corvus` Syntax Examples:

    ```crow
    <!-- <<ENFR:corvus{.markdownlint.jsonc}> -->
    ```

    ```crow
    <!-- <<ENFR:{code_style:pep8}><validation:{strict:true}><auto_fix:{enabled:true}>+
      <{ignore:legacy}> -->
    ```

    ```crow
    <!-- <<ENFR:{security:ssl}><cert:{type:wildcard}><validation:{strict:true}>+
      <{expiry:90_days}> -->
    ```

### CREATE (A:`CRT`) ###

USAGE:
    - Directive to create a new element, resource, or component
    - Other Language Example:
      - `class` definition in Python
    - `corvus` Syntax Examples:

    ```crow
    <!-- <<CREATE:{file:config.json}><type:{format:json}><schema:{validation:strict}>+
      <{backup:true}> -->
    ```

    ```crow
    <!-- <<CREATE:{database:user_table}><schema:{fields:name,email,password}>+
      <index:{unique:email}><{constraints:not_null}> -->
    ```

    ```crow
    <!-- <<CREATE:{api:endpoint}><method:{type:post}><auth:{required:true}>+
      <rate_limit:{requests:100}><per:{time:minute}> -->
    ```

### UPDATE (A:`UPD`) ###

USAGE:
    - Directive to update an existing element or resource
    - Other Language Example:
      - `.update()` method in Python dictionaries
    - `corvus` Syntax Examples:

    ```crow
    <!-- <<UPDATE:{config:database_url}><value:{new:postgresql://prod/db}>+
      <migration:{backup:true}><{validation:connection_test}> -->
    ```

    ```crow
    <!-- <<UPDATE:{user:permissions}><add:{role:editor}><scope:{resources:documents}>+
      <{expiry:2024-12-31}> -->
    ```

    ```crow
    <!-- <<UPDATE:{api:version}><bump:{from:v1.0,to:v1.1}>+
      <breaking_changes:{count:2}><{migration_guide:required}> -->
    ```

### DELETE (A:`DEL`) ###

USAGE:
    - Directive to delete an element or resource
    - Other Language Example:
      - `del` statement in Python
    - `corvus` Syntax Examples:

    ```crow
    <!-- <<DELETE:{file:temp_data.json}><backup:{location:archive}>+
      <{confirmation:required}> -->
    ```

    ```crow
    <!-- <<DELETE:{user:inactive_accounts}><condition:{status:inactive}>+
      <grace_period:{days:30}><{notification:email}> -->
    ```

    ```crow
    <!-- <<DELETE:{cache:expired_entries}><cleanup:{frequency:daily}>+
      <threshold:{age:7_days}><{log:deleted_count}> -->
    ```

### VALIDATE (A:`VAL`) ###

USAGE:
    - Directive to validate a condition, requirement, or data integrity
    - Other Language Example:
      - `isinstance()` function in Python
    - `corvus` Syntax Examples:

    ```crow
    <!-- <<VALIDATE:{input:email_format}><pattern:{regex:^[\w\.-]+@[\w\.-]+\.[a-zA-Z]{2,}$}>+
      <sanitize:{trim:true}><{error_message:invalid_email}> -->
    ```

    ```crow
    <!-- <<VALIDATE:{config:required_fields}><check:{missing:api_key,database_url}>+
      <severity:{level:critical}><{auto_fix:false}> -->
    ```

    ```crow
    <!-- <<VALIDATE:{data:user_permissions}><verify:{access:admin,role:editor}>+
      <scope:{resources:all}><{audit_log:enabled}> -->
    ```

## VARIABLES (A:`var`) ##

- VARIABLES UTILIZE `{ }` brackets.

RULES:
    - Variables must be enclosed in `{` and `}` brackets
    - Variable names are case-sensitive
    - Variables can contain values separated by `:`
    - Variables can be nested within other variables

### System (A:`sys`) ###

USAGE:
    - Variable for system-level configurations and settings
    - Other Language Example:
      - `system` in Python
    - `corvus` Syntax Examples:
      - `{sys:admin}`
      - `{sys:production}`
      - `{sys:debug_mode}`
      - `{sys:database_url}`

### Output (A:`output`) ###

USAGE:
    - Variable for output formats and destinations
    - Other Language Example:
      - `output` in Python
    - `corvus` Syntax Examples:
      - `{output:console}`
      - `{output:file}`
      - `{output:json}`
      - `{output:corvus}`

### Input (A:`input`) ###

USAGE:
    - Variable for input sources and formats
    - Other Language Example:
      - `input` in Python
    - `corvus` Syntax Examples:
      - `{input:user}`
      - `{input:file}`
      - `{input:api}`
      - `{input:database}`

### Format (A:`format`) ###

USAGE:
    - Variable for formatting specifications
    - Other Language Example:
      - `format` in Python
    - `corvus` Syntax Examples:
      - `{format:json}`
      - `{format:yaml}`
      - `{format:markdown}`
      - `{format:corvus}`

### Style (A:`style`) ###

USAGE:
    - Variable for styling and presentation options
    - Other Language Example:
      - `style` in Python
    - `corvus` Syntax Examples:
      - `{style:professional}`
      - `{style:minimal}`
      - `{style:verbose}`
      - `{style:compact}`

### Dependency (A:`dep`) ###

USAGE:
    - Variable for dependency management and relationships
    - Other Language Example:
      - `dep` in Python
    - `corvus` Syntax Examples:
      - `{dep:database}`
      - `{dep:api_service}`
      - `{dep:authentication}`
      - `{dep:logging}`

### Require (A:`req`) ###

USAGE:
    - Variable for requirement specifications
    - Other Language Example:
      - `req` in Python
    - `corvus` Syntax Examples:
      - `{req:python>=3.8}`
      - `{req:authentication}`
      - `{req:ssl_certificate}`
      - `{req:admin_access}`

### Execute (A:`exec`) ###

USAGE:
    - Variable for execution parameters and settings
    - Other Language Example:
      - `exec` in Python
    - `corvus` Syntax Examples:
      - `{exec:sync}`
      - `{exec:async}`
      - `{exec:background}`
      - `{exec:immediate}`

### Configure (A:`config`) ###

USAGE:
    - Variable for configuration values and settings
    - Other Language Example:
      - `config` in Python
    - `corvus` Syntax Examples:
      - `{config:database}`
      - `{config:api_keys}`
      - `{config:logging}`
      - `{config:security}`

### Process (A:`proc`) ###

USAGE:
    - Variable for processing parameters and data
    - Other Language Example:
      - `proc` in Python
    - `corvus` Syntax Examples:
      - `{proc:validate}`
      - `{proc:transform}`
      - `{proc:filter}`
      - `{proc:aggregate}`

### Generate (A:`gen`) ###

USAGE:
    - Variable for generation settings and options
    - Other Language Example:
      - `gen` in Python
    - `corvus` Syntax Examples:
      - `{gen:documentation}`
      - `{gen:code}`
      - `{gen:reports}`
      - `{gen:templates}`

### Transform (A:`trans`) ###

USAGE:
    - Variable for transformation parameters and rules
    - Other Language Example:
      - `trans` in Python
    - `corvus` Syntax Examples:
      - `{trans:format}`
      - `{trans:structure}`
      - `{trans:encoding}`
      - `{trans:validation}`

## COMMANDS (A:`cmd`) ##

- COMMANDS UTILIZE `<< >>` brackets.

RULES:
    - Commands must be enclosed in `<<` and `>>` brackets
    - Commands can contain variables and options
    - Commands are case-sensitive
    - Commands can be chained with `+` operator

### SET (A:`set`) ###

USAGE:
    - Command to set a property or value
    - Other Language Example:
      - `set()` function in Python
    - `corvus` Syntax Examples:

     ```crow
     <<SET:{formatting_style:professional_document}><format:corvus>>
     ```

     ```crow
     <<SET:{debug:mode}><level:{type:verbose}><output:{destination:console}>+
       <{file:debug.log}>>
     ```

     ```crow
     <<SET:{api:config}><timeout:{value:30}><unit:{type:seconds}>+
       <retries:{count:3}>>
     ```

### GET (A:`get`) ###

USAGE:
    - Command to retrieve a property or value
    - Other Language Example:
      - `.get()` method in Python dictionaries
    - `corvus` Syntax Examples:

     ```crow
     <<GET:{user:permissions}><scope:{resources:documents}><format:{type:json}>>
     ```

     ```crow
     <<GET:{config:database_url}><env:{type:production}><validate:{connection:true}>+
       <{cache:ttl_300}>>
     ```

     ```crow
     <<GET:{api:version}><endpoint:{path:/version}><auth:{required:true}>+
       <{headers:content_type}>>
     ```

### CALL (A:`call`) ###

USAGE:
    - Command to call a function or method
    - Other Language Example:
      - Function call syntax in Python
    - `corvus` Syntax Examples:

     ```crow
     <<CALL:{validate:email}><input:{format:string}><pattern:{regex:email}>+
       <{error_handling:strict}>>
     ```

     ```crow
     <<CALL:{process:data}><input:{source:user_data}><transform:{type:normalize}>+
       <{output:structured}>>
     ```

     ```crow
     <<CALL:{generate:report}><template:{type:professional}><data:{source:database}>+
       <{format:pdf}>>
     ```

### RUN (A:`run`) ###

USAGE:
    - Command to run a process or script
    - Other Language Example:
      - `subprocess.run()` in Python
    - `corvus` Syntax Examples:

     ```crow
     <<RUN:{script:deploy.sh}><env:{type:production}><timeout:{seconds:300}>+
       <{log:verbose}>>
     ```

     ```crow
     <<RUN:{test:unit_tests}><coverage:{threshold:80}><parallel:{workers:4}>+
       <{report:html}>>
     ```

     ```crow
     <<RUN:{build:docker_image}><tag:{version:latest}><registry:{host:dockerhub}>+
       <{push:true}>>
     ```

### BUILD (A:`build`) ###

USAGE:
    - Command to build or compile resources
    - Other Language Example:
      - `python -m build` command in Python
    - `corvus` Syntax Examples:

     ```crow
     <<BUILD:{package:wheel}><format:{type:universal}><target:{python:3.8+}>+
       <{sign:true}>>
     ```

     ```crow
     <<BUILD:{docker:image}><base:{os:alpine}><layers:{optimize:true}>+
       <{security:scan}>>
     ```

     ```crow
     <<BUILD:{docs:html}><theme:{style:professional}><navigation:{depth:3}>+
       <{search:enabled}>>
     ```

### TEST (A:`test`) ###

USAGE:
    - Command to test or validate functionality
    - Other Language Example:
      - `pytest` command in Python
    - `corvus` Syntax Examples:

     ```crow
     <<TEST:{unit:user_auth}><coverage:{threshold:90}><parallel:{workers:auto}>+
       <{report:xml}>>
     ```

     ```crow
     <<TEST:{integration:api}><endpoints:{count:all}><auth:{required:true}>+
       <{mock:external}>>
     ```

     ```crow
     <<TEST:{coverage:report}><format:{type:html}><threshold:{line:80,branch:70}>+
       <{fail_under:75}>>
     ```

### DEPLOY (A:`deploy`) ###

USAGE:
    - Command to deploy or publish resources
    - Other Language Example:
      - `pip install` command in Python
    - `corvus` Syntax Examples:

     ```crow
     <<DEPLOY:{app:production}><strategy:{type:rolling}><health_check:{enabled:true}>+
       <{rollback:auto}>>
     ```

     ```crow
     <<DEPLOY:{package:pypi}><repository:{name:testpypi}><version:{auto:increment}>+
       <{twine:check}>>
     ```

     ```crow
     <<DEPLOY:{docs:github_pages}><branch:{name:gh-pages}><build:{source:docs}>+
       <{custom_domain:docs.example.com}>>
     ```

## OPTIONS (A:`opt`) ##

USAGE:
    - Options are used to provide additional parameters
    - Other Language Example:
      - Function parameters in Python
    - `corvus` Syntax Examples:
      - `(option1, option2)`
      - `(debug:true, verbose:false)`
      - `(timeout:30, retries:3)`

- OPTIONS UTILIZE `( )` brackets.

RULES:
    - Options must be enclosed in `(` and `)` brackets
    - Options are used to provide additional parameters
    - Options are optional and can be omitted
    - Multiple options can be separated by commas

## CORVUS BRACKETS ##

### SPACING LOGIC ###

**CRITICAL SPACING RULES:**

- **Principal brackets `<!-- -->`**: NO SPACING (direct connection)
- **Teacher brackets `<< >>`**: TWO SPACES (indented from principal)
- **Parent brackets `< >`**: TWO SPACES (indented from teacher)
- **Variable brackets `{ }`**: NO SPACING (direct connection)
- **Option brackets `( )`**: NO SPACING (direct connection)

### PRINCIPAL BRACKETS `<!-- -->` ###

**PURPOSE**: Highest level directive container
**SPACING**: NO SPACING - direct connection
**RULES**:
    - There must always be a space to isolate the closing directive
    - Principal brackets must be properly nested
    - Each opening `<!--` must have a corresponding closing `-->`
    - Content within principal brackets follows the directive syntax
    - **WHEN TO USE**: For complete directive sequences that span multiple lines

### TEACHER BRACKETS `<< >>` ###

**PURPOSE**: Command execution and action sequences
**SPACING**: TWO SPACES (indented from principal)
**RULES**:
    - Commands must be enclosed in `<<` and `>>` brackets
    - Commands can contain variables and options
    - Commands are case-sensitive
    - Commands can be chained with `+` operator
    - **WHEN TO USE**: For individual commands or command sequences

### PARENT BRACKETS `< >` ###

**PURPOSE**: Property assignment and value setting
**SPACING**: TWO SPACES (indented from teacher)
**RULES**:
    - Properties must be enclosed in `<` and `>` brackets
    - Properties can contain variables and options
    - Properties are case-sensitive
    - Properties can be chained with `+` operator
    - **WHEN TO USE**: For setting properties, values, and configurations

### VARIABLE BRACKETS `{ }` ###

**PURPOSE**: Data storage and variable assignment
**SPACING**: NO SPACING - direct connection
**RULES**:
    - Variables must be enclosed in `{` and `}` brackets
    - Variable names are case-sensitive
    - Variables can contain values separated by `:`
    - Variables can be nested within other variables
    - **WHEN TO USE**: For storing data, values, and variable assignments

### OPTION BRACKETS `( )` ###

**PURPOSE**: Additional parameters and options
**SPACING**: NO SPACING - direct connection
**RULES**:
    - Options must be enclosed in `(` and `)` brackets
    - Options are used to provide additional parameters
    - Options are optional and can be omitted
    - Multiple options can be separated by commas
    - **WHEN TO USE**: For providing additional parameters and configuration options

## EXAMPLE ##

### Source of Truth Example ###

**COMPLETE CORVUS SYSTEM DEMONSTRATION:**

This example demonstrates the full corvus bracket hierarchy system with:
    - proper spacing
    - operator usage
    - sequence logic

Each line shows how the different bracket types work together to create sophisticated, structured commands.

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
    - `{ }` is used to assign the value(`adherence`) to a variable(`req`).
        - `{req:adherence}` is the variable value.
    - `>` Parent closing bracket assigns the directive to the property variable value

**NOTE**:
    - `><` Opposite bracket pairs of parent values touching identifying
    an open and closed sequence of Principal, Teacher,Parent and child commands
    - This pairing bridges the two sequences together
        - Only the closing Parent bracket meeting the opening Parent Bracket has this effect

> `syntax:opinion={strict:dep=(design_format)}>+`
    - `<` Parent Bracket is opened to assign the second property to a variable value.
        - Dependency: Teacher Bracket
    - `syntax` is the property.
    - `opinion` is the value.
    - `strict` is the value.
    - `dep` is the value.
    - `design_format` is the value.
    - `=` is used to connect the Directive Property to the value.
    - `{ }` is used to assign the Option(`design_format`) to the Variable(`dep`).
        - `{dep:design_format}` is the variable value.

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
    - `dep` is the property.
    - `corvus` is the property.
    - `{corvus_design}` is the value.
    - `=` is used to connect the Property to the value.
    - `{ }` is used to assign the Option(`corvus_design`) to the Variable(`corvus`).
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
    - `{ }` is used to assign the Option(`corvus_design`) to the Variable(`corvus`).
        - `{corvus:corvus_design}` is the variable value.
>
> `+` is used to concatenate the enforcement and dependency.
>
> `-->` is used to close the directive.

 Closing Principal bracket `-->` closes the directive.

### COMPLETE SYSTEM LOGIC ###

**HOW THE CORVUS SYSTEM WORKS:**

1. **Principal Level**: `<!-- -->` creates a complete directive container
   - **NO SPACING**: Direct connection to content
   - **PURPOSE**: Encompasses entire directive operations
   - **LOGIC**: The principal bracket circumvents the need for individual teacher brackets

2. **Teacher Level**: `<< >>` executes commands within the directive
   - **TWO SPACES**: Indented from principal
   - **PURPOSE**: Individual commands and actions
   - **LOGIC**: Each command is a discrete action within the directive

3. **Parent Level**: `< >` assigns properties and values
   - **TWO SPACES**: Indented from teacher
   - **PURPOSE**: Setting properties and configurations
   - **LOGIC**: Properties define the characteristics and behavior of elements

4. **Variable Level**: `{ }` stores data and values
   - **NO SPACING**: Direct connection
   - **PURPOSE**: Storing actual data and values
   - **LOGIC**: Variables hold the concrete data that drives the system

5. **Option Level**: `( )` provides additional parameters
   - **NO SPACING**: Direct connection
   - **PURPOSE**: Additional configuration and context
   - **LOGIC**: Options provide extra information and configuration

**OPERATOR SEQUENCE LOGIC:**

1. **`:` (FIRST)**: Establish property-value relationships
2. **`=` (SECOND)**: Connect properties to values (after `:` is used)
3. **`+` (CONCATENATION)**: Chain sequences and properties
4. **`><` (BRIDGE)**: Connect sequences (BYPRODUCT of proper bracket pairing)

**SPACING LOGIC:**

- **Principal**: NO SPACING (direct connection)
- **Teacher**: TWO SPACES (indented from principal)
- **Parent**: TWO SPACES (indented from teacher)
- **Variable**: NO SPACING (direct connection)
- **Option**: NO SPACING (direct connection)

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

    ```crow
    <!-- DIRECTIVE -->
    << COMMAND >>
        < PROPERTY >
        { VARIABLE }
            ( OPTION )
    ```

## USAGE GUIDE ##

### BRACKET HIERARCHY LOGIC ###

**THE COMPLETE CORVUS SYSTEM:**

1. **Principal Level `<!-- -->`**: Complete directive sequences
   - **NO SPACING**: Direct connection to content
   - **PURPOSE**: Encompasses entire directive operations
   - **EXAMPLE**: `<!-- <ASGN:{sys:admin}><{sys_output:corvus}>> -->`

2. **Teacher Level `<< >>`**: Command execution
   - **TWO SPACES**: Indented from principal
   - **PURPOSE**: Individual commands and actions
   - **EXAMPLE**: `<<SET:{formatting_style:professional_document}><format:corvus>>`

3. **Parent Level `< >`**: Property assignment
   - **TWO SPACES**: Indented from teacher
   - **PURPOSE**: Setting properties and values
   - **EXAMPLE**: `<completion:str[oper, var, opt]:(dep:corvus_design)>`

4. **Variable Level `{ }`**: Data storage
   - **NO SPACING**: Direct connection
   - **PURPOSE**: Storing values and data
   - **EXAMPLE**: `{sys:admin}`, `{corvus_design}`

5. **Option Level `( )`**: Parameters
   - **NO SPACING**: Direct connection
   - **PURPOSE**: Additional parameters
   - **EXAMPLE**: `(dep:corvus_design)`, `(type:adherence)`

### OPERATOR USAGE LOGIC ###

**SEQUENCE OF OPERATIONS:**

1. **`:` (FIRST)** - Establish property-value relationship
   - `{sys:admin}` - sets `sys` to `admin`
   - `syntax:opinion` - sets `syntax` property to `opinion` value

2. **`=` (SECOND)** - Connect properties to values (after `:` is used)
   - `syntax:opinion={strict:dep=(design_format)}`
   - Connects the `opinion` property to the `{strict:dep=(design_format)}` value

3. **`+` (CONCATENATION)** - Chain sequences and properties
   - `<completion:str[oper, var, opt]:(dep:corvus_design)>+<dep:corvus={corvus_design}>`
   - Each `+` creates a new sequence building upon the previous

4. **`><` (BRIDGE)** - Connect sequences (BYPRODUCT of proper bracket pairing)
   - `syntax:opinion={strict:dep=(design_format)}>+`
   - Bridges the property assignment to the concatenation
   - **RULE**: Only occurs when closing Parent bracket meets opening Parent bracket

### Basic Syntax Structure ###

The corvus format follows a hierarchical structure:

    ```crow
    <!-- DIRECTIVE:command{variable:value}(option) -->
    ```

### Common Patterns ###

Simple Assignment:

    ```crow
    <!-- <ASGN:{sys:admin}><{sys_output:corvus}>>
      <<SET:{formatting_style:professional_document}><format:corvus>>
      <<TASK:[nl]"Design a Professional Format for the corvus syntax">+ -->
    ```

Command Execution:

    ```crow
    <<SET:{formatting_style:professional_document}><format:corvus>>
      <completion:str[formatting, style, format]:(dep:document_design)>>
    ```

Task Definition:

    ```crow
    <<TASK:[nl]"Design a Professional Format for the corvus syntax">+
      <priority:{level:critical}><deadline:{date:2024-01-15}>+
      <completion:str[task, priority, deadline]:(dep:project_management)>>
    ```

Dependency Management:

    ```crow
    <<DEV:req={type:adherence}><syntax:opinion={strict:dep=(design_format)}>+
      <completion:str[oper, var, opt, dirv, cmd, nl]:(dep:corvus_design)>+
      <validation:{strict:true}><{enforce:corvus_standard}>>
    ```

Property Setting:

    ```crow
    <completion:str[oper, var, opt, dirv, cmd, nl]:(dep:corvus_design)>+
      <dep:corvus={corvus_design}><validation:{strict:true}>>
    ```

Variable with Options:

    ```crow
    {syntax:opinion={strict:dep=(design_format)}}>(type:adherence, completion:str, validation:strict)
      <format:{style:professional}><enforcement:{level:critical}>>
    ```

### BRACKET USAGE LOGIC ###

**WHEN TO USE EACH BRACKET TYPE:**

1. **Principal `<!-- -->`**: Complete directive sequences
   - **USE WHEN**: Creating a complete directive that spans multiple operations
   - **EXAMPLE**: `<!-- <ASGN:{sys:admin}><{sys_output:corvus}>> -->`
   - **LOGIC**: Encompasses the entire directive operation

2. **Teacher `<< >>`**: Individual commands and actions
   - **USE WHEN**: Executing specific commands or actions
   - **EXAMPLE**: `<<SET:{formatting_style:professional_document}><format:corvus>>`
   - **LOGIC**: Each command is a discrete action within the directive

3. **Parent `< >`**: Property assignment and configuration
   - **USE WHEN**: Setting properties, values, or configurations
   - **EXAMPLE**: `<completion:str[oper, var, opt]:(dep:corvus_design)>`
   - **LOGIC**: Properties define the characteristics and behavior of elements

4. **Variable `{ }`**: Data storage and values
   - **USE WHEN**: Storing data, values, or variable assignments
   - **EXAMPLE**: `{sys:admin}`, `{corvus_design}`
   - **LOGIC**: Variables hold the actual data and values

5. **Option `( )`**: Additional parameters
   - **USE WHEN**: Providing additional parameters or configuration options
   - **EXAMPLE**: `(dep:corvus_design)`, `(type:adherence)`
   - **LOGIC**: Options provide additional context and configuration

### Best Practices ###

1. **Consistency:** Always use the same bracket types for the same purposes
2. **Clarity:** Use descriptive variable names and clear directives
3. **Structure:** Follow the Principal -> Teacher -> Parent -> Child hierarchy
4. **Validation:** Ensure all brackets are properly paired and nested
5. **Spacing:** Follow the spacing rules (Principal: NO, Teacher: TWO, Parent: TWO)
6. **Operators:** Use `:` first, then `=`, then `+` for concatenation

### Error Prevention ###

- Always close brackets in the reverse order they were opened
- Use consistent spacing around operators
- Validate syntax before committing changes
- Test examples to ensure they follow the defined rules

### Real-World Examples ###

#### Configuration Management ####

    ```crow
    <!-- <ASGN:{sys:production}><{database_url:postgresql://prod/db}><{env:production}>+
      <<SET:{debug_mode:false}><log_level:{type:info}><output:{destination:file}>+
        <{rotation:daily}><{compression:gzip}>>+
      <<ENFR:{ssl:required}><cert:{type:wildcard}><validation:{strict:true}>+
        <{expiry:90_days}><{auto_renew:true}>> -->
    ```

#### Development Workflow ####

    ```crow
    <!-- <<TASK:[nl]"Implement user authentication system">+
      <priority:{level:high}><deadline:{date:2024-01-15}>+
      <<DEV:{module:auth}><req:{security:oauth2}><validation:{input:email}>+
        <{output:jwt_token}><{expiry:3600}>>+
      <<TEST:{unit:auth_functions}><coverage:{threshold:90}><parallel:{workers:auto}>+
        <{report:xml}><{fail_fast:true}>>+
      <<DEPLOY:{staging:true}><strategy:{type:blue_green}><health_check:{enabled:true}>+
        <{rollback:auto}><{monitoring:enabled}>> -->
    ```

#### Data Processing ####

    ```crow
    <<PROC:{input:user_data}><validate:{email:true}><sanitize:{trim:true}>+
      <{error_handling:strict}><{retry_count:3}>>
    <<TRANS:{format:json}><structure:{normalize:true}><schema:{validation:strict}>+
      <{output:api_response}><{compression:gzip}>>
    <<GEN:{report:user_summary}><template:{type:professional}><data:{source:processed}>+
      <{format:pdf}><{watermark:enabled}>>
    ```
