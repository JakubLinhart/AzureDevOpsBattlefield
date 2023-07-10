# AzureDevOpsBattlefield

This GitHub repository aims to provide a comprehensive resource for learning Azure DevOps, specifically focusing on features such as templates and runtime expressions. The objective of this project is to offer a practical and methodical approach to understanding the complexities of Azure DevOps.

It is important to note that this repository does not claim to provide exhaustive documentation of all Azure DevOps features. Rather, it serves as a space for experimentation, learning, and gaining a deeper understanding of the features offered by Azure DevOps.

### Macros

[Documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/variables?view=azure-devops&tabs=yaml%2Cbatch#macro-syntax-variables):

> Macro syntax is designed to interpolate variable values into task inputs and into other variables.

<details>
  <summary>
    Macros can be used in the majority of task inputs, such as the "script".
  </summary>

  For `PowerShell@2` task it is possible to use for
  [targetType](https://github.com/JakubLinhart/AzureDevOpsBattlefield/blob/5aa439679c34ae8a7dec235517d2d2c750ce7481/pipelines/macros.yml#L124), [workingDirectory](https://github.com/JakubLinhart/AzureDevOpsBattlefield/blob/5aa439679c34ae8a7dec235517d2d2c750ce7481/pipelines/macros.yml#L125C15-L125C31),
  and [script](https://github.com/JakubLinhart/AzureDevOpsBattlefield/blob/5aa439679c34ae8a7dec235517d2d2c750ce7481/pipelines/macros.yml#L126) inputs (see [example output](https://linj.visualstudio.com/AzureDevOpsBattleground/_build/results?buildId=245&view=logs&j=0ab14b9f-e499-56d5-97b1-fd98b70ea339&t=3fa529ca-c925-5304-b42f-2bbd21f9750e)), 
  but in general, it should be possible for any input of any task.

  ```yaml
    - task: PowerShell@2
      displayName: 'A task with macros in inputs'
      inputs:
        targetType: $(var_targetType)
        workingDirectory: $(var_workingDirectory)
        script: $(var_script)
  ```

</details>

<details>
  <summary>
    Macros can also be used in variable value definitions.
  </summary>

  This is [possible](https://github.com/JakubLinhart/AzureDevOpsBattlefield/blob/5aa439679c34ae8a7dec235517d2d2c750ce7481/pipelines/macros.yml#L20):

  ```yaml
    - name: var_with_value_for_another_value
      value: 'this comes from a macro'
    - name: var_with_macro_in_value_at_pipeline_level
      value: '$(var_with_value_for_another_value)'
  ```

  [![Example output](images/macros-variable-value-definition.png)](https://linj.visualstudio.com/AzureDevOpsBattleground/_build/results?buildId=245&view=logs&j=0ab14b9f-e499-56d5-97b1-fd98b70ea339&t=f064c65f-5d7b-5dd9-a2c0-b27c2b3dbefa&l=12)

</details>

<details>
  <summary>
    Macros can be used in the "env" section.
  </summary>

  `env` section is at the properties level, but it is the same exception as `inputs`. 

  ```yaml
    - pwsh: |
      Write-Output "my_environment_variable: '$env:my_environment_variable'"
    displayName: 'A task with macro in env'
    env:
      my_environment_variable: $(var_my_environment_variable)
  ```

  [![Example output](images/macros-env.png)](https://linj.visualstudio.com/AzureDevOpsBattleground/_build/results?buildId=245&view=logs&j=0ab14b9f-e499-56d5-97b1-fd98b70ea339&t=67bb029a-943e-5196-8d89-e7392cea21c1&l=12)
</details>

<details>
  <summary>
    In general, macros cannot be used at the task properties level.
  </summary>

  
</details>

<details>
  <summary>
    Macros can utilize UI-defined variables.
  </summary>
</details>

<details>
  <summary>
    Variable definitions can contain macros with variables that are not defined yet. For example, you can use a job-level variable when defining a stage-level variable, as long as both variables exist during the final evaluation.
  </summary>
</details>

<details>
  <summary>
    Nested expansion is supported.
  </summary>
</details>

<details>
  <summary>
    Variables referenced by macros can be defined using runtime expressions.
  </summary>
</details>

<details>
  <summary>
    If a variable is not defined, the expansion of the macro will retain the original macro syntax.
  </summary>
</details>

### Runtime expressions

### Template expressions

### Template parameters
