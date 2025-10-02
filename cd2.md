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

### ASSIGN (A:`ASGN`) Assign a value to a variable ###

- Directive to assign a value to a variable.

### SET (A:`SET`) Set a property to a value ###

- Directive to set a property to a value.

### TASK (A:`TASK`) Set a task to be completed ###

- Directive to set a task to be completed.

### ENFORCE (A:`ENFR`) Enforce a rule ###

- Directive to enforce a rule.

### CREATE (A:`CRT`) Create a new element ###

- Directive to create a new element or resource.

### UPDATE (A:`UPD`) Update an existing element ###

- Directive to update an existing element or resource.

### DELETE (A:`DEL`) Delete an element ###

- Directive to delete an element or resource.

### VALIDATE (A:`VAL`) Validate a condition ###

- Directive to validate a condition or requirement.

### ITERATE (A:`ITER`) Perform iteration ###

- Directive to perform iteration or looping operations.

### CONDITION (A:`COND`) Evaluate conditions ###

- Directive to evaluate conditions and branch logic.

### MERGE (A:`MERGE`) Combine resources ###

- Directive to merge or combine multiple resources.

### SPLIT (A:`SPLIT`) Divide resources ###

- Directive to split or divide resources into parts.

### FILTER (A:`FILTER`) Select elements ###

- Directive to filter or select specific elements.

### SORT (A:`SORT`) Order elements ###

- Directive to sort or order elements.

### GROUP (A:`GROUP`) Categorize elements ###

- Directive to group or categorize elements.

### AGGREGATE (A:`AGG`) Summarize data ###

- Directive to aggregate or summarize data.

### OPTIMIZE (A:`OPT`) Improve performance ###

- Directive to optimize performance or efficiency.

### SCHEDULE (A:`SCHED`) Schedule operations ###

- Directive to schedule or time operations.

### MONITOR (A:`MON`) Monitor processes ###

- Directive to monitor or track processes.

### LOG (A:`LOG`) Record events ###

- Directive to log or record events and activities.

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

### Array (A:`arr`) ###

- Variable for array or list data structures.

### Object (A:`obj`) ###

- Variable for object or structure data.

### Function (A:`func`) ###

- Variable for function definitions and parameters.

### Condition (A:`cond`) ###

- Variable for conditional logic and branching.

### Loop (A:`loop`) ###

- Variable for iteration and repetition control.

### State (A:`state`) ###

- Variable for state management and tracking.

### Context (A:`ctx`) ###

- Variable for contextual information and metadata.

### Template (A:`tpl`) ###

- Variable for template definitions and placeholders.

### Schema (A:`schema`) ###

- Variable for data structure definitions and validation rules.

## PROPERTIES (A:`prop`) ##

- PROPERTIES UTILIZE `< >` brackets.

RULES:
    - Properties must be enclosed in `<` and `>` brackets
    - Properties are used to assign values to variables
    - Properties can contain nested variables and options
    - Properties must be properly nested within their context

### Key (A:`key`) ###

- Property for key-value assignments.

### Value (A:`val`) ###

- Property for value assignments.

### Name (A:`name`) ###

- Property for naming assignments.

### Type (A:`type`) ###

- Property for type assignments.

### Status (A:`status`) ###

- Property for status assignments.

### Result (A:`result`) ###

- Property for result assignments.

## COMPLETION (A:`comp`) ##

- COMPLETION UTILIZE `str[oper, var, opt, dirv, cmd, nl]` format.

RULES:
    - Completion must include all required elements: oper, var, opt, dirv, cmd, nl
    - Completion is used to specify what needs to be completed
    - Completion can reference dependencies and requirements
    - Completion must be properly nested within directives

### String (A:`str`) ###

- Completion element for string operations.

### Operator (A:`oper`) ###

- Completion element for operator definitions.

### Variable (A:`var`) ###

- Completion element for variable definitions.

### Option (A:`opt`) ###

- Completion element for option definitions.

### Directive (A:`dirv`) ###

- Completion element for directive definitions.

### Command (A:`cmd`) ###

- Completion element for command definitions.

### Natural Language (A:`nl`) ###

- Completion element for natural language taskstrings.

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

### ITERATE (A:`iter`) ###

- Command to iterate over collections or perform loops.

### CONDITION (A:`cond`) ###

- Command to evaluate conditions and branch logic.

### MERGE (A:`merge`) ###

- Command to merge or combine multiple resources.

### SPLIT (A:`split`) ###

- Command to split or divide resources into parts.

### FILTER (A:`filter`) ###

- Command to filter or select specific elements.

### SORT (A:`sort`) ###

- Command to sort or order elements.

### GROUP (A:`group`) ###

- Command to group or categorize elements.

### AGGREGATE (A:`agg`) ###

- Command to aggregate or summarize data.

### TRANSFORM (A:`trans`) ###

- Command to transform data from one format to another.

### VALIDATE (A:`val`) ###

- Command to validate data against schemas or rules.

### OPTIMIZE (A:`opt`) ###

- Command to optimize performance or efficiency.

## OPTIONS (A:`opt`) ##

RARE USES CASES WHEN VARIABLES REQUIRE OPTIONS.

- OPTIONS UTILIZE `( )` brackets.

RULES:
    - Options must be enclosed in `(` and `)` brackets
    - Options are used to provide additional parameters
    - Options are optional and can be omitted
    - Multiple options can be separated by commas

## VALIDATION RULES ##

### Syntax Validation ###

- All brackets must be properly paired and nested
- Directives must be in ALL CAPITAL LETTERS
- Commands must follow the `<< >>` bracket pattern
- Variables must follow the `{ }` bracket pattern
- Options must follow the `( )` bracket pattern
- Properties must follow the `< >` bracket pattern

### Semantic Validation ###

- Variable names must be descriptive and meaningful
- Commands must have valid parameters
- Directives must have valid targets
- Options must be relevant to their context
- Properties must have valid assignments

### Context Validation ###

- Variables must be defined before use
- Commands must have valid targets
- Directives must have valid scope
- Options must be compatible with their variables
- Properties must be properly nested within their context

### Error Handling ###

- Invalid syntax must be flagged immediately
- Missing variables must be reported
- Conflicting directives must be resolved
- Ambiguous references must be clarified
- Unbalanced brackets must be corrected

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
| Property | `< >` | Value assignment | `<key:value>` |
| Option | `( )` | Parameters | `(option1, option2)` |

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

## WORKFLOW PATTERNS ##

### Real-World Data Processing Pipeline ###

```crow
<!-- <ASGN:{project:customer_analytics}><environment:production>>
  <<SET:{data_source:customer_database}><format:sql_export>>
  <<TASK:[nl]"Process customer data for marketing insights">>
  <<ITERATE:{table:customer_records}><batch_size:1000>>
    <<FILTER:{criteria:active_customers}><date_range:last_12_months>>
    <<TRANSFORM:{schema:marketing_schema}><format:json_output>>
    <<VALIDATE:{rules:data_quality}><threshold:95_percent>>
    <<MERGE:{existing:analytics_db}><conflict_resolution:update>>
    <<LOG:{event:batch_complete}><timestamp:processing_time>>
  <<AGGREGATE:{metrics:customer_insights}><output:marketing_report>>
  <<ENFR:data_privacy{gdpr_compliance}> -->
```

### Complex Business Logic Workflow ###

```crow
<!-- <CONDITION:{test:order_validation}><result:validation_status>>
  <<IF:{condition:valid_customer}><action:process_order>>
    <<SET:{order_status:processing}><timestamp:current_time>>
    <<ITERATE:{items:order_items}><iterator:current_item>>
      <<CHECK:{inventory:item_availability}><result:stock_status>>
      <<IF:{condition:in_stock}><action:reserve_item>>
      <<ELSE:{condition:out_of_stock}><action:backorder_item>>
    <<CALCULATE:{pricing:total_cost}><tax:applicable_rates>>
    <<PROCESS:{payment:customer_payment}><gateway:stripe_api>>
  <<ELSE:{condition:invalid_customer}><action:reject_order>>
    <<LOG:{event:order_rejected}><reason:customer_validation_failed>>
  <<END:{condition:order_complete}><result:order_status>>
  <<NOTIFY:{customer:order_confirmation}><method:email_sms>>
  <<OUTPUT:{result:order_processed}><status:success>> -->
```

### Multi-System Integration Workflow ###

```crow
<!-- <ASGN:{integration:erp_crm}><environment:staging>>
  <<SET:{source_system:erp_database}><target_system:crm_platform>>
  <<TASK:[nl]"Sync customer data between ERP and CRM systems">>
  <<ITERATE:{table:erp_customers}><batch_size:500>>
    <<EXTRACT:{data:customer_records}><format:api_response>>
    <<TRANSFORM:{mapping:erp_to_crm}><schema:crm_format>>
    <<VALIDATE:{rules:data_integrity}><duplicate_check:enabled>>
    <<MERGE:{target:crm_database}><conflict_resolution:timestamp_based>>
    <<LOG:{event:sync_progress}><records_processed:current_count>>
  <<MONITOR:{process:sync_status}><alerts:error_threshold>>
  <<REPORT:{metrics:sync_statistics}><output:dashboard_update>>
  <<ENFR:data_consistency{referential_integrity}> -->
```

### Parallel Processing Workflow ###

```crow
<!-- <PARALLEL:{threads:multiple}><{data:shared_data}>>
  <<SPLIT:{data:shared_data}><{result:split_data}>>
  <<PROCESS:{thread:thread_1}><{result:result_1}>>
  <<PROCESS:{thread:thread_2}><{result:result_2}>>
  <<MERGE:{results:combined}><{result:final_result}>>
  <<OUTPUT:{result:parallel_output}><{result:completed_parallel}> -->
```

### Error Handling Workflow ###

```crow
<!-- <TRY:{operation:risky}><{result:attempt_result}>>
  <<CATCH:{error:exception}><{action:handle_error}>>
  <<RETRY:{operation:retry}><{result:retry_result}>>
  <<FALLBACK:{operation:alternative}><{result:fallback_result}>>
  <<OUTPUT:{result:error_handled}><{result:completed_error_handling}> -->
```

### Monitoring and Logging Workflow ###

```crow
<!-- <MONITOR:{process:target_process}><{status:process_status}>>
  <<LOG:{event:process_start}><{timestamp:start_time}>>
  <<TRACK:{progress:process_progress}><{status:current_status}>>
  <<ALERT:{condition:threshold}><{action:send_alert}>>
  <<LOG:{event:process_complete}><{timestamp:end_time}>>
  <<OUTPUT:{result:monitoring_complete}><{result:completed_monitoring}> -->
```

## CROSS-REFERENCES ##

### Element Relationships ###

| Element Type | Related Elements | Usage Context |
|--------------|------------------|---------------|
| Directives | Commands, Variables, Options | Principal operations |
| Commands | Variables, Options | Action execution |
| Variables | Options, Properties | Data storage |
| Options | Variables, Commands | Parameter specification |
| Properties | Variables, Commands | Value assignment |

### Navigation Aids ###

- **[[OPERATORS]]** - Complete operator reference
- **[[DIRECTIVES]]** - All directive definitions
- **[[COMMANDS]]** - Command execution patterns
- **[[VARIABLES]]** - Variable type definitions
- **[[OPTIONS]]** - Option specification rules
- **[[VALIDATION]]** - Validation and error handling
- **[[WORKFLOWS]]** - Common workflow patterns
- **[[EXAMPLES]]** - Detailed usage examples

### Quick Lookup ###

- **Syntax Issues**: See [[VALIDATION RULES]]
- **Workflow Help**: See [[WORKFLOW PATTERNS]]
- **Operator Reference**: See [[OPERATORS]]
- **Command Help**: See [[COMMANDS]]
- **Variable Types**: See [[VARIABLES]]
- **Error Handling**: See [[VALIDATION RULES]]

## ADVANCED FEATURES ##

### Complex Multi-Dimensional Operations ###

```crow
<!-- <ASGN:{project:corvus_docs}><{status:development}>>
  <<SET:{formatting_style:professional_document}><format:corvus>>
  <<TASK:[nl]"Create comprehensive documentation format">>
  <<DEV:req={type:adherence}><syntax:opinion={strict:dep=(design_format)}>>
    <completion:str[oper, var, opt, dirv, cmd, nl]:(dep:corvus_design)>>
  <<ENFR:corvus{.markdownlint.jsonc}> -->
```

### Advanced Workflow with Multiple Dependencies ###

```crow
<!-- <ITERATE:{collection:data_sources}><iterator:current_source>>
  <<FILTER:{criteria:valid_data}><result:filtered_items>>
  <<TRANSFORM:{format:target_schema}><result:transformed_data>>
  <<VALIDATE:{schema:expected_structure}><result:validated_output>>
  <<MERGE:{existing:database_records}><new:processed_data>>
  <<LOG:{event:processing_complete}><timestamp:completion_time>>
  <<OUTPUT:{destination:final_database}><result:updated_records>> -->
```

### Conditional Processing with Error Handling ###

```crow
<!-- <CONDITION:{test:data_quality}><result:quality_check>>
  <<IF:{condition:high_quality}><action:direct_processing>>
  <<ELSE:{condition:low_quality}><action:data_cleaning>>
    <<CLEAN:{data:raw_input}><result:cleaned_data>>
    <<VALIDATE:{schema:clean_requirements}><result:validated_clean>>
  <<END:{condition:processing_complete}><result:final_output>>
  <<CATCH:{error:processing_failure}><action:fallback_procedure>>
  <<OUTPUT:{result:conditional_complete}><status:success>> -->
```
