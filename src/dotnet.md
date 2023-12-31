# .NET Quick-Ref

* run xunit tests with output to console: `dotnet test --logger "console;verbosity=detailed" --filter <filterexpr>`

  * `<filterexpr>` can be e.g. the test name, or with XUnit.Categories e.g. `Feature=83922`.
    But if we are interested in the output then it's best to run one test at a time, otherwise it's hard to find.

* work around `Strings.PlatformNotSupported_DataSqlClient` error when running ef core database migrations on (some) linux platforms

  * Add `--runtime linux-x64` to the cli command

* run fsharp fsx script `dotnet fsi <filename>`

* open fsharp interpreter `dotnet fsi --readline`

