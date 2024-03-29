
# valstat dll

Windows native DLL specimen, implementing (very) few (very) simple valstat enabled functions.

## Building & Using

Use Visual Studio. After build event will xcopy the resulting 

`valstat_dll.dll` 

to 

`C:\Users\<your user name>\.valstat\valstat_dll.dll`

This is **important** as this is the location you need to specify when using this dll from various other projects when testing the valstat.

For example in [valstat/valstat_csharp](https://github.com/valstat/valstat_csharp) in a file [valstat_csharp/demo/valstat_dll.cs](https://github.com/valstat/valstat_csharp/blob/master/demo/valstat_dll.cs), we type:

```c#
namespace dbj
{
    internal class valstat_dll
    {
        const string valstat_dll_location = @"C:\Users\<your user name>\.valstat\valstat_dll.dll";
```



## The Purpose of VALSTAT

> [valstat](https://github.com/DBJDBJ/valstat) is language agnostic call/response protocol

One could say: for people who do not want to use exceptions. 

The purpose of this dll is to show valstat interop with various projects and languages who can run on Windows and load and use this DLL.

Thus it does not contains "snazzy, whiz-bang" code. It shows the valstat usability and malleability.

*(Roadmap: that is not stopping me to show the fastest possible Fibonacci generator, valstat enabled)*

## Operational Environment

- The "dll" suffix means this is Windows only project
  - This is not VS Code project, this is Visual Studio project, hence the *.sln and *.vcxproj files.
- The Visual Studio project use is very advisable, if one needs to debug the "native" dll (this one), mixed with "managed" project .eg. C# or VB.NET project.
  - As [per instructions](https://docs.microsoft.com/en-us/visualstudio/debugger/how-to-debug-managed-and-native-code?view=vs-2019), one will need the full path to the built dll in order to perform a so called "mixed mode" .NET debugging.
  - in case of "others" (e.g. GO) it is yet to be seen if "mixed mode" debugging is possible.
- Building
  - As per Windows lore no static CRT is linked in, that means 
      - `/MD` and `/MDd` compiler switches
      - [`DisableThreadLibraryCalls`](https://docs.microsoft.com/en-us/windows/win32/api/libloaderapi/nf-libloaderapi-disablethreadlibrarycalls) function 
      - Actual `DllMain` code is included
- This  dll is coded in C
  - that makes possible for the simplest, fastest and smallest windows dll 
  - valstat C implementation is perfectly simple, light and usable
- This is a separate repo 
  - One can use it as such and reference it from her projects
  - Or use as submodule in her repos using this dll

**&copy; 2021 (and onwards) by dbj@dbj.org  https://dbj.org/license_dbj**