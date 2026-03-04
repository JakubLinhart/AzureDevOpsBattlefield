# Resource Triggers

[Documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/pipeline-triggers?view=azure-devops):

> Pipeline completion triggers use the `resources.pipelines` syntax to define which pipeline's completion will trigger the current pipeline.

## Resource trigger with a stage filter fires for PR validation builds

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

When a [PR validation build](https://github.com/JakubLinhart/AzureDevOpsBattlefield/pull/1) of the source pipeline completes successfully, the consumer pipeline [is triggered](https://linj.visualstudio.com/AzureDevOpsBattleground/_build/results?buildId=592&view=results) with `Build.Reason: ResourceTrigger`. The consumer receives the PR's source branch via `resources.pipeline.source.sourceBranch`.

- [Source PR validation run (build 591)](https://linj.visualstudio.com/AzureDevOpsBattleground/_build/results?buildId=591&view=results)
- [Consumer triggered run (build 592)](https://linj.visualstudio.com/AzureDevOpsBattleground/_build/results?buildId=592&view=results)

## Resource trigger with a stage filter does not fire when the stage fails

The [official documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/pipeline-triggers?view=azure-devops) states that pipeline resource triggers fire "upon the **successful** completion of the triggering pipeline" and stage filters trigger "on **successful** completion of all the stages provided."

When the source pipeline's `ResultStage` completes with a failure (`exit 1`), the consumer pipeline is [not triggered](https://linj.visualstudio.com/AzureDevOpsBattleground/_build/results?buildId=642&view=results). There is no configuration to make the trigger fire on failure.

- [Source failed run (build 642)](https://linj.visualstudio.com/AzureDevOpsBattleground/_build/results?buildId=642&view=results) — both stages completed with failure, consumer was not triggered
