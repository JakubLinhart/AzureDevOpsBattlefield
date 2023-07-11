# Template parameters

## Unknown parameters cannot be passed to strongly typed templates

Consider this strongly typed template `template-parameters-strong.yml` with a single defined parameter `parameter1`:

```yaml
parameters:
  - name: parameter1
    type: string
    default: 'parameter1 default value'
```

If you try to pass a parameter that is not defined in the template from a pipeline YAML:

```yaml
steps:
  - template: template-parameters-strong.yml
    parameters:
      parameter1: 'value of parameter1'
      parameter_not_defined_in_template: 'value of parameter not defined in template'
```

then you will get an error when you try to run the pipeline.

## All parameters without a default value must be specified for strongly typed templates

TBD

## Unknown parameters can be passed to weakly typed templates

TBD

## Unspecified parameters without a default value are evaluated as an empty string in weakly typed templates

TBD

## Template expressions cannot be used for parameter defaults

TBD

## A template expression can specify a template name

TBD
