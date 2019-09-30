# ShareGate Rule Sets
These `*.ruleset` files are the starting point for C# development projects in ShareGate.

## How to Configure
I the solution directory, create a `Directory.Build.props` file if it's not already present ([see here for more information](https://docs.microsoft.com/en-us/visualstudio/msbuild/customize-your-build?view=vs-2019)).

In the `Directory.Build.props` file, the following property groups should be configured:
```
<Project>
...
  <PropertyGroup>
    <CodeAnalysisIgnoreBuiltInRuleSets>true</CodeAnalysisIgnoreBuiltInRuleSets>
    <CodeAnalysisIgnoreBuiltInRules>false</CodeAnalysisIgnoreBuiltInRules>
    <CodeAnalysisRuleSet>$(MSBuildThisFileDirectory)sg.ruleset</CodeAnalysisRuleSet>
  </PropertyGroup>
  <PropertyGroup Condition="$(MSBuildProjectName.Contains('Tests'))">
    <CodeAnalysisRuleSet>$(MSBuildThisFileDirectory)sg.tests.ruleset</CodeAnalysisRuleSet>
  </PropertyGroup>
  <PropertyGroup>
...
</Project> 
```

_Note: Notice the condition setup for the `sg.tests.ruleset`. Make sure your test projects naming conventions work for this condition._

## License

Copyright © 2019, GSoft inc. This code is licensed under the Apache License, Version 2.0. You may obtain a copy of this license at https://github.com/gsoft-inc/gsoft-license/blob/master/LICENSE.
