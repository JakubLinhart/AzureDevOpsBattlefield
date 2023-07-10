# Azure DevOps Battlefield

This GitHub repository aims to provide a comprehensive resource for learning Azure DevOps, specifically focusing on features such as templates and runtime expressions. The objective of this project is to offer a practical and methodical approach to understanding the complexities of Azure DevOps.

It is important to note that this repository does not claim to provide exhaustive documentation of all Azure DevOps features. Rather, it serves as a space for experimentation, learning, and gaining a deeper understanding of the features offered by Azure DevOps.

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

TBD

## Template expressions (aka compile-time expressions)

- [Usable on the left side of a key.](template-expressions.md#usable-on-the-left-side-of-a-key)
- [UI-defined variables are unavailable in template expressions.](template-expressions.md#ui-defined-variables-are-unavailable-in-template-expressions)
- [An undefined variable is evaluated as an empty string.](template-expressions.md#an-undefined-variable-is-evaluated-as-an-empty-string)
- [Can contain `if`.](template-expressions.md#can-contain-if)
- [The order of variable definitions is important.](template-expressions.md#the-order-of-variable-definitions-is-important)
- [Nested evaluation is NOT supported.](template-expressions.md#nested-evaluation-is-not-supported)

## Template parameters

TBD
