# .NET Quick-Ref

* run xunit tests with output to console: `dotnet test --logger "console;verbosity=detailed" --filter <filterexpr>`

  * `<filterexpr>` can be e.g. the test name, or with XUnit.Categories e.g. `Feature=83922`.
    But if we are interested in the output then it's best to run one test at a time, otherwise it's hard to find.

* run fsharp fsx script `dotnet fsi <filename>`

* open fsharp interpreter `dotnet fsi --readline`

## Fixes and work-arounds

* `Strings.PlatformNotSupported_DataSqlClient` error when running ef core database migrations on (some) linux platforms

  * Add `--runtime linux-x64` to the cli command

* `Microsoft.Data.SqlClient.SqlException` when connecting to database over HTTPS on older versions of dotnet core with newer versions of OpenSSL

  ```
  Microsoft.Data.SqlClient.SqlException (0x80131904): A connection was successfully established with the server, but then an error occurred during the pre-login handshake. (provider: TCP Provider, error: 35 - An internal exception was caught)
  ...
   ---> System.TypeInitializationException: The type initializer for 'SslInitializer' threw an exception.
   ---> Interop+Crypto+OpenSslCryptographicException: error:0E076071:configuration file routines:module_run:unknown module name
  ```

  * Set environment variable `OPENSSL_CONF=/dev/null` before/while running your command
    Source: https://stackoverflow.com/questions/73004195/phantomjs-wont-install-autoconfiguration-error


