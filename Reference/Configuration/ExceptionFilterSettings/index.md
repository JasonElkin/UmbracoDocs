---
versionFrom: 9.0.0
versionTo: 10.0.0
meta.Title: "Umbraco Exception Filter Settings"
meta.Description: "Information on the exception filter settings section"
---

# Exception filter settings

This section allows you to disable the `ModelBindingExceptionFilter`, this filter is only enable if the models builder mode is set to `InMemoryAuto`. This filter will return a redirect to the page being loaded after one second, if a `ModelsBindingException` or `InvalidCastException` occurs. The reason for this filter is that a page might be requested just as the content type has been changed, if this occurs the new model might not have been generated and loaded yet, this filter will take care of this.

By default this filter is enabled, but will be ignored if the mode is not `InMemoryAuto`. To manually disable the filter add the `"ExecptionFilter"` section to your config with the `"Disabled"` key set to `true` like so:

```json
"Umbraco": {
  "CMS": {
    "ExceptionFilter": {
      "Disabled": true
    }
  }
}
```

