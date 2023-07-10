# AzureDevOpsBattlefield

This GitHub repository aims to provide a comprehensive resource for learning Azure DevOps, specifically focusing on features such as templates and runtime expressions. The objective of this project is to offer a practical and methodical approach to understanding the complexities of Azure DevOps.

It is important to note that this repository does not claim to provide exhaustive documentation of all Azure DevOps features. Rather, it serves as a space for experimentation, learning, and gaining a deeper understanding of the features offered by Azure DevOps.

### Macros

<details>
  <summary>
      Macros can be used in the majority of task inputs, such as the "script".
  </summary>
</details>
<details>
  <summary>
      Macros can also be used in variable value definitions.
  </summary>
</details>
<details>
  <summary>
      Macros can utilize UI-defined variables.
  </summary>
</details>
<details>
  <summary>
      In general, macros cannot be used at the properties level, except values in the `env` section.
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
