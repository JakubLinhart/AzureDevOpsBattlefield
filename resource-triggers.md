# Resource Triggers

[Documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/pipeline-triggers?view=azure-devops):

> Pipeline completion triggers use the `resources.pipelines` syntax to define which pipeline's completion will trigger the current pipeline.

## Resource trigger fires/does not fire for PR validation builds

It is unclear from Azure DevOps documentation whether a resource trigger fires when the source pipeline is run as a PR validation build (`Build.Reason == 'PullRequest'`).

The [source pipeline](https://github.com/JakubLinhart/AzureDevOpsBattlefield/blob/main/pipelines/resource-trigger-source.yml) has two stages and is triggered by both pushes and PRs:

```yaml
stages:
- stage: BuildStage
  displayName: Build
  jobs:
  - job: build
    steps:
    - script: echo "Build stage running."

- stage: ResultStage
  displayName: Result
  dependsOn: BuildStage
  jobs:
  - job: result
    steps:
    - script: echo "Result stage running."
```

The [consumer pipeline](https://github.com/JakubLinhart/AzureDevOpsBattlefield/blob/main/pipelines/resource-trigger-consumer.yml) has a resource trigger on `ResultStage` without any branch filter:

```yaml
trigger: none
pr: none

resources:
  pipelines:
  - pipeline: source
    source: resource-trigger-source
    trigger:
      stages:
        - ResultStage
```
