# Repositories

## A repository resource branch can be defined by a macro

Consider this repository [resource definition](https://github.com/JakubLinhart/AzureDevOpsBattlefield/blob/7d7dfd142da3b49e5104745b0e58a24ef03bf958/pipelines/repository-macros.yml#L15-L19):

```yaml
resources:
  repositories:
    - repository: dynamic-repository
      type: github
      endpoint: JakubLinhart
      name: JakubLinhart/AzureDevOpsBattlefield
      ref: $(var_defined_at_ui_level)
```

Then if you define `var_defined_at_ui_level` at the UI level, the macro is evaluated at compile time. In such a case Azure DevOps supposes that the variable contains a branch name and prepends `refs/heads/` to the variable value, resolves such `ref` to a specific commit which leads to a repository with a detached head:

[![repository branch defined by a macro](images/macros-repository-branch-defined-by-macro.png)](https://linj.visualstudio.com/AzureDevOpsBattleground/_build/results?buildId=357&view=logs&j=011e1ec8-6569-5e69-4f06-baf193d1351e&t=0f4aa080-c997-58ca-481c-4930865ae0f8&l=13)

This also means that macros at this level are evaluated after template expressions since template expressions are evaluated even before UI-defined variables are defined (see [UI-defined variables are unavailable in template expressions](template-expressions.md#ui-defined-variables-are-unavailable-in-template-expressions)).

The same works also for variables defined at the [pipeline level](https://github.com/JakubLinhart/AzureDevOpsBattlefield/blob/7d7dfd142da3b49e5104745b0e58a24ef03bf958/pipelines/repository-macros.yml#L21-L25).

## A repository resource branch cannot be defined by a macro with job-level variable

You cannot use variables defined at the [job level](https://github.com/JakubLinhart/AzureDevOpsBattlefield/blob/7d7dfd142da3b49e5104745b0e58a24ef03bf958/pipelines/repository-macros-job-level-invalid.yml), because they don't exist yet and you get:

[![error when using job level variables](images/macros-repository-job-level-variable-error.png)](https://linj.visualstudio.com/AzureDevOpsBattleground/_build/results?buildId=358&view=results).

## A repository resource branch defined by macro gets `refs/heads/` prefix

Azure DevOps adds `refs/heads/` prefix to a `ref` defined by a macro. This means that you cannot specify a commit hash directly. For [example](https://github.com/JakubLinhart/AzureDevOpsBattlefield/blob/30f7fb7b23246c46d0f817042bf1191e0380655f/pipelines/repository-macros-prefix-invalid.yml):

```yaml
variables:
  - name: var_defined_at_pipeline_level
    value: refs/heads/dynamicBranch

resources:
  repositories:
    - repository: dynamic-repository-pipeline-level
      type: github
      endpoint: JakubLinhart
      name: JakubLinhart/AzureDevOpsBattlefield
      ref: $(var_defined_at_pipeline_level)
```

leads to:

[![default branch prefix](images/repository-macros-prefix-error.png)](https://linj.visualstudio.com/AzureDevOpsBattleground/_build/results?buildId=362&view=results)