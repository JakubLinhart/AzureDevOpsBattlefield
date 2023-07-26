# Azure DevOps Battlefield

This GitHub repository aims to provide a comprehensive resource for learning Azure DevOps, specifically focusing on features such as templates and runtime expressions. The objective of this project is to offer a practical and methodical approach to understanding the complexities of Azure DevOps.

It is important to note that this repository does not claim to provide exhaustive documentation of all Azure DevOps features, nor does it serve as a comprehensive Azure DevOps tutorial. Instead, it serves as a space for experimentation, learning, and gaining a deeper understanding of the features offered by Azure DevOps.

## Macros

[Documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/variables?view=azure-devops&tabs=yaml%2Cbatch#macro-syntax-variables):

> Macro syntax is designed to interpolate variable values into task inputs and into other variables.

- [Macros can be used in the majority of task inputs, such as the "script".](macros.md#macros-can-be-used-in-the-majority-of-task-inputs-such-as-the-script)
- [Macros can also be used in variable value definitions.](macros.md#macros-can-also-be-used-in-variable-value-definitions)
- [Macros can be used in the "env" section.](macros.md#macros-can-be-used-in-the-env-section)
- [In general, macros cannot be used at the task property level.](macros.md#in-general-macros-cannot-be-used-at-the-task-property-level)
- [Macros can utilize UI-defined variables.](macros.md#macros-can-utilize-ui-defined-variables)
- [Macros are evaluated lazily, variable definition order is not relevant.](macros.md#macros-are-evaluated-lazily-variable-definition-order-is-not-relevant)
- [Nested evaluation is NOT supported.](macros.md#nested-expansion-is-supported)
- [Variables referenced by macros can be defined using runtime expressions.](macros.md#variables-referenced-by-macros-can-be-defined-using-runtime-expressions)
- [An undefined variable preserve macro syntax.](macros.md#undefined-variables-preserve-macro-syntax)

## Runtime expressions

- [Can be used for variable value definition.](runtime-expressions.md#can-be-used-for-variable-value-definition)
- [Cannot be used for task properties.](runtime-expressions.md#cannot-be-used-for-task-properties)
- [Cannot be used for task inputs.](runtime-expressions.md#cannot-be-used-for-task-inputs)
- [Evaluated at the job level.](runtime-expressions.md#evaluated-at-the-job-level)
- [Can use variables that are not defined yet.](runtime-expressions.md#can-use-variables-that-are-not-defined-yet)
- [Can use variables defined at the UI level.](runtime-expressions.md#can-use-variables-defined-at-the-ui-level)
- [Cannot contain macros.](runtime-expressions.md#cannot-contain-macros)
- [Can contain template expressions.](runtime-expressions.md#can-contain-template-expressions)
- [Can use `dependencies` and `stageDependencies`.](runtime-expressions.md#can-use-dependencies-and-stagedependencies)
- [Undefined variables are expanded to an empty string.](runtime-expressions.md#undefined-variables-are-expanded-to-an-empty-string)

## Template expressions (aka compile-time expressions)

- [Usable on the left side of a key.](template-expressions.md#usable-on-the-left-side-of-a-key)
- [An undefined variable is evaluated as an empty string.](template-expressions.md#an-undefined-variable-is-evaluated-as-an-empty-string)
- [UI-defined variables are unavailable in template expressions.](template-expressions.md#ui-defined-variables-are-unavailable-in-template-expressions)
- TBD Macro can be used to access UI-defined variables in template expression.
- [The order of variable definitions is important.](template-expressions.md#the-order-of-variable-definitions-is-important)
- [Nested evaluation is NOT supported.](template-expressions.md#nested-evaluation-is-not-supported)
- [Templates expression can be used in runtime expressions.](template-expressions.md#templates-expression-can-be-used-in-runtime-expressions)

## Template parameters

- [Unknown parameters cannot be passed to strongly typed templates.](template-parameters.md#unknown-parameters-cannot-be-passed-to-strongly-typed-templates)
- [All parameters without a default value must be specified for strongly typed templates.](template-parameters.md#all-parameters-without-a-default-value-must-be-specified-for-strongly-typed-templates)
- [Unknown parameters can be passed to weakly typed templates.](template-parameters.md#unknown-parameters-can-be-passed-to-weakly-typed-templates)
- [Undefined parameters are evaluated as empty string in weakly typed templates.](template-parameters.md#undefined-parameters-are-evaluated-as-empty-string-in-weakly-typed-templates)
- [Template expressions cannot be used for parameter defaults.](template-parameters.md#template-expressions-cannot-be-used-for-parameter-defaults)
- [Runtime expressions cannot reference parameters.](template-parameters.md#runtime-expressions-cannot-reference-parameters)
- [A template expression can specify a template name.](template-parameters.md#a-template-expression-can-specify-a-template-name)

## Repositories

- [A repository resource branch can be defined by a macro.](repositories.md#a-repository-resource-branch-can-be-defined-by-a-macro)
- [A repository resource branch cannot be defined by a macro with job-level variable.](repositories.md#a-repository-resource-branch-cannot-be-defined-by-a-macro-with-job-level-variable)
- [A repository resource branch defined by macro gets `refs/heads/` prefix.](repositories.md#a-repository-resource-branch-defined-by-macro-gets-refsheads-prefix)