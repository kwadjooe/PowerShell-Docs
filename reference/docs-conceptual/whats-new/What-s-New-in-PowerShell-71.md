---
title: What's New in PowerShell 7.1
description: New features and changes released in PowerShell 7.1
ms.date: 11/10/2020
---

# What's New in PowerShell 7.1

TODO: Refresh

PowerShell 7.1 is an open-source, cross-platform (Windows, macOS, and Linux) edition of PowerShell,
built to manage heterogeneous environments and hybrid cloud.

In this release, we're introducing a number of new features, including:

## Where can I install PowerShell?

TODO: Refresh

PowerShell 7 currently supports the following operating systems on x64, including:

- Windows 8.1, and 10
- Windows Server 2012, 2012 R2, 2016, and 2019
- macOS 10.13+
- Red Hat Enterprise Linux (RHEL) / CentOS 7
- Fedora 30+
- Debian 9
- Ubuntu LTS 16.04+
- Alpine Linux 3.8+

Additionally, PowerShell 7.1 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine
Linux.

Check the installation instructions for your preferred operating system
[Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7),
[macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7),
or
[Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).

While not officially supported, the community has also provided packages for
[Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.

> [!NOTE]
> Debian 10 and CentOS 8 currently do not support WinRM remoting. For details on setting up
> SSH-based remoting, see
> [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).

For more up-to-date information about supported operating systems and support lifecycle, see the
[PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).

## Running PowerShell 7.1

TODO: Refresh + STORE

PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1. For
PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.

- PowerShell 7 is installed to `%programfiles%\PowerShell\7`
- The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`

The PowerShell 7 installer packages upgrade previous versions of PowerShell Core 6.x:

- PowerShell Core 6.x on Windows: `%programfiles%\PowerShell\6` is replaced by
  `%programfiles%\PowerShell\7`
- Linux: `/opt/microsoft/powershell/6` is replaced by `/opt/microsoft/powershell/7`
- macOS: `/usr/local/microsoft/powershell/6` is replaced by `/usr/local/microsoft/powershell/7`

> [!NOTE]
> In Windows PowerShell, the executable to launch PowerShell is named `powershell.exe`. In version 6
> and above, the executable is changed to support side-by-side execution. The new executable to
> launch PowerShell 7 is `pwsh.exe`. Preview builds will remain in-place as `pwsh-preview` instead
> of `pwsh` under the 7-preview directory.

## Improved shell experience with Predictive IntelliSense

TODO

## TODO - Add other Features

## Breaking Changes and Improvements

(TODO:IsComplete-ThruRC2)

### Breaking Changes

- **v7.1.0-preview.7**
- Fix $? to not be $false when native command writes to stderr (#13395)
- **v7.1.0-preview.6**
- Rename -FromUnixTime to -UnixTimeSeconds on Get-Date to allow Unix time input (#13084) (Thanks @aetos382!)
- Make $ErrorActionPreference not affect stderr output of native commands (#13361)
- Allow explicitly specified named parameter to supersede the same one from hashtable splatting (#13162)
- **v7.1.0-preview.4**
- Make the switch parameter -Qualifier not positional for Split-Path (#12960) (Thanks @yecril71pl!)
- Resolve the working directory as literal path for Start-Process when it's not specified (#11946) (Thanks @NoMoreFood!)
- Make -OutFile parameter in web cmdlets to work like -LiteralPath (#11701) (Thanks @iSazonov!)
- **v7.1.0-preview.3**
- Fix string parameter binding for BigInteger numeric literals (#11634) (Thanks @vexx32!)
- **v7.1.0-preview.2**
- On Windows, Start-Process creates a process environment with all the environment variables from
  current session, using -UseNewEnvironment creates a new default process environment (#10830)
  (Thanks @iSazonov!)
- Do not wrap return result to PSObject when converting ScriptBlock to delegate
  (#10619)
- **v7.1.0-preview.1**
- Use invariant culture string conversion for -replace operator (#10954) (Thanks @iSazonov!)

### Engine Updates and Fixes

- **v7.1.0-preview.rc.2**
- Rename Get-Subsystem to Get-PSSubsystem and fix two related minor issues (#13765)
- Add missing PSToken token table entries to fix the PSParser API (#13779)
- Add additional PowerShell modules to the tracked modules list (#12183)
- Fix blocking wait when starting file associated with a Windows application (#13750)
- Revert PSNativePSPathResolution to being an experimental feature (#13734)
- **v7.1.0-preview.rc.1**
- Make fixes to ComInterop code as suggested by .NET team (#13533)
- **v7.1.0-preview.7**
- Initial work of the subsystem plugin model (for minimal powershell) (#13186)
- Optimize GetSystemLockdownPolicy for non-lockdown scenarios (#13438)
- **v7.1.0-preview.6**
- Refactor command line parser to do early parsing (#11482) (Thanks @iSazonov!)
- Add support for some .NET intrinsic type converters (#12580) (Thanks @iSazonov!)
- Refresh and enable the ComInterop code in PowerShell (#13304)
- **v7.1.0-preview.5**
- Ensure assemblies listed in the module manifest FileList field are not loaded (#12968)
- **v7.1.0-preview.4**
- Ensure null-coalescing LHS is evaluated only once (#12667)
- Fix path handling bug in PSTask (#12554) (Thanks @IISResetMe!)
- Remove extra line before formatting group (#12163) (Thanks @iSazonov!)
- Make module formatting not generate error with strict mode (#11943)
- Adding more ETW logs to WSMan plugin (#12798) (Thanks @krishnayalavarthi!)
- Restrict loading of amsi.dll to system32 folder (#12730)
- **v7.1.0-preview.3**
- Set correct PSProvider full name at module load time (#11813) (Thanks @iSazonov!)
- **v7.1.0-preview.2**
- Allow case insensitive paths for determining PSModulePath (#12192)
- Add PowerShell version 7.0 to compatible version list (#12184)
- Discover assemblies loaded by Assembly.Load(byte[]) and Assembly.LoadFile (#12203)
- **v7.1.0-preview.1**
- Revert the PRs that made DBNull.Value and NullString.Value treated as $null (#11648)

### Experimental Features

- **v7.1.0-preview.6**
- Add -Runspace parameter to all *-PSBreakpoint cmdlets (#10492) (Thanks @KirkMunro!)
- **v7.1.0-preview.3**
- Support passing PSPath to native commands (#12386)
- **v7.1.0-preview.1**
- Use invariant culture string conversion for -replace operator (#10954) (Thanks @iSazonov!)

### General Cmdlet Updates and Fixes

- **v7.1.0-preview.rc.2**
- Emit warning if ConvertTo-Json exceeds -Depth value (#13692)
- **v7.1.0-preview.rc.1**
- Fix case where exception message contains just "`n" on Windows (#13684)
- Recognize CONOUT$ and CONIN$ as reserved device names (#13508) (Thanks @davidreis97!)
- Fix ConciseView for interactive advanced function when writing error (#13623)
- **v7.1.0-preview.7**
- Revert "Add the parameter -Paged to Get-Help to support paging (#13374)" (#13519)
- Add support for TLS 1.3 in Web cmdlets (#13409) (Thanks @iSazonov!)
- Add null check for args in CommandLineParser (#13451) (Thanks @iSazonov!)
- Process reparse points for Microsoft Store applications (#13481) (Thanks @iSazonov!)
- Move PSNullConditionalOperators feature out of experimental (#13529)
- Move PSNativePSPathResolution feature out of Experimental (#13522)
- Use field if property does not exist for ObRoot when using PowerShell Direct to container (#13375) (Thanks @hemisphera!)
- Suppress UTF-7 obsolete warnings (#13484)
- Avoid multiple enumerations of an IEnumerable<Expression> instance in Compiler.cs (#13491)
- Change Add-Type -OutputType to not support ConsoleApplication and WindowsApplication (#13440)
- Create warnings when UTF-7 is specified as an encoding (#13430)
- **v7.1.0-preview.6**
- Fix error message from new symbolic link missing target (#13085) (Thanks @yecril71pl!)
- Make the parameter args non-nullable in the public ConsoleHost APIs (#13429)
- Add missing dispose for CancellationTokenSource (#13420) (Thanks @Youssef1313!)
- Add the parameter -Paged to Get-Help to support paging (#13374)
- Fix Get-Help not properly displaying if parameter supports wildcards (#13353) (Thanks @ThomasNieto!)
- Update pwsh help for -InputFormat parameter (#13355) (Thanks @sethvs!)
- Declare MIT license for files copied from Roslyn (#13305) (Thanks @xtqqczze!)
- Improve BigInteger casting behaviors (#12629) (Thanks @vexx32!)
- Fix Get-Acl -LiteralPath "HKLM:Software\Classes\*" behavior (#13107) (Thanks @Shriram0908!)
- Add DefaultVisit method to the visitor interface and class (#13258)
- Fix conflicting shorthand switch -s (STA) for pwsh (#13262) (Thanks @iSazonov!)
- Change Read-Host -MaskInput to use existing SecureString path, but return as plain text (#13256)
- Remove ComEnumerator as COM objects using IEnumerator is now supported in .NET 5.0 (#13259)
- Use temporary personal path at Runspace startup when the 'HOME' environment variable is not defined (#13239)
- Fix Invoke-Command to detect recursive call of the same history entry (#13197)
- Change pwsh executable -inputformat switch prefix -in to -inp to fix conflict with -interactive (#13205) (Thanks @iSazonov!)
- Handle WSL filesystem path when analyze security zone of a file (#13120)
- Make other switches mandatory in Split-Path (#13150) (Thanks @kvprasoon!)
- New Fluent Design icon for PowerShell 7 (#13100) (Thanks @sarthakmalik!)
- Fix Move-Item to support cross-mount moves on Unix (#13044)
- **v7.1.0-preview.4**
- Fix NullReferenceException in CommandSearcher.GetNextCmdlet (#12659) (Thanks @powercode!)
- Prevent NullReferenceException in Unix computer cmdlets with test hooks active (#12651) (Thanks @vexx32!)
- Fix issue in Select-Object where Hashtable members (e.g. Keys) cannot be used with -Property or -ExpandProperty (#11097) (Thanks @vexx32!)
- Fix conflicting shorthand switch -w for pwsh (#12945)
- Rename the CimCmdlet resource file (#12955) (Thanks @iSazonov!)
- Remove use of Test-Path in ConciseView (#12778)
- Flag default switch statement condition clause as keyword (#10487) (Thanks @msftrncs!)
- Add parameter SchemaFile to Test-Json cmdlet (#11934) (Thanks @beatcracker!)
- Bring back Certificate provider parameters (#10622) (Thanks @iSazonov!)
- Fix New-Item to create symbolic link to relative path target (#12797) (Thanks @iSazonov!)
- Add CommandLine property to Process (#12288) (Thanks @iSazonov!)
- Adds -MaskInput parameter to Read-Host (#10908) (Thanks @davinci26!)
- Change CimCmdlets to use AliasAttribute (#12617) (Thanks @thlac!)
- **v7.1.0-preview.3**
- Fix incorrect index in format string in ParameterBinderBase (#12630) (Thanks @powercode!)
- Copy the CommandInfo property in Command.Clone() (#12301) (Thanks @TylerLeonhardt!)
- Apply -IncludeEqual in Compare-Object when -ExcludeDifferent is specified (#12317) (Thanks @davidseibel!)
- Change Get-FileHash to close file handles before writing output (#12474) (Thanks @HumanEquivalentUnit!)
- Fix inconsistent exception message in -replace operator (#12388) (Thanks @jackdcasey!)
- **v7.1.0-preview.2**
- Fix WinCompat module loading to treat PowerShell 7 modules with higher priority (#12269)
- Implement ForEach-Object -Parallel runspace reuse (#12122)
- Fix Get-Service to not modify collection while enumerating it (#11851) (Thanks @NextTurn!)
- Clean up the IPC named pipe on PowerShell exit (#12187)
- Fix <img /> detection regex in web cmdlets (#12099) (Thanks @vexx32!)
- Allow shorter signed hex literals with appropriate type suffixes (#11844) (Thanks @vexx32!)
- Update UseNewEnvironment parameter behavior of Start-Process cmdlet on Windows (#10830) (Thanks @iSazonov!)
- Add -Shuffle switch to Get-Random command (#11093) (Thanks @eugenesmlv!)
- Make GetWindowsPowerShellModulePath compatible with multiple PS installations (#12280)
- Fix Start-Job to work on systems that don't have Windows PowerShell registered as default shell (#12296)
- Specifying an alias and -Syntax to Get-Command returns the aliased commands syntax (#10784) (Thanks @ChrisLGardner!)
- Make CSV cmdlets work when using -AsNeeded and there is an incomplete row (#12281) (Thanks @iSazonov!)
- In local invocations, do not require -PowerShellVersion 5.1 for Get-FormatData in order to see all format data. (#11270) (Thanks @mklement0!)
- Added Support For Big Endian UTF-32 (#11947) (Thanks @NoMoreFood!)
- Fix possible race that leaks PowerShell object dispose in ForEach-Object -Parallel (#12227)
- Add -FromUnixTime to Get-Date to allow Unix time input (#12179) (Thanks @jackdcasey!)
- Change default progress foreground and background colors to provide improved contrast (#11455) (Thanks @rkeithhill!)
- Fix foreach -parallel when current drive is not available (#12197)
- Do not wrap return result to PSObject when converting ScriptBlock to delegate (#10619)
- Don't write DNS resolution errors on Test-Connection -Quiet (#12204) (Thanks @vexx32!)
- Use dedicated threads to read the redirected output and error streams from the child process for out-of-proc jobs (#11713)
- **v7.1.0-preview.1**
- Fix an operator preference order issue in binder code (#12075) (Thanks @DamirAinullin!)
- Fix NullReferenceException when binding common parameters of type ActionPreference (#12124)
- Fix default formatting for deserialized MatchInfo (#11728) (Thanks @iSazonov!)
- Use asynchronous streams in Invoke-RestMethod (#11095) (Thanks @iSazonov!)
- Address UTF-8 Detection In Get-Content -Tail (#11899) (Thanks @NoMoreFood!)
- Handle the IOException in Get-FileHash (#11944) (Thanks @iSazonov!)
- Change 'PowerShell Core' to 'PowerShell' in a resource string (#11928) (Thanks @alexandair!)
- Bring back MainWindowTitle in PSHostProcessInfo (#11885) (Thanks @iSazonov!)
- Miscellaneous minor updates to Windows Compatibility (#11980)
- Fix ConciseView to split PositionMessage using [Environment]::NewLine (#12010)
- Remove network hop restriction for interactive sessions (#11920)
- Fix NullReferenceException in SuspendStoppingPipeline() and RestoreStoppingPipeline() (#11870) (Thanks @iSazonov!)
- Generate GUID for FormatViewDefinition InstanceId if not provided (#11896)
- Fix ConciseView where error message is wider than window width and doesn't have whitespace (#11880)
- Allow cross-platform CAPI-compatible remote key exchange (#11185) (Thanks @silijon!)
- Fix error message (#11862) (Thanks @NextTurn!)
- Fix ConciseView to handle case where there isn't a console to obtain the width (#11784)
- Update CmsCommands to use Store vs certificate provider (#11643) (Thanks @mikeTWC1984!)
- Enable pwsh to work on Windows systems where mpr.dll and STA is not available (#11748)
- Refactor and implement Restart-Computer for Un*x and macOS (#11319)
- Add an implementation of Stop-Computer for Linux and macOS (#11151)
- Fix help function to check if less is available before using (#11737)
- Update PSPath in certificate_format_ps1.xml (#11603) (Thanks @xtqqczze!)
- Change regular expression to match relation-types without quotes in Link header (#11711) (Thanks @Marusyk!)
- Fix error message during symbolic link deletion (#11331)
- Add custom 'Selected.*' type to PSCustomObject in Select-Object only once (#11548) (Thanks @iSazonov!)
- Add -AsUTC to the Get-Date cmdlet (#11611)
- Fix grouping behavior with Boolean values in Format-Hex (#11587) (Thanks @vexx32!)
- Make Test-Connection always use the default synchronization context for sending ping requests (#11517)
- Correct startup error messages (#11473) (Thanks @iSazonov!)
- Ignore headers with null values in web cmdlets (#11424) (Thanks @iSazonov!)
- Re-add check for Invoke-Command job dispose. (#11388)
- Revert "Update formatter to not write newlines if content is empty (#11193)" (#11342) (Thanks @iSazonov!)
- Allow CompleteInput to return results from ArgumentCompleter when AST or Script has matching function definition (#10574) (Thanks @M1kep!)
- Update formatter to not write new lines if content is empty (#11193)

### Code Cleanup

- **v7.1.0-preview.rc.1**
- Simplify logical negation (#13555) (Thanks @xtqqczze!)
- Fixed the indentation of the help content for -nologo (#13557) (Thanks @soccypowa!)
- **v7.1.0-preview.7**
- Add single blank line after copyright header (#13486) (Thanks @xtqqczze!)
- Use read-only auto-implemented properties (#13507) (Thanks @xtqqczze!)
- Use boolean instead of bitwise operators on bool values (#13506) (Thanks @xtqqczze!)
- Fix erroneous assert (#13495) (Thanks @tamasvajk!)
- Cleanup: remove duplicate words in comments (#13539) (Thanks @xtqqczze!)
- Reformat StringUtil (#13509) (Thanks @xtqqczze!)
- Use uint instead of long for PDH constants (#13502) (Thanks @xtqqczze!)
- Cleanup: Remove redundant empty lines (#13404) (Thanks @xtqqczze!)
- Add StringUtil.Format overload to avoid unnecessary allocations (#13408) (Thanks @xtqqczze!)
- Fix test hooks for CommandLineParameterParser (#13459)
- Remove redundant delegate creation (#13441) (Thanks @xtqqczze!)
- **v7.1.0-preview.6**
- Use null check with pattern-matching instead of object.ReferenceEquals (#13065) (Thanks @xtqqczze!)
- Fix comparison of value type object to null (#13285) (Thanks @xtqqczze!)
- Use is operator instead of as operator (#13287) (Thanks @xtqqczze!)
- Change SwitchParameter fields to properties (#13291) (Thanks @xtqqczze!)
- Change "operable" to "executable" (#13281) (Thanks @yecril71pl!)
- Remove AssemblyInfo property from list views (#13331) (Thanks @ThomasNieto!)
- Use is not syntax where appropriate and remove unnecessary parentheses (#13323) (Thanks @xtqqczze!)
- Remove unreachable code in CustomShellCommands.cs (#13316) (Thanks @xtqqczze!)
- Add copyright header to .editorconfig and update files (#13306) (Thanks @xtqqczze!)
- Fix typo in Out-File.cs and Out-Printer.cs (#13298) (Thanks @dgoldman-msft!)
- Fix SA1026CodeMustNotContainSpaceAfterNewKeywordInImplicitlyTypedArrayAllocation (#13249) (Thanks @xtqqczze!)
- Remove usage of do statement to create an infinite loop (#13137) (Thanks @xtqqczze!)
- Use int instead of uint in places where it's more appropriate (#13141) (Thanks @xtqqczze!)
- Use int instead of long to avoid Interlocked.Read (#13069) (Thanks @xtqqczze!)
- **v7.1.0-preview.5**
- Code performance fixes (#12956) (Thanks @xtqqczze!)
- **v7.1.0-preview.4**
- Use nameof operator (#12716) (Thanks @xtqqczze!)
- Fix comments in Mshexpression.cs (#12711) (Thanks @sethvs!)
- Formatting: remove duplicate semicolons (#12666) (Thanks @xtqqczze!)
- Replace SortedList with Generic.SortedList<TKey,TValue> (#12954) (Thanks @xtqqczze!)
- Use HashSet instead of Hashtable with null values (#12958) (Thanks @xtqqczze!)
- Rename CopyItem.Tests.ps1 to Copy-Item.Tests.ps1 to match other tests (#10701) (Thanks @romero126!)
- Fix RCS1114: Remove redundant delegate creation (#12917) (Thanks @xtqqczze!)
- Code redundancy fixes (#12916) (Thanks @xtqqczze!)
- Update the PowerShell modules to use the new Help URI (#12686)
- Reorder modifiers according to preferred order (#12864) (Thanks @xtqqczze!)
- Expand numberOfPowershellRefAssemblies list capacity (#12840) (Thanks @xtqqczze!)
- Add readonly modifier to internal static members (#11777) (Thanks @xtqqczze!)
- cleanup: Use coalesce expression (#12829) (Thanks @xtqqczze!)
- Add missing assessibility modifiers (#12820) (Thanks @xtqqczze!)
- Use t_ naming convention for ThreadStatic members (#12826) (Thanks @xtqqczze!)
- Formatting: Add empty line between declarations (#12824) (Thanks @xtqqczze!)
- Clarify defaultRefAssemblies list capacity in AddType.cs (#12520) (Thanks @xtqqczze!)
- Fixing "Double "period" (..) in message for System.InvalidOperationException" (#12758) (Thanks @kvprasoon!)
- Rethrow to preserve stack details for better maintainability (#12723) (Thanks @xtqqczze!)
- Delete license.rtf (#12738) (Thanks @xtqqczze!)
- Nullable annotations for CommandSearcher (#12733) (Thanks @powercode!)
- Redundancy: Remove 'partial' modifier from type with a single part (#12725) (Thanks @xtqqczze!)
- Remove phrase 'All rights reserved' from Microsoft copyright statements (#12722) (Thanks @xtqqczze!)
- IDictionary -> IDictionary<string, FunctionInfo> for FunctionTable (#12658) (Thanks @powercode!)
- **v7.1.0-preview.3**
- Replace Unicode non-breaking space character with space (#12576) (Thanks @xtqqczze!)
- Remove unused New-DockerTestBuild.ps1 (#12610) (Thanks @RDIL!)
- Annotate Assert methods for better code analysis (#12618) (Thanks @powercode!)
- Use correct casing for cmdlet names and parameters in *.ps1 files throughout the codebase (#12584) (Thanks @xtqqczze!)
- Document why PackageVersion is used in PowerShell.Common.props (#12523) (Thanks @xtqqczze!)
- **v7.1.0-preview.2**
- Fix erroneous comment in tokenizer.cs (#12206) (Thanks @ShaydeNofziger!)
- Fix terms checker issues (#12189)
- Update copyright notice to latest guidance (#12190)
- CodeFactor cleanup (#12251) (Thanks @RDIL!)
- **v7.1.0-preview.1**
- Use span-based overloads (#11884) (Thanks @iSazonov!)
- Use new string.Split() overloads (#11867) (Thanks @iSazonov!)
- Remove unreachable DSC code (#12076) (Thanks @DamirAinullin!)
- Remove old dead code from FullCLR (#11886) (Thanks @iSazonov!)
- Use Dictionary.TryAdd() where possible (#11767) (Thanks @iSazonov!)
- Use Environment.NewLine instead of hard-coded linefeed in ParseError.ToString (#11746)
- Fix FileSystem provider error message (#11741) (Thanks @iSazonov!)
- Reformat code according to EditorConfig rules (#11681) (Thanks @xtqqczze!)
- Replace use of throw GetExceptionForHR with ThrowExceptionForHR (#11640) (Thanks @xtqqczze!)
- Refactor delegate types to lambda expressions (#11690) (Thanks @xtqqczze!)
- Remove Unicode BOM from text files (#11546) (Thanks @xtqqczze!)
- Fix Typo in Get-ComputerInfo cmdlet description (#11321) (Thanks @doctordns!)
- Fix typo in description for Get-ExperimentalFeature PSWindowsPowerShellCompatibility (#11282) (Thanks @alvarodelvalle!)
- Cleanups in command discovery (#10815) (Thanks @iSazonov!)
- Review currentculture (#11044) (Thanks @iSazonov!)

### Tools

- **v7.1.0-preview.7**
- vscode: Add editorconfig to recommended extensions (#13537) (Thanks @xtqqczze!)
- Remove the out-dated ZapDisable related code from build.psm1 (#13350) (Thanks @jackerr3!)
- **v7.1.0-preview.6**
- Fix dotnet install errors (#13387)
- Increase the timeout of Windows daily build to 90 minutes (#13354)
- Update the dependabot configuration to version 2 (#13230) (Thanks @RDIL!)
- Fix Test-XUnitTestResults function (#13270) (Thanks @iSazonov!)
- Update .devcontainer to use nightly docker SDK images (#13128)
- **v7.1.0-preview.5**
- Add missing .editorconfig settings present in dotnet/runtime (#12871) (Thanks @xtqqczze!)
- **v7.1.0-preview.4**
- Use correct isError parameter with Write-Log (#12989)
- Disable NonPrivateReadonlyFieldsMustBeginWithUpperCaseLetter rule in StyleCop (#12855) (Thanks @xtqqczze!)
- Add @TylerLeonhardt to PowerShell team list to correct changelog generation (#12927)
- Enable the upload of ETW traces to CLR CAP in Windows daily build (#12890)
- Prevent GitHub workflow for daily dotnet build updates from running in forks (#12763) (Thanks @bergmeister!)
- Add GitHub action for PR creation and Wix file generation logic (#12748)
- **v7.1.0-preview.3**
- Update @PoshChan config to include SSH (#12526) (Thanks @vexx32!)
- Update log message in Start-PSBootstrap (#12573) (Thanks @xtqqczze!)
- Add the .NET SDK installation path to the current process path in tools/UpdateDotnetRuntime.ps1 (#12525)
- **v7.1.0-preview.2**
- Update .NET dependency update script to include test csproj files (#12372)
- Scripts to update to .NET prerelease version (#12284)
- **v7.1.0-preview.1**
- Change recommended VS Code extension name from ms-vscode.csharp to ms-dotnettools.csharp (#12083) (Thanks @devlead!)
- Specify csharp_preferred_modifier_order in EditorConfig (#11775) (Thanks @xtqqczze!)
- Update .editorconfig (#11675) (Thanks @xtqqczze!)
- Enable EditorConfig support in OmniSharp (#11627) (Thanks @xtqqczze!)
- Specify charset in .editorconfig as utf-8 (no BOM) (#11654) (Thanks @xtqqczze!)
- Configure the issue label bot (#11527)
- Avoid variable names that conflict with automatic variables (#11392) (Thanks @xtqqczze!)

### Tests

- **v7.1.0-preview.7**
- Disable WMF download link validation test (#13479)
- **v7.1.0-preview.6**
- Mark Test-Connection -TraceRoute tests as pending (#13310)
- **v7.1.0-preview.5**
- Add new test for Format-Custom to avoid data loss (#11393) (Thanks @iSazonov!)
- **v7.1.0-preview.4**
- Remove duplicate tests from Measure-Object.Tests.ps1 (#12683) (Thanks @sethvs!)
- Fix tests to not write errors to console (#13010)
- Make sure tabcompletion tests run (#12981)
- Remove dependency on DNS for Test-Connection tests on macOS (#12943)
- Restore markdownlint tests (#12549) (Thanks @xtqqczze!)
- Wrap tests in pester blocks (#12700) (Thanks @xtqqczze!)
- **v7.1.0-preview.3**
- Make CIM tab completion test case insensitive (#12636)
- Mark ping tests as Pending due to stability issues in macOS (#12504)
- **v7.1.0-preview.2**
- Pin major Pester version to 4 to prevent breaking changes caused by upcoming release of v5 (#12262) (Thanks @bergmeister!)
- **v7.1.0-preview.1**
- Add empty preview.md file to fix broken link (#12041)
- Add helper functions for SSH remoting tests (#11955)
- Add new tests for Get-ChildItem for FileSystemProvider (#11602) (Thanks @iSazonov!)
- Ensure that types referenced by PowerShellStandard are present (#10634)
- Check state and report reason if it's not "opened" (#11574)
- Fixes for running tests on Raspbian (#11661)
- Unify pester test syntax for the arguments of -BeOfType (#11558) (Thanks @xtqqczze!)
- Correct casing for automatic variables (#11568) (Thanks @iSazonov!)
- Avoid variable names that conflict with automatic variables part 2 (#11559) (Thanks @xtqqczze!)
- Update pester syntax to v4 (#11544) (Thanks @xtqqczze!)
- Allow error 504 (Gateway Timeout) in markdown-link tests (#11439) (Thanks @xtqqczze!)
- Re-balance CI tests (#11420) (Thanks @iSazonov!)
- Include URL in the markdown-links test error message (#11438) (Thanks @xtqqczze!)
- Use CIM cmdlets instead of WMI cmdlets in tests (#11423) (Thanks @xtqqczze!)

### Build and Package Improvements

- **v7.1.0-preview.rc.2**
- Change Linux package script call to publish to the production repository in release builds (#13714)
- Update PSReadLine version to 2.1.0-rc1 (#13777)
- Move PowerShell build to dotnet 5.0-RC.2 (#13780)
- Bump Microsoft.PowerShell.Native to 7.1.0-rc.2 (#13794)
- **v7.1.0-preview.rc.1**
- Bump NJsonSchema from 10.1.24 to 10.1.26 (#13586)
- Bump PowerShellGet from 2.2.4 to 2.2.5 (#13683)
- Bump Microsoft.ApplicationInsights from 2.14.0 to 2.15.0 (#13639)
- Update PowerShell to build against dotnet 5.0-RC.1 (#13643)
- Write the InstallLocation to fixed registry key (#13576) (Thanks @heaths!)
- **v7.1.0-preview.7**
- Add Microsoft.NET.Test.Sdk dependency (Internal 12589)
- Update .NET NuGet package version to 5.0.0-preview.8.20407.11 (Internal 12555)
- Update to .NET 5 preview 8 (#13530)
- Change stage dependency for docker release stage in release pipeline (#13512)
- Bump Microsoft.NET.Test.Sdk from 16.7.0 to 16.7.1 (#13492)
- Create the folder before copying the global tools (#13476)
- A few fixes to the release pipeline (#13473)
- Bump Markdig.Signed from 0.20.0 to 0.21.1 (#13463)
- Add a pre-check for git to build.psm1 (#13227) (Thanks @yecril71pl!)
- **v7.1.0-preview.6**
- Update README.md and metadata.json for next release (#13059)
- Create release pipeline as a yaml pipeline (#13394)
- Update infrastructure to consume private builds from .NET (#13427)
- Fix breaks in packages daily build due to macOS signing changes (#13421)
- Sign individual files for macOS PKG (#13392)
- Disable code sign validation on jobs that do not sign (#13389)
- Bump PSReadLine from 2.0.2 to 2.0.4 (#13240)
- Update build documentation for Visual Studio 2019 dependency (#13336) (Thanks @xtqqczze!)
- Bump Microsoft.CodeAnalysis.CSharp from 3.6.0 to 3.7.0 (#13360)
- Bump Microsoft.NET.Test.Sdk from 16.6.1 to 16.7.0 (#13364)
- Bump xunit.runner.visualstudio from 2.4.2 to 2.4.3 (#13343)
- Use Authenticode certificate for MSIX signing (#13330)
- Add default help content to the assets folder (#13257)
- Update .NET SDK version from 5.0.100-preview.7.20366.2 to 5.0.100-preview.7.20366.15 (#13200)
- Set C# language version to preview/9.0 (#13090) (Thanks @iSazonov!)
- Use pwsh for build and test of package in CI build (#13223)
- Remove rcedit dependency, move daily ico dependency to props file (#13123)
- Bump NJsonSchema from 10.1.23 to 10.1.24 (#13214)
- Update .NET SDK version from 5.0.100-preview.7.20364.3 to 5.0.100-preview.7.20366.2 (#13192)
- Add support for installing arm64 MSIX package. (#13043) (Thanks @77!)
- Fix Azure file copy issues in release build (#13182)
- Update .NET SDK version from 5.0.100-preview.7.20358.6 to 5.0.100-preview.7.20364.3 (#13155)
- Fix Azure file copy break in Azure DevOps (#13173)
- Bump Xunit.SkippableFact from 1.4.8 to 1.4.13 (#13143)
- Add new chibi svg version of the avatar (#13160) (Thanks @WorrenB!)
- Refactor MSI code to make it easier to add a WiX exe installer (#13139)
- Disable ReadyToRun for debug build (#13144) (Thanks @iSazonov!)
- Add new chibi version of the avatar (#13140)
- Update .NET SDK version from 5.0.100-preview.7.20356.2 to 5.0.100-preview.7.20358.6 (#13134) (Thanks @github-actions[bot]!)
- Update .NET SDK version from 5.0.100-preview.6.20318.15 to 5.0.100-preview.7.20356.2 (#13125) (Thanks @github-actions[bot]!)
- **v7.1.0-preview.5**
- Change log for v7.1.0-preview.5 (Internal 11880)
- Fix Path for the Preview MSI (#13070)
- Correct stable and preview upgrade codes for MSI (#13036)
- Changelog for `v7.1.0-preview.4` (Internal 11841)
- Fix NuGet package compliance issues (#13045)
- Bump xunit.runner.visualstudio from 2.4.1 to 2.4.2 (#12874)
- Bump NJsonSchema from `10.1.21` to `10.1.23` (#13032) (#13022)
- **v7.1.0-preview.4**
- Update Distribution_Request.md
- Bump NJsonSchema from 10.1.15 to 10.1.16 (#12685)
- Disable uploading Symbols package (#12687)
- Update .NET SDK version from 5.0.100-preview.5.20279.10 to 5.0.100-preview.6.20318.15 (#13018)
- Remove component ref when re-generating the wix file (#13019)
- Make sure icons are added to MSI staging folder (#12983)
- Update DotnetRutimeMetadata.json to point to preview 6 (#12972)
- Bump PSReadLine from 2.0.1 to 2.0.2 (#12909)
- Bump NJsonSchema from 10.1.18 to 10.1.21 (#12944)
- Check if Azure Blob exists before overwriting (#12921)
- Enable skipped tests (#12894) (Thanks @iSazonov!)
- Fix break in package build by pinning ffi version to 1.12 (#12889)
- Upgrade APIScan version (#12876)
- Make contributors unique in Release notes (#12878) (Thanks @kvprasoon!)
- Update Linux daily CI to run in a single agent & collect traces (#12866)
- Update .NET SDK version from 5.0.100-preview.5.20278.13 to 5.0.100-preview.5.20279.10 (#12844) (Thanks @github-actions[bot]!)
- Sign the MSIX files for the store (#12582)
- Update the CI builds (#12830)
- Update .NET SDK version from 5.0.100-preview.5.20272.6 to 5.0.100-preview.5.20278.13 (#12772) (Thanks @github-actions[bot]!)
- Allow use of build module on unknown Linux distros (#11146) (Thanks @Saancreed!)
- Fix MSI upgrade and shortcut issues (#12792) (Thanks @heaths!)
- Bump NJsonSchema from 10.1.17 to 10.1.18 (#12812)
- Update .NET SDK version from 5.0.100-preview.5.20269.29 to 5.0.100-preview.5.20272.6 (#12759) (Thanks @github-actions[bot]!)
- Bump NJsonSchema from 10.1.16 to 10.1.17 (#12761)
- Update to dotnet SDK 5.0.0-preview.5.20268.9 (#12740)
- Remove assets\license.rtf (#12721) (Thanks @xtqqczze!)
- Bump Microsoft.CodeAnalysis.CSharp from 3.5.0 to 3.6.0 (#12731)
- **v7.1.0-preview.3**
- Update build to use the new .NET SDK 5.0.100-preview.4.20258.7 (#12637)
- Bump NJsonSchema from 10.1.14 to 10.1.15 (#12608)
- Bump NJsonSchema from 10.1.13 to 10.1.14 (#12598)
- Bump NJsonSchema from 10.1.12 to 10.1.13 (#12583)
- Update the build to sign any unsigned files as 3rd party Dlls (#12581)
- Update .NET SDK to 5.0.100-preview.4.20229.10 (#12538)
- Add ability to Install-Dotnet to specify directory (#12469)
- Allow / in relative paths for using module (#7424) (#12492) (Thanks @jcotton42!)
- Update dotnet metadata for next channel for automated updates (#12502)
- Bump .NET to 5.0.0-preview.4 (#12507)
- Bump Microsoft.ApplicationInsights from 2.13.1 to 2.14.0 (#12479)
- Bump PackageManagement from 1.4.6 to 1.4.7 in /src/Modules (#12506)
- Bump Xunit.SkippableFact from 1.3.12 to 1.4.8 (#12480)
- Fix quotes to allow variable expansion (#12512)
- Use new TargetFramework as net5.0 in packaging scripts (#12503) (Thanks @iSazonov!)
- Use new value for TargetFramework as net5.0 instead of netcoreapp5.0 (#12486) (Thanks @iSazonov!)
- Disable PublishReadyToRun for framework dependent packages (#12450)
- Add dependabot rules to ignore updates from .NET (#12466)
- Update README.md and metadata.json for upcoming release (#12441)
- Turn on ReadyToRun (#12361) (Thanks @iSazonov!)
- Add summary to compressed sections of change log (#12429)
- **v7.1.0-preview.2**
- Add the nuget.config from root to the temporary build folder (#12394)
- Bump System.IO.Packaging (#12365)
- Bump Markdig.Signed from 0.18.3 to 0.20.0 (#12379)
- Bump to .NET 5 Preview 3 pre-release (#12353)
- Bump PowerShellGet from 2.2.3 to 2.2.4 (#12342)
- Linux: Initial support for Gentoo installations. (#11429) (Thanks @rkitover!)
- Upgrade to .NET 5 Preview 2 (#12250) (Thanks @bergmeister!)
- Fix the Sync PSGalleryModules to Artifacts build (#12277)
- Bump PSReadLine from 2.0.0 to 2.0.1 (#12243)
- Bump NJsonSchema from 10.1.11 to 10.1.12 (#12230)
- Update change log generation script to support collapsible sections (#12214)
- **v7.1.0-preview.1**
- Put symbols in separate package (#12169)
- Disable x86 PDB generation (#12167)
- Bump NJsonSchema from 10.1.5 to 10.1.11 (#12050) (#12088) (#12166)
- Create crossgen symbols for Windows x64 and x86 (#12157)
- Move to .NET 5 preview.1 (#12140)
- Bump Microsoft.CodeAnalysis.CSharp from 3.4.0 to 3.5.0 (#12136)
- Move to standard internal pool for building (#12119)
- Fix package syncing to private Module Feed (#11841)
- Add Ubuntu SSH remoting tests CI (#12033)
- Bump Markdig.Signed from 0.18.1 to 0.18.3 (#12078)
- Fix MSIX packaging to determine if a Preview release by inspecting the semantic version string (#11991)
- Ignore last exit code in the build step as dotnet may return error when SDK is not installed (#11972)
- Fix daily package build (#11882)
- Fix package sorting for syncing to private Module Feed (#11838)
- Set StrictMode version 3.0 (#11563) (Thanks @xtqqczze!)
- Bump .devcontainer version to dotnet 3.1.101 (#11707) (Thanks @Jawz84!)
- Move to version 3 of AzFileCopy (#11697)
- Update README.md and metadata.json for next release (#11664)
- Code Cleanup for environment data gathering in build.psm1 (#11572) (Thanks @xtqqczze!)
- Update Debian Install Script To Support Debian 10 (#11540) (Thanks @RandomNoun7!)
- Update ADOPTERS.md (#11261) (Thanks @edyoung!)
- Change back to use powershell.exe in 'SetVersionVariables.yml' to unblock daily build (#11207)
- Change to use pwsh to have consistent JSON conversion for DateTime (#11126)

### Documentation and Help Content

- **v7.1.0-preview.rc.2**
-
- **v7.1.0-preview.rc.1**
- Update README and metadata.json for 7.1.0-preview.7 release (#13565)
- **v7.1.0-preview.7**
- Update README links and metadata.json for 7.1.0-preview.6 (#13437)
- **v7.1.0-preview.6**
- Fix/clarify instructions for running Start-PSPester tests (#13373)
- Improve inline documentation for VerbInfo (#13265) (Thanks @yecril71pl!)
- Improve the wording of inline comments in the help system (#13274) (Thanks @yecril71pl!)
- Correct grammar in README.md and other docs (#13269) (Thanks @tasnimzotder!)
- Add "GitHub Actions Python builds" to ADOPTERS.md (#13228) (Thanks @brcrista!)
- Update change logs for 6.2.x and 7.0.x (#13194)
- Update README.md and metadata.json for the v7.0.3 release (#13187)
- **v7.1.0-preview.5**
- Fix links for MSI packages to point to 7.1.0-preview.3 (#13056)
- Add update packages.microsoft.com step to distribution request template. (#13008)
- Update windows-core.md (#13053) (Thanks @xtqqczze!)
- Add @rjmholt to maintainers list (#13033)
- Update docs for v7.1.0-preview.4 release (#13028)
- **v7.1.0-preview.4**
- Update README and metadata files for next release (#12717)
- Update README.md removing experimental status of Arm builds, but Win-Arm64 is still preview for Stable release. (#12707)
- Add link to Github compare in changelog (#12713) (Thanks @xtqqczze!)
- Added missing changelog for v7.1.0-preview.2 (#12665)
- Update required Visual Studio version in build docs (#12628) (Thanks @xtqqczze!)
- minor update to Distribution_Request.md (#12705) (Thanks @kilasuit!)
- Update docs.microsoft.com links (#12653) (Thanks @xtqqczze!)
- Update change log for 6.2.5 release (#12670)
- Update README.md and metadata.json for next release (#12668)
- Merge 7.0.1 change log (#12669)
- Remove markdown unused definitions (#12656) (Thanks @xtqqczze!)
- Add HoloLens to list of PowerShell adopters (#12940) (Thanks @reynoldsbd!)
- Update README.md and metadata.json for next releases (#12939)
- Fix broken link in README.md (#12887) (Thanks @xtqqczze!)
- Minor typo corrections in Distribution Request Issue Templates (#12744) (Thanks @corbob!)
- Correct 'review-for-comments' in Governance.md (#11035) (Thanks @MarvTheRobot!)
- Fix markdown ordered lists (#12657) (Thanks @xtqqczze!)
- Fix broken docs.microsoft.com link (#12776) (Thanks @xtqqczze!)
- Replace link to Slack with link to PowerShell Virtual User Group (#12786) (Thanks @xtqqczze!)
- Update LICENSE.txt so that it's recognized as MIT (#12729)
- **v7.1.0-preview.3**
- Add link to life cycle doc to distribution request template (#12638)
- Update TFM reference in build docs (#12514) (Thanks @xtqqczze!)
- Fix broken link for blogs in documents (#12471)
- **v7.1.0-preview.2**
- Add documentation for WebResponseObject and BasicHtmlWebResponseObject properties (#11876) (Thanks @kevinoid!)
- Add Windows 10 IoT Core reference in Adopters.md (#12266) (Thanks @parameshbabu!)
- Update README.md and metadata.json for 7.1.0-preview.1 (#12211)
- **v7.1.0-preview.1**
- Replace VSCode link in CONTRIBUTING.md (#11475) (Thanks @stevend811!)
- Remove the version number of PowerShell from LICENSE (#12019)
- Add the 7.0 change log link to CHANGELOG/README.md (#12062) (Thanks @LabhanshAgrawal!)
- Improvements to the contribution guide (#12086) (Thanks @ShaydeNofziger!)
- Update the doc about debugging dotnet core in VSCode (#11969)
- Update README.md and metadata.json for the next release (#11918) (#11992)
- Update Adopters.md to include info on Azure Pipelines and GitHub Actions (#11888) (Thanks @alepauly!)
- Add information about how Amazon AWS uses PowerShell. (#11365) (Thanks @bpayette!)
- Add link to .NET CLI version in build documentation (#11725) (Thanks @joeltankam!)
- Added info about DeploymentScripts in ADOPTERS.md (#11703)
- Update CHANGELOG.md for 6.2.4 release (#11699)
- Update README.md and metadata.json for next release (#11597)
- Update the breaking change definition (#11516)
- Adding System Frontier to the PowerShell Core adopters list ADOPTERS.md (#11480) (Thanks @OneScripter!)
- Update ChangeLog, README.md and metadata.json for 7.0.0-rc.1 release (#11363)
- Add AzFunctions to ADOPTERS.md (#11311) (Thanks @Francisco-Gamino!)
- Add Universal Dashboard to ADOPTERS.md (#11283) (Thanks @adamdriscoll!)
- Add config.yml for ISSUE_TEMPLATE so that Doc, Security, Support, and Windows PowerShell issues go to URLs (#11153)
- Add Adopters.md file (#11256)
- Update Readme.md for preview.6 release (#11108)
- Update SUPPORT.md (#11101) (Thanks @mklement0!)
- Update README.md (#11100) (Thanks @mklement0!)