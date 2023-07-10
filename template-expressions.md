# Template expressions (aka compile-time expressions)

## Usable on the left side of a key

This allows you to define a task name using a variable. For [example](https://github.com/JakubLinhart/AzureDevOpsBattlefield/blob/9db84151d6a37aae91ebda190ad7ac7c662a51f7/pipelines/template-expressions.yml#L73):

```yaml
variables:
  - name: var_task_name
    value: 'pwsh'

steps:
  - ${{ variables.var_task_name }}: Write-Output 'Hello from a task defined by template expression.'
    displayName: The task name is defined by a template expression
```

Then the output is:

[![task name defined by a variable](images/template-expressions-variable-task-name-output.png)](https://dev.azure.com/linj/AzureDevOpsBattleground/_build/results?buildId=260&view=logs&j=0ab14b9f-e499-56d5-97b1-fd98b70ea339&t=bd5b3379-fc2b-58be-675b-6db955a3e723).

## UI-defined variables are unavailable in template expressions

TBD

## An undefined variable is evaluated as an empty string

TBD

## Can contain `if`

TBD

## The order of variable definitions is important

TBD

## Nested evaluation is NOT supported

TBD