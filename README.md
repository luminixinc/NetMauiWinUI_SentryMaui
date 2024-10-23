

# NetMauiWinUI_SentryMaui

This Visual Studio 2022 solution contains 2 projects that are the standard .NET MAUI "hello world". It is a reduced test case to demonstrate an issue we are having integrating the [Sentry.Maui](https://www.nuget.org/packages/Sentry.Maui) package.

## How the Basic App was created
1. Opened Visual Studio 2022 Community Edition
2. Create a new project > .NET MAUI Multi-Project App > Next
3. Configured New Project screen: used defaults > Next
4. Additional Information screen: unchecked Android, iOS and macOS and left only Windows using WinUI 3 checked on  > Create
5. confirmed I could run and see default main page with waving dotnet bot
6. Commit #1

## Adding Sentry.Maui
1. Added Sentry.Maui (v 4.12.1) to both projects in the solution (https://www.nuget.org/packages/Sentry.Maui)
2. Configured SDK through MauiAppBuilder according to instructions on https://luminix-inc.sentry.io/projects/dotnet-maui/getting-started/
3. Added simple button on MainPage.xaml and implemented button click to call `SentrySdk.CaptureMessage`
4. Can no longer run the application
5. Commit #2

## Errors
The application encounters a `Microsoft.UI.Xaml.UnhandledExceptionEventArgs` in `App.InitializeComponent`.

Exception
> {"Could not load file or assembly 'WinRT.Runtime, Version=2.1.0.0, Culture=neutral, PublicKeyToken=99ea127f02d97709'. The system cannot find the file specified.":"WinRT.Runtime, Version=2.1.0.0, Culture=neutral, PublicKeyToken=99ea127f02d97709"}

Stack Trace
- at MauiApp1.MauiProgramExtensions.UseSharedMauiApp(MauiAppBuilder builder) in C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1\MauiProgramExtensions.cs:line 41
- at MauiApp1.WinUI.MauiProgram.CreateMauiApp() in C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\MauiProgram.cs:line 9
- at MauiApp1.WinUI.App.CreateMauiApp() in C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\App.xaml.cs:line 22
- at Microsoft.Maui.MauiWinUIApplication.OnLaunched(LaunchActivatedEventArgs args) in Microsoft.Maui\MauiWinUIApplication.cs:line 66
- at Microsoft.UI.Xaml.Application.Microsoft.UI.Xaml.IApplicationOverrides.OnLaunched(LaunchActivatedEventArgs args) in Microsoft.UI.Xaml\Application.cs:line 356
- at ABI.Microsoft.UI.Xaml.IApplicationOverrides.Do_Abi_OnLaunched_0(IntPtr thisPtr, IntPtr args) in ABI.Microsoft.UI.Xaml\IApplicationOverrides.cs:line 26



### Visual Studio Output Window

> 'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\MauiApp1.WinUI.exe'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\ntdll.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\kernel32.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\KernelBase.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\user32.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\win32u.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\gdi32.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\gdi32full.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\msvcp_win.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\ucrtbase.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\shell32.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\advapi32.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\msvcrt.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\sechost.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\bcrypt.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\rpcrt4.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\imm32.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\hostfxr.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\hostpolicy.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\coreclr.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\ole32.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\combase.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\oleaut32.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\bcryptprimitives.dll'. 
The thread 134688 has exited with code 0 (0x0).
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Private.CoreLib.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\clrjit.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: DefaultDomain): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Private.CoreLib.dll'. Symbols loaded.
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\MauiApp1.WinUI.dll'. 
'MauiApp1.WinUI.exe' (Win32): Unloaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\MauiApp1.WinUI.dll'
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\MauiApp1.WinUI.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\kernel.appcore.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\MauiApp1.WinUI.dll'. Symbols loaded.
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Runtime.dll'. 
The thread 126620 has exited with code 0 (0x0).
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Runtime.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\uxtheme.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\icu.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Windows.ApplicationModel.WindowsAppRuntime.Projection.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Windows.ApplicationModel.WindowsAppRuntime.Projection.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Runtime.InteropServices.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Runtime.InteropServices.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\WinRT.Runtime.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\WinRT.Runtime.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Collections.Concurrent.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Collections.Concurrent.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Collections.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Collections.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Threading.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Threading.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Runtime.CompilerServices.Unsafe.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Runtime.CompilerServices.Unsafe.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\clbcatq.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\Windows.StateRepositoryCore.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Program Files\WindowsApps\Microsoft.WindowsAppRuntime.1.5_5001.275.500.0_x64__8wekyb3d8bbwe\Microsoft.WindowsAppRuntime.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\shlwapi.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\WinTypes.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\xmllite.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\powrprof.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\rometadata.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\userenv.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\umpdc.dll'. 
onecore\base\appmodel\runtime\src\lookup.cpp(218)\kernelbase.dll!00007FFD23C74BB5: (caller: 00007FFD23CCE9CA) ReturnHr(1) tid(2481c) 8007007A The data area passed to a system call is too small.
onecore\base\appmodel\runtime\src\lookup.cpp(218)\kernelbase.dll!00007FFD23C74BB5: (caller: 00007FFD23CCE9CA) ReturnHr(2) tid(2481c) 8007007A The data area passed to a system call is too small.
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Private.Uri.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Private.Uri.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.ObjectModel.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.ObjectModel.dll'. Symbols loaded.
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.ComponentModel.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.ComponentModel.dll'. Symbols loaded.
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Numerics.Vectors.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Numerics.Vectors.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.WinUI.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.WinUI.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Program Files\WindowsApps\Microsoft.WindowsAppRuntime.1.5_5001.275.500.0_x64__8wekyb3d8bbwe\Microsoft.ui.xaml.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Program Files\WindowsApps\Microsoft.WindowsAppRuntime.1.5_5001.275.500.0_x64__8wekyb3d8bbwe\Microsoft.Internal.FrameworkUdk.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Program Files\WindowsApps\Microsoft.WindowsAppRuntime.1.5_5001.275.500.0_x64__8wekyb3d8bbwe\Microsoft.UI.Windowing.Core.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\urlmon.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\SHCore.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Program Files\WindowsApps\Microsoft.WindowsAppRuntime.1.5_5001.275.500.0_x64__8wekyb3d8bbwe\CoreMessagingXP.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\d3d11.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\version.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\DWrite.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\d2d1.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\iertutil.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\srvcli.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\netutils.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\ntmarta.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\profapi.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\BCP47Langs.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\CoreMessaging.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\dcomp.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\dxgi.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\Microsoft.Internal.FrameworkUdk.System.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Windows.SDK.NET.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Windows.SDK.NET.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Security.Cryptography.Algorithms.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Security.Cryptography.Algorithms.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Security.Cryptography.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Security.Cryptography.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Linq.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Linq.dll'. Symbols loaded.
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Memory.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Memory.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\twinapi.appcore.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\Windows.UI.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\DXCore.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\ResourcePolicyClient.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\Windows.ApplicationModel.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\Windows.UI.Immersive.dll'. 
'MauiApp1.WinUI.exe' (Win32): Unloaded 'C:\Windows\System32\ResourcePolicyClient.dll'
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\directxdatabasehelper.dll'. 
onecore\windows\directx\database\helperlibrary\lib\directxdatabasehelper.cpp(527)\directxdatabasehelper.dll!00007FFD124A823F: (caller: 00007FFD124A41ED) ReturnHr(1) tid(24c74) 80070057 The parameter is incorrect.
onecore\windows\directx\database\helperlibrary\lib\directxdatabasehelper.cpp(527)\directxdatabasehelper.dll!00007FFD124A823F: (caller: 00007FFD124A41ED) ReturnHr(2) tid(24c74) 80070057 The parameter is incorrect.
onecore\windows\directx\database\helperlibrary\lib\directxdatabasehelper.cpp(527)\directxdatabasehelper.dll!00007FFD124A823F: (caller: 00007FFD124A4515) ReturnHr(3) tid(24c74) 80070057 The parameter is incorrect.
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\DriverStore\FileRepository\nvdm.inf_amd64_3f15a44cbe11db49\nvdlistx.dll'. 
'MauiApp1.WinUI.exe' (Win32): Unloaded 'C:\Windows\System32\DriverStore\FileRepository\nvdm.inf_amd64_3f15a44cbe11db49\nvdlistx.dll'
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\DriverStore\FileRepository\nvdm.inf_amd64_3f15a44cbe11db49\nvdlistx.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\DriverStore\FileRepository\iigd_dch.inf_amd64_0cfb7a84e9f43778\igd10iumd64.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\apphelp.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.InteractiveExperiences.Projection.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\DriverStore\FileRepository\iigd_dch.inf_amd64_0cfb7a84e9f43778\igd10um64xe.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\winmm.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\DriverStore\FileRepository\iigd_dch.inf_amd64_0cfb7a84e9f43778\IntelControlLib.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\cfgmgr32.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.InteractiveExperiences.Projection.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\DriverStore\FileRepository\iigd_dch.inf_amd64_0cfb7a84e9f43778\igdgmm64.dll'. 
'MauiApp1.WinUI.exe' (Win32): Unloaded 'C:\Windows\System32\DriverStore\FileRepository\nvdm.inf_amd64_3f15a44cbe11db49\nvdlistx.dll'
The thread 151664 has exited with code 0 (0x0).
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\DriverStore\FileRepository\iigd_dch.inf_amd64_0cfb7a84e9f43778\igc64.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\DriverStore\FileRepository\iigd_dch.inf_amd64_0cfb7a84e9f43778\igc1464.dll'. 
'MauiApp1.WinUI.exe' (Win32): Unloaded 'C:\Windows\System32\DriverStore\FileRepository\iigd_dch.inf_amd64_0cfb7a84e9f43778\igc1464.dll'
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\DriverStore\FileRepository\iigd_dch.inf_amd64_0cfb7a84e9f43778\igc1464.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\windows.storage.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\TextShaping.dll'. 
The thread '0xdd100001' (150644) has exited with code 0 (0x0).
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Linq.Expressions.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Linq.Expressions.dll'. Symbols loaded.
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Reflection.Emit.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Reflection.Emit.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'Snippets'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Program Files\WindowsApps\Microsoft.WindowsAppRuntime.1.5_5001.275.500.0_x64__8wekyb3d8bbwe\Microsoft.Windows.ApplicationModel.Resources.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Program Files\WindowsApps\Microsoft.WindowsAppRuntime.1.5_5001.275.500.0_x64__8wekyb3d8bbwe\MRM.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\BCP47mrm.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Windows\System32\Windows.Globalization.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.Essentials.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.Essentials.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.Controls.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.Controls.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\Program Files\WindowsApps\Microsoft.WindowsAppRuntime.1.5_5001.275.500.0_x64__8wekyb3d8bbwe\Microsoft.UI.Xaml.Controls.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.Controls.Compatibility.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.Controls.Compatibility.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.Graphics.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.Graphics.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Extensions.DependencyInjection.Abstractions.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Extensions.DependencyInjection.Abstractions.dll'. Symbols loaded.
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\MauiApp1.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\MauiApp1.dll'. Symbols loaded.
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Extensions.Configuration.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Extensions.Configuration.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Extensions.Configuration.Abstractions.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Extensions.Configuration.Abstractions.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Extensions.Primitives.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Extensions.Primitives.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.Controls.Xaml.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Maui.Controls.Xaml.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Sentry.Maui.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Sentry.Maui.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Sentry.Extensions.Logging.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Sentry.Extensions.Logging.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Sentry.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Sentry.dll'. Symbols loaded.
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Net.Primitives.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Net.Primitives.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.IO.Compression.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.IO.Compression.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Extensions.Logging.Abstractions.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\Microsoft.Extensions.Logging.Abstractions.dll'. 
'MauiApp1.WinUI.exe' (Win32): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Text.Json.dll'. 
'MauiApp1.WinUI.exe' (CoreCLR: clrhost): Loaded 'C:\luminix\thirdparty\NetMauiWinUI_SentryMaui\MauiApp1.WinUI\bin\x64\Debug\net8.0-windows10.0.19041.0\win10-x64\AppX\System.Text.Json.dll'. 
Exception thrown at 0x00007FFD23CAFA4C in MauiApp1.WinUI.exe: Microsoft C++ exception: EEFileLoadException at memory location 0x000000C9A65E8770.
Exception thrown at 0x00007FFD23CAFA4C in MauiApp1.WinUI.exe: Microsoft C++ exception: [rethrow] at memory location 0x0000000000000000.
Exception thrown at 0x00007FFD23CAFA4C in MauiApp1.WinUI.exe: Microsoft C++ exception: EEFileLoadException at memory location 0x000000C9A65E8770.
Exception thrown at 0x00007FFD23CAFA4C in MauiApp1.WinUI.exe: Microsoft C++ exception: [rethrow] at memory location 0x0000000000000000.
Exception thrown at 0x00007FFD23CAFA4C in MauiApp1.WinUI.exe: Microsoft C++ exception: EEFileLoadException at memory location 0x000000C9A65E8770.
Exception thrown at 0x00007FFD23CAFA4C in MauiApp1.WinUI.exe: Microsoft C++ exception: [rethrow] at memory location 0x0000000000000000.
Exception thrown: 'System.IO.FileNotFoundException' in Sentry.Maui.dll
Exception thrown at 0x00007FFD23CAFA4C in MauiApp1.WinUI.exe: Microsoft C++ exception: [rethrow] at memory location 0x0000000000000000.
Exception thrown at 0x00007FFD23CAFA4C in MauiApp1.WinUI.exe: Microsoft C++ exception: [rethrow] at memory location 0x0000000000000000.
Exception thrown: 'System.TypeInitializationException' in MauiApp1.WinUI.dll
Exception thrown at 0x00007FFD23CAFA4C (KernelBase.dll) in MauiApp1.WinUI.exe: WinRT originate error - 0x80131534 : 'The type initializer for '<Module>' threw an exception.'.
Microsoft.ui.xaml.dll!00007FFC59D7FD86: 80131534 - 
