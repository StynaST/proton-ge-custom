# FiveM client compatibility

Applied last in the Wine stage of `protonprep-valve-staging.sh`, on top of the
GE-Proton11-9 prepared tree. Source of truth: `fivem-linux` branch of the Wine
fork, commits after "Apply GE-Proton11-9 preparation patches".

| Patch | Fixes |
|---|---|
| 0001 widl | composable WinRT classes (DesktopWindowXamlSource) get registered |
| 0002 xmllite | XML starting with whitespace read as UTF-8 (FiveM updater markup) |
| 0003 windows.ui.xaml | XAML Islands subset used by the official updater UI |
| 0004 ntdll | NtQueryDebugFilterState, hookable DbgPrintEx filter |
| 0005 ntdll | `_fltused` data export with LdrpDebugFlags 16 bytes before it |
| 0006 ntdll | RtlLookupFunctionTable calls RtlpxLookupFunctionTable once (x86_64) |
| 0007 win32u | D3DKMT statistics and adapter perf data from NVML / sysfs |
| 0008 pdh | real CPU counters, GPU Engine / GPU Adapter Memory counters, raw counter arrays |
| 0009 win32u | desktop window creation no longer loads the display driver (explorer/desktop deadlock) |
| 0010 win32u | imported Vulkan memory keeps its NT handle, so DXVK can re-export it ("Failed to open shared NT handle") |

Regenerate: `git -C wine format-patch --no-signature -o ../patches/wine-hotfixes/fivem <prep-commit>..fivem-linux`
